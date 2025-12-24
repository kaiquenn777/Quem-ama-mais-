# Quem-ama-mais-
Para o amor da minha vida, minha princesa querida.
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Quem ama mais?</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Poppins:wght@400;600&display=swap');

        body {
            font-family: 'Poppins', sans-serif;
            background: #000814; /* Fundo bem escuro para o espaço */
            height: 100vh;
            width: 100vw;
            overflow: hidden;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0;
            padding: 0;
            position: relative;
        }

        /* Efeito de Galáxia/Nebulosa no fundo */
        .galaxy-bg {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle at 20% 30%, rgba(0, 31, 63, 0.8) 0%, transparent 40%),
                        radial-gradient(circle at 80% 70%, rgba(177, 156, 217, 0.3) 0%, transparent 40%),
                        radial-gradient(circle at 50% 50%, rgba(75, 0, 130, 0.2) 0%, transparent 60%);
            z-index: 0;
        }

        /* BURACO NEGRO NO CENTRO */
        .black-hole {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 250px;
            height: 250px;
            background: #000;
            border-radius: 50%;
            box-shadow: 0 0 40px #b19cd9, 
                        0 0 80px rgba(0, 31, 63, 0.8),
                        inset 0 0 20px rgba(177, 156, 217, 0.5);
            z-index: 1;
        }

        /* Disco de Acreção (O anel girando) */
        .black-hole::after {
            content: '';
            position: absolute;
            top: -15%;
            left: -15%;
            width: 130%;
            height: 130%;
            border: 4px solid #b19cd9;
            border-radius: 40% 60% 70% 30% / 50% 60% 30% 70%;
            box-shadow: 0 0 20px #b19cd9;
            animation: swirl 10s linear infinite;
            opacity: 0.6;
            filter: blur(2px);
        }

        @keyframes swirl {
            0% { transform: rotate(0deg) scale(1); }
            50% { transform: rotate(180deg) scale(1.1); }
            100% { transform: rotate(360deg) scale(1); }
        }

        /* Estrelas Cintilantes */
        .stars-container {
            position: absolute;
            width: 100%;
            height: 100%;
            z-index: 1;
        }

        .star {
            position: absolute;
            background: white;
            border-radius: 50%;
            opacity: 0.5;
            animation: twinkle var(--duration) infinite ease-in-out;
        }

        @keyframes twinkle {
            0%, 100% { opacity: 0.3; transform: scale(1); }
            50% { opacity: 1; transform: scale(1.2); }
        }

        .cursive {
            font-family: 'Dancing Script', cursive;
        }

        #iris-button {
            transition: all 0.15s ease-out;
            z-index: 999;
            touch-action: none;
            position: absolute;
        }

        .heart {
            position: fixed;
            font-size: 20px;
            color: #b19cd9;
            user-select: none;
            pointer-events: none;
            animation: float 4s linear infinite;
            z-index: 2;
        }

        @keyframes float {
            0% { transform: translateY(105vh) rotate(0deg); opacity: 1; }
            100% { transform: translateY(-10vh) rotate(360deg); opacity: 0; }
        }

        .card {
            background: rgba(255, 255, 255, 0.94);
            backdrop-filter: blur(12px);
            border-radius: 30px;
            box-shadow: 0 0 60px rgba(177, 156, 217, 0.4);
            padding: 3rem 2rem;
            text-align: center;
            max-width: 450px;
            width: 90%;
            z-index: 10;
            border: 2px solid rgba(177, 156, 217, 0.5);
            position: relative;
            min-height: 300px;
        }

        .btn-base {
            font-weight: 600;
            padding: 0.75rem 2rem;
            border-radius: 9999px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.2);
            cursor: pointer;
            min-width: 120px;
            display: inline-block;
            user-select: none;
        }
    </style>
</head>
<body>

    <div class="galaxy-bg"></div>
    <div class="black-hole"></div>
    <div id="stars" class="stars-container"></div>

    <div id="main-card" class="card">
        <div id="content">
            <h1 class="text-4xl text-[#001f3f] mb-8 cursive leading-tight">Quem entre nós dois ama mais?</h1>
            
            <div id="button-container" class="flex justify-center gap-6 items-center min-h-[120px] relative">
                <!-- Botão do Kaique -->
                <button id="kaique-button" class="btn-base bg-[#001f3f] hover:bg-[#003366] text-white transform transition active:scale-90">
                    KAIQUE
                </button>
                
                <!-- Botão da IRIS -->
                <button id="iris-button" class="btn-base bg-[#b19cd9] hover:bg-[#967bb6] text-white">
                    IRIS
                </button>
            </div>
        </div>
    </div>

    <script>
        // Criar estrelas dinamicamente
        const starsContainer = document.getElementById('stars');
        for (let i = 0; i < 150; i++) {
            const star = document.createElement('div');
            star.className = 'star';
            const size = Math.random() * 3 + 'px';
            star.style.width = size;
            star.style.height = size;
            star.style.top = Math.random() * 100 + '%';
            star.style.left = Math.random() * 100 + '%';
            star.style.setProperty('--duration', (Math.random() * 3 + 2) + 's');
            starsContainer.appendChild(star);
        }

        const irisBtn = document.getElementById('iris-button');
        const kaiqueBtn = document.getElementById('kaique-button');
        const content = document.getElementById('content');

        // Posições ajustadas laterais e para baixo para nunca cobrir o Kaique
        const posicoes = [
            { top: '0px', left: '150px' },   
            { top: '0px', left: '-150px' },  
            { top: '60px', left: '100px' },  
            { top: '60px', left: '-100px' }, 
            { top: '80px', left: '0px' },    
            { top: '40px', left: '140px' },  
            { top: '40px', left: '-140px' }  
        ];

        let indiceAtual = -1;

        function fugir(e) {
            if (e && e.type === 'touchstart') e.preventDefault();
            let novoIndice;
            do {
                novoIndice = Math.floor(Math.random() * posicoes.length);
            } while (novoIndice === indiceAtual);
            indiceAtual = novoIndice;
            const pos = posicoes[novoIndice];
            irisBtn.style.top = pos.top;
            irisBtn.style.left = pos.left;
        }

        irisBtn.addEventListener('mouseover', fugir);
        irisBtn.addEventListener('touchstart', fugir, {passive: false});
        irisBtn.addEventListener('click', (e) => {
            e.preventDefault();
            fugir();
        });

        kaiqueBtn.addEventListener('click', () => {
            irisBtn.style.display = 'none';
            content.innerHTML = `
                <div class="animate-bounce mb-4 text-5xl">🌌</div>
                <h1 class="text-4xl text-[#001f3f] mb-2 cursive">Eu já sabia!</h1>
                <p class="text-xl text-[#967bb6] mb-6 cursive">Isso tava muito facil.</p>
                <p class="text-lg text-gray-700">O <b>Kaique</b> ama muitão mesmo, até o infinito!!! PRINCESONA! 💜</p>
                <p class="text-[#b19cd9] mt-4 text-sm font-medium italic">Impossível competir!</p>
            `;
            
            for(let i = 0; i < 50; i++) {
                setTimeout(createHeart, i * 50);
            }
            setInterval(createHeart, 300);
        });

        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            const icons = ['💜', '💙', '✨', '🌌', '⭐'];
            heart.innerHTML = icons[Math.floor(Math.random() * icons.length)];
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.fontSize = (Math.random() * 20 + 15) + 'px';
            heart.style.animationDuration = (Math.random() * 2 + 3) + 's';
            document.body.appendChild(heart);
            setTimeout(() => heart.remove(), 4000);
        }

        setInterval(createHeart, 1000);
    </script>
</body>
</html>
