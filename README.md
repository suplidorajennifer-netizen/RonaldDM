<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Página de Prueba - Ronald Dávila</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <style>
        body {
            font-family: Arial, Helvetica, sans-serif;
            background: linear-gradient(135deg, #4facfe, #00f2fe);
            min-height: 100vh;
            margin: 0;
            overflow: hidden;
        }

        /* ===== LOADER ===== */
        #loader {
            position: fixed;
            inset: 0;
            background: linear-gradient(135deg, #4facfe, #00f2fe);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 9999;
            transition: opacity 1s ease, visibility 1s ease;
        }

        .spinner {
            width: 80px;
            height: 80px;
            border: 8px solid rgba(255,255,255,0.3);
            border-top: 8px solid #ffffff;
            border-radius: 50%;
            animation: girar 1s linear infinite;
        }

        @keyframes girar {
            to { transform: rotate(360deg); }
        }

        /* ===== CONTENIDO ===== */
        #contenido {
            opacity: 0;
            visibility: hidden;
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: opacity 1s ease;
        }

        #contenido.mostrar {
            opacity: 1;
            visibility: visible;
        }

        .contenedor {
            background-color: #ffffff;
            padding: 30px;
            border-radius: 12px;
            max-width: 650px;
            text-align: center;
            box-shadow: 0 15px 30px rgba(0,0,0,0.2);
            animation: aparecer 1.5s ease-out;
        }

        h1 {
            animation: brillo 3s infinite;
        }

        /* ===== JUEGO ===== */
        .juego {
            margin-top: 30px;
            padding: 20px;
            border-top: 2px dashed #ddd;
        }

        .juego button {
            padding: 15px 25px;
            font-size: 18px;
            border: none;
            border-radius: 8px;
            background: #4facfe;
            color: #fff;
            cursor: pointer;
            margin: 10px;
        }

        .juego button:disabled {
            background: #aaa;
            cursor: not-allowed;
        }

        .contador {
            font-size: 22px;
            margin: 10px 0;
        }

        footer {
            margin-top: 20px;
            font-size: 14px;
            color: #888;
        }

        /* ===== ANIMACIONES ===== */
        @keyframes aparecer {
            from { opacity: 0; transform: translateY(30px); }
            to { opacity: 1; transform: translateY(0); }
        }

        @keyframes brillo {
            0% { text-shadow: 0 0 5px rgba(79,172,254,0.5); }
            50% { text-shadow: 0 0 15px rgba(79,172,254,1); }
            100% { text-shadow: 0 0 5px rgba(79,172,254,0.5); }
        }
    </style>
</head>
<body>

    <!-- LOADER -->
    <div id="loader">
        <div class="spinner"></div>
    </div>

    <!-- CONTENIDO -->
    <div id="contenido">
        <div class="contenedor">
            <h1>Página de Prueba</h1>
            <p>Hola, mi nombre es <strong>Ronald Dávila</strong>.</p>
            <p>Esta página es una prueba para mi servidor web.</p>

            <!-- JUEGO -->
            <div class="juego">
                <h2>🎮 Juego de Clics</h2>
                <p>Tienes <strong>10 segundos</strong> para hacer clics</p>
                <div class="contador">Clics: <span id="clics">0</span></div>
                <div class="contador">Tiempo: <span id="tiempo">10</span>s</div>

                <button id="btnIniciar">Iniciar juego</button>
                <button id="btnClic" disabled>¡CLIC!</button>
            </div>

            <footer>
                © 2026 - Ronald Dávila
            </footer>
        </div>
    </div>

    <script>
        // Loader
        window.addEventListener("load", () => {
            setTimeout(() => {
                loader.style.opacity = "0";
                loader.style.visibility = "hidden";
                contenido.classList.add("mostrar");
                document.body.style.overflow = "auto";
            }, 1500);
        });

        // Juego
        let clics = 0;
        let tiempo = 10;
        let intervalo;

        const btnIniciar = document.getElementById("btnIniciar");
        const btnClic = document.getElementById("btnClic");
        const spanClics = document.getElementById("clics");
        const spanTiempo = document.getElementById("tiempo");

        btnIniciar.addEventListener("click", () => {
            clics = 0;
            tiempo = 10;
            spanClics.textContent = clics;
            spanTiempo.textContent = tiempo;
            btnClic.disabled = false;
            btnIniciar.disabled = true;

            intervalo = setInterval(() => {
                tiempo--;
                spanTiempo.textContent = tiempo;
                if (tiempo === 0) {
                    clearInterval(intervalo);
                    btnClic.disabled = true;
                    btnIniciar.disabled = false;
                    alert("⏱️ Tiempo terminado\nTotal de clics: " + clics);
                }
            }, 1000);
        });

        btnClic.addEventListener("click", () => {
            clics++;
            spanClics.textContent = clics;
        });
    </script>

</body>
</html>
