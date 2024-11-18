<!DOCTYPE html>
<html lang="en">
    <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Se feliz</title>
    <style>
      * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
        }
        body {
        background: rgb(0, 0, 0);
        color: #00f7ff;
        width: 100vw;
        height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
        overflow: hidden;
        position: relative;
        }

        
        .section1 p {
        text-align: center;
        font-size: 1.2rem;
        padding: 0 1rem; 
        }

        .span-1 {
        font-size: 3rem; 
        }

        .span-2 {
        font-size: 1.8rem;
        }

        .span-3 {
        font-size: 2.5rem;
        }

        .span-4 {
        font-size: 2rem;
        }

        button {
        width: 100px;
        height: 45px;
        border: none;
        border-radius: 15px;
        color: rgb(14, 14, 14);
        background: #ca22c2;
        margin-top: 20px;
        cursor: pointer;
        }

        button:hover {
        background: #090909c3;
        }

        .snowflake {
        position: absolute;
        top: -10px;
        background-image: url('./svg.svg');
        background-size: cover;
        opacity: 4;
        width: 10px;
        height: 10px;
        filter: drop-shadow(0 0 20px rgba(255, 255, 255, 0.8)) hue-rotate(180deg)
        brightness(1.5);
        animation: fall linear infinite;
        transform: scale(1);
        }

        @keyframes fall {
        0% {
        transform: translateY(0);
        }
        100% {
        transform: translateY(100vh);
        }
        }


        @media (max-width: 768px) {
        body {
        flex-direction: column;
        }

        .span-1 {
        font-size: 2.5rem;
        }

        .span-2 {
        font-size: 1.5rem;
        }

        .span-3 {
        font-size: 2rem;
        }

        .span-4 {
        font-size: 1.8rem;
        }

        button {
        width: 80px;
        height: 35px;
        }

        .snowflake {
        width: 8px;
        height: 8px;
        }
        }

    
    .letras span {
        font-size: 2.5rem;
        }

        .meme-final {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        height: 100vh;
        text-align: center;
        span {
        font-size: 2.5rem;
        }
        }

        .desactivado {
        display: none;
        }

        .oculto {
        visibility: hidden;
        }
    </style>
    <script type="module">
        const $ = (e) => document.getElementById(e);
        const section1 = $("s1");
        const btn = $("btn");
        const audio = $("myAudio");

        const section2 = $("s2");
        const pLetras = $("pLetras");

        const letrasConfig = [
        { palabras: ["Desde", "Noviembre"], tiempo: 0 },
        { palabras: ["se", "siente"], tiempo: 1900 },
        { palabras: ["que", "viene"], tiempo: 4000 },
        { palabras: ["Diciembre"], tiempo: 5000, esUltimo: true },
        ];

        function createSnowflakes() {
        const numFlakes = 100;
        for (let i = 0; i < numFlakes; i++) {
        const snowflake = document.createElement("div");
        snowflake.classList.add("snowflake");
          const size = Math.random() * 50 + 30;
        snowflake.style.width = `${size}px`;
        snowflake.style.height = `${size}px`;
          snowflake.style.left = `${Math.random() * 100}vw`;
          snowflake.style.animationDuration = `${Math.random() * 5 + 5}s`;
          snowflake.style.animationDelay = `${Math.random() * 2}s`;
        document.body.appendChild(snowflake);
        }
        }

        createSnowflakes();

        btn.addEventListener("click", () => {
        section1.classList.add("desactivado");
        section2.classList.remove("desactivado");

        audio.volume = 1.0;
        audio.play();
        mostrarLetras(letrasConfig);
        });

        function mostrarLetras(config) {
        config.forEach((letraObj) => {
        setTimeout(() => {
            pLetras.innerHTML = "";

            const span1 = document.createElement("span");
            span1.textContent = letraObj.palabras[0];
            pLetras.appendChild(span1);

            const saltoDeLinea = document.createElement("br");
            pLetras.appendChild(saltoDeLinea);

            if (letraObj.esUltimo) {
                setTimeout(() => {
                pLetras.innerHTML = "";
                const gif = document.createElement("img");
                const span = document.createElement("span");
                const span2 = document.createElement("span");
                const saltoDeLinea = document.createElement("br");

                span.innerHTML = "FELIZ CASI <br />🎶❄️ NAVIDAD 🎶❄️";
                gif.src = "./feliz.gif";
                pLetras.appendChild(span);
                pLetras.appendChild(saltoDeLinea);
                pLetras.appendChild(gif);
                pLetras.classList.add("meme-final");
                }, 2000);
                } else {
                const span2 = document.createElement("span");
                span2.textContent = letraObj.palabras[1];
                span2.classList.add("oculto");
                pLetras.appendChild(span2);

                setTimeout(() => {
                span2.classList.remove("oculto");
                }, 520);
            }
            }, letraObj.tiempo);
        });
        }
    </script>
    </head>
    <body>
    <div class="section1" id="s1">
        <p>
        <span class="span-1">🌟HOLA COMO TE VA🌟</span><br />
        <span class="span-2">QUIERO</span><br />
        <span class="span-3">CONTARTE</span><br />
        <span class="span-4">QUE</span><br />
        <button id="btn">❄️click❄️</button>
        </p>
    </div>
    <div class="section2 desactivado" id="s2">
        <audio
        id="myAudio"
        src="indi,rock.unknown"
        preload="auto"
        class="desactivado"
        ></audio>
        <p class="letras" id="pLetras">HOLA</p>
    </div>
    </body>
</html>

