<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cena Romântica</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
            background: linear-gradient(45deg, #8a2be2, #da70d6);
            overflow: hidden;
            font-family: 'Arial', sans-serif;
        }

        button {
            padding: 20px 40px;
            font-size: 24px;
            background: #ff69b4;
            color: white;
            border: none;
            border-radius: 30px;
            cursor: pointer;
            position: relative;
            overflow: hidden;
            transition: all 0.3s;
            animation: brilho 2s infinite;
            box-shadow: 0 0 20px rgba(255, 105, 180, 0.5);
        }

        button:hover {
            transform: scale(1.1);
            animation: brilho 0.5s infinite;
        }

        @keyframes brilho {
            0% { box-shadow: 0 0 15px #ff69b4; }
            50% { box-shadow: 0 0 30px #ff69b4, 0 0 40px #ff69b4; }
            100% { box-shadow: 0 0 15px #ff69b4; }
        }

        button::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent, rgba(255,255,255,0.3), transparent);
            transform: rotate(45deg);
            animation: reflexo 3s infinite;
        }

        @keyframes reflexo {
            0% { transform: rotate(45deg) translateX(-100%); }
            100% { transform: rotate(45deg) translateX(100%); }
        }

        #imagemRomantica {
            display: none;
            max-width: 300px;
            margin: 20px;
            border-radius: 15px;
            box-shadow: 0 0 30px rgba(255, 105, 180, 0.7);
        }

        .emoji {
            position: fixed;
            font-size: 24px;
            animation: cair 3s linear forwards;
            pointer-events: none;
        }

        #mensagem {
            display: none;
            font-size: 24px;
            color: #fff;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
            margin-top: 30px;
            text-align: center;
            position: absolute;
            bottom: 20px;
        }

        @keyframes cair {
            0% {
                transform: translateY(-100%) rotate(0deg);
                opacity: 1;
            }
            100% {
                transform: translateY(100vh) rotate(360deg);
                opacity: 0;
            }
        }
    </style>
</head>
<body>
    <div id="container">
        <button onclick="iniciarEfeito()">Selecionar</button>
        <img id="imagemRomantica" src="C:\Users\pesso\Downloads\WhatsApp Image 2025-03-27 at 13.14.46.jpeg" alt="Cena Romântica">
        <div id="mensagem">Cada momento contigo é como um conto de fadas real! 💜</div>
    </div>

    <script>
        function iniciarEfeito() {
            const btn = document.querySelector('button');
            btn.style.display = 'none';
            
            document.getElementById('imagemRomantica').style.display = 'block';
            document.getElementById('mensagem').style.display = 'block';

            const emojis = ['💖', '💘', '💝', '💞', '💕'];
            const intervalo = setInterval(() => {
                const emoji = document.createElement('div');
                emoji.classList.add('emoji');
                emoji.style.left = Math.random() * 100 + 'vw';
                emoji.textContent = emojis[Math.floor(Math.random() * emojis.length)];
                document.body.appendChild(emoji);

                setTimeout(() => emoji.remove(), 3000);
            }, 200);

            setTimeout(() => clearInterval(intervalo), 5000);
        }
    </script>
</body>
</html>
