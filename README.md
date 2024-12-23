<html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Letter of Appreciation</title>
    <style>
        body {
            font-family: 'Georgia', serif;
            background-color: #f8f1f1;
            margin: 0;
            padding: 20px;
            color: #333;
        }
        .container {
            max-width: 800px;
            margin: 50px auto;
            background-color: #fff8e7;
            border-radius: 12px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
            padding: 30px;
            line-height: 1.6;
        }
        h1 {
            color: #f4a261;
            text-align: center;
            margin-bottom: 20px;
        }
        p, .signature {
            margin: 15px 0;
            display: none;
        }
        .signature {
            margin-top: 30px;
            text-align: right;
            font-style: italic;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1 id="title"></h1>
        <p class="content"> Sorry for interrupting, but I just wanted to remind you that you are deeply appreciated. Please don't hurt yourself with the negative thoughts that may come into your mind. I want you to always remember that I accept you for who you are, so don’t feel insecure. If only you could see yourself through my eyes, you would realize just how beautiful you truly are.</p>
        <p class="content"> Please take care of your mental health as well. Don’t let negative thoughts overpower you. I will always be by your side whenever you feel alone or when it seems like the world is against you. Even if others aren't there, remember that I am. We will face any challenge the world throws at us, together. We will live and grow side by side.</p>
        <p class="content"> Before I end this letter, I want to remind you that I will always pursue you, no matter what happens. I know how much pain your past has caused you, and I will never let it repeat. I won’t allow anyone to hurt you again the way they did before.</p>
        <div class="signature">
            <p>Sincerely, <br>Kaizen</p> 
        </div>
    </div>

    <audio id="music" src="https://audio.jukehost.co.uk/dD1B66ITCxrUvHrI7rCObK2tB0EDgdTm"></audio>

    <script>
        document.body.addEventListener('dblclick', function() {
            const music = document.getElementById('music');
            if (music.paused) {
                music.play();
            } else {
                music.pause();
            }
        });

        // Typewriter Effect
        function typeWriter(element, text, delay, callback) {
            let i = 0;
            function typing() {
                if (i < text.length) {
                    element.innerHTML += text.charAt(i);
                    i++;
                    setTimeout(typing, delay);
                } else if (callback) {
                    callback();
                }
            }
            typing();
        }

        // Start typewriting effect
        window.onload = function() {
            const paragraphs = document.querySelectorAll('.content');
            const signature = document.querySelector('.signature');
            let current = 0;

            function typeNextParagraph() {
                if (current < paragraphs.length) {
                    paragraphs[current].style.display = "block";
                    typeWriter(paragraphs[current], paragraphs[current].textContent, 50, typeNextParagraph);
                    paragraphs[current].textContent = ""; // Clear existing text for typing
                    current++;
                } else if (signature) {
                    signature.style.display = "block";
                    typeWriter(signature, signature.textContent, 50);
                    signature.textContent = ""; // Clear existing text for typing
                }
            }

            typeWriter(document.getElementById('title'), "Hi my bae", 50, typeNextParagraph);
        };
    </script>
</body>
</html>
