<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sebuah Pertanyaan</title>
    
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.9.3/dist/confetti.browser.min.js"></script>
    
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #f0f0f0;
            font-family: Arial, sans-serif;
            overflow: hidden;
        }
        .container {
            text-align: center;
        }
        h1 {
            font-size: 2.5em;
            color: #333;
        }
        #pleadingEmoji {
            font-size: 3em;
            margin-top: 10px;
            animation: pulse 2s infinite ease-in-out;
        }
        /* PERUBAHAN CSS: Sederhanakan container tombol */
        .buttons {
            margin-top: 20px;
            display: flex; /* Gunakan flexbox untuk menata tombol */
            justify-content: center;
            align-items: center;
            gap: 20px; /* Jarak antar tombol */
        }
        button {
            padding: 15px 30px;
            font-size: 1.2em;
            cursor: pointer;
            border: none;
            border-radius: 8px;
            transition: all 0.3s ease;
            /* HAPUS: 'position: absolute' agar tombol saling mendorong */
        }
        #yesBtn {
            background-color: #4CAF50;
            color: white;
        }
        #noBtn {
            background-color: #f44336;
            color: white;
        }
        #thankYouMessage {
            display: none;
        }
        #thankYouMessage h1 {
            color: #2c3e50;
        }
        #cuteEmoticon {
            font-size: 5em;
            margin-top: 20px;
            animation: bounce 1s infinite;
        }
        
        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% { transform: translateY(0); }
            40% { transform: translateY(-30px); }
            60% { transform: translateY(-15px); }
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.1); }
            100% { transform: scale(1); }
        }
    </style>
</head>
<body>

    <div class="container" id="mainContent">
        <h1 id="questionText">Aku Kalau aku salah maafin ya!!!</h1>
        <div id="pleadingEmoji">🥺</div>
        <div class="buttons" id="buttonsContainer">
            <button id="yesBtn">Yes</button>
            <button id="noBtn">No</button>
        </div>
    </div>

    <div class="container" id="thankYouMessage">
        <h1>Terima Kasih! ❤️</h1>
        <div id="cuteEmoticon">😊</div>
    </div>

    <script>
        const yesBtn = document.getElementById('yesBtn');
        const noBtn = document.getElementById('noBtn');
        const mainContent = document.getElementById('mainContent');
        const thankYouMessage = document.getElementById('thankYouMessage');

        const noButtonPhrases = [
            "No", "Yakin?", "Coba lagi deh", "Ayolah...", "Please?", "Jangan gitu dong...", "Oops!"
        ];
        let phraseIndex = 0;

        let currentPaddingV = 15;
        let currentPaddingH = 30;
        let currentFontSize = 1.2;

        noBtn.addEventListener('click', function() {
            // Membesarkan tombol Yes
            currentPaddingV += 8;
            currentPaddingH += 15;
            currentFontSize += 0.3;
            yesBtn.style.padding = `${currentPaddingV}px ${currentPaddingH}px`;
            yesBtn.style.fontSize = `${currentFontSize}em`;
            
            // HAPUS: Semua logika untuk memindahkan tombol No
            
            // Mengubah teks tombol No
            phraseIndex++;
            noBtn.textContent = noButtonPhrases[phraseIndex % noButtonPhrases.length];
        });

        yesBtn.addEventListener('click', function() {
            mainContent.style.display = 'none';
            thankYouMessage.style.display = 'block';

            confetti({
                particleCount: 150,
                spread: 90,
                origin: { y: 0.6 }
            });
        });
    </script>

</body>
</html>
