<html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Reveal the Message</title>
    <style>
        body {
            margin: 0;
            font-family: 'Arial', sans-serif;
            text-align: center;
            color: #fff;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background: linear-gradient(135deg, #ff69b4, #ffc0cb); /* Gradient background */
            overflow: hidden;
            position: relative;
            animation: backgroundAnimation 5s ease-in-out infinite;
        }

        h1 {
            font-size: 3rem;
            font-weight: bold;
            margin: 20px;
            text-shadow: 0px 4px 10px rgba(0, 0, 0, 0.3);
            animation: fadeIn 1s ease-in-out;
        }

        .button {
            padding: 15px 40px;
            font-size: 1.2rem;
            font-weight: bold;
            color: #ffc0cb;
            background: #fff;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            box-shadow: 0 8px 15px rgba(0, 0, 0, 0.2);
            transition: all 0.3s ease-in-out;
            animation: pulse 1.5s infinite;
        }

        .button:hover {
            transform: scale(1.1);
            background: #ffe4e1;
            box-shadow: 0 15px 25px rgba(0, 0, 0, 0.3);
        }

        .message-container {
            background-color: rgba(255, 255, 255, 0.9); /* Soft white background with transparency */
            padding: 40px 30px;
            border-radius: 20px;
            box-shadow: 0 4px 30px rgba(0, 0, 0, 0.3);
            max-width: 600px;
            margin: auto;
            text-align: left;
            color: #333; /* Dark text for readability */
            font-size: 1.1rem;
            line-height: 1.8;
            position: relative;
            animation: fadeIn 2s ease-in-out;
        }

        .hidden {
            display: none;
        }

        .falling-flowers {
            position: absolute;
            top: 0;
            width: 100%;
            pointer-events: none;
            animation: fall 6s linear infinite;
        }

        .flower {
            position: absolute;
            width: 30px;
            height: 30px;
            background-color: #ff69b4;
            border-radius: 50%;
            opacity: 0;
            animation: flowerAnimation 6s infinite;
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(-20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes pulse {
            0%, 100% {
                transform: scale(1);
                box-shadow: 0 8px 15px rgba(0, 0, 0, 0.2);
            }
            50% {
                transform: scale(1.05);
                box-shadow: 0 12px 20px rgba(0, 0, 0, 0.3);
            }
        }

        @keyframes backgroundAnimation {
            0% {
                background: linear-gradient(135deg, #ff69b4, #ffc0cb);
            }
            50% {
                background: linear-gradient(135deg, #ffc0cb, #ff69b4);
            }
            100% {
                background: linear-gradient(135deg, #ff69b4, #ffc0cb);
            }
        }

        @keyframes flowerAnimation {
            0% {
                opacity: 1;
                transform: translateY(-50px) rotate(0deg);
            }
            100% {
                opacity: 0;
                transform: translateY(100vh) rotate(360deg);
            }
        }

    </style>
</head>
<body id="page">

    <!-- Falling Pink Flowers -->
    <div class="falling-flowers">
        <div class="flower" style="left: 20%; animation-delay: 0s;"></div>
        <div class="flower" style="left: 40%; animation-delay: 1s;"></div>
        <div class="flower" style="left: 60%; animation-delay: 2s;"></div>
        <div class="flower" style="left: 80%; animation-delay: 3s;"></div>
    </div>

    <!-- First Page -->
    <div id="first-page">
        <h1>Reveal the Message</h1>
        <button class="button" onclick="revealMessage()">Reveal the Message</button>
    </div>

    <!-- Second Page -->
    <div id="second-page" class="hidden">
        <div class="message-container">
            <h2>Hello Nami</h2>
            <p>Today is January 5, 2025, and this day is not just an ordinary one because it holds special meaning for us. Before I proceed to the main reason why I created this message, I want to thank you for always being there whenever I need you the most. Thank you for being my ally in everything, especially in this exhausting world.</p>

            <p>You've made my life better than it used to be, and I hope you can feel how much I appreciate your presence. I value you more than words can ever express. If only you could see things from my perspective, you would realize just how much you truly mean to me.</p>

            <p>I hope you learn to appreciate yourself more. Always be kind to yourself and don't let sadness overwhelm you. Remember that you can lean on me whenever you feel tired or when it seems like the world is against you. We'll support each other always, and forever. So, please, never think you're alone in this challenging world, okay? If you ever need me, I'm just one call away.</p>

            <p>Now, I want to be honest about why I wrote this letter. Nami, I want to take this relationship seriously, not just as puppy love or something fleeting. I want us to be together forever and succeed together in the future. I can't imagine my life without you in this exhausting world. I want to continue what we have now, and as I've said before, I'm willing to pursue you wholeheartedly.</p>

            <p>Before I end this letter, I just have one question for you:</p>

            <p><strong>Nami, may I court you?</strong></p>
        </div>
    </div>

    <!-- Background music -->
    <audio id="backgroundMusic" loop>
        <source src="https://audio.jukehost.co.uk/IEEeBmgcBSRv8iWqg8QaB2AsOzII4HUK" type="audio/mpeg">
        Your browser does not support the audio element.
    </audio>

    <script>
        function revealMessage() {
            // Play background music
            const music = document.getElementById('backgroundMusic');
            music.play();

            // Change the background color for the second page
            document.body.style.backgroundColor = '#ffc0cb';

            // Hide the first page and show the second page
            document.getElementById('first-page').classList.add('hidden');
            document.getElementById('second-page').classList.remove('hidden');
        }
    </script>

</body>
</html>
