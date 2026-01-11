<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Página Arcade - Ronald Dávila</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <style>
body {
    font-family: Arial, Helvetica, sans-serif;
    min-height: 100vh;
    margin: 0;
    overflow: hidden;

    /* Fondo con imagen */
    background-image: 
        linear-gradient(rgba(0,0,0,0.45), rgba(0,0,0,0.45)),
        url("playa.jpg");
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
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
            border-top: 8px solid #fff;
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
            background: #fff;
            padding: 30px;
            border-radius: 12px;
            max-width: 700px;
            width: 95%;
            text-align: center;
            box-shadow: 0 15px 30px rgba(0,0,0,0.2);
        }

        h1 {
            animation: brillo 3s infinite;
        }

        /* ===== JUEGO ARCADE ===== */
        .juego {
            margin-top: 25px;
        }

        .info {
            font-size: 18px;
            margin-bottom: 10px;
        }

        .area-juego {
            position: relative;
            background: #f4f4f4;
            height: 300px;
            border-radius: 10px;
            overflow: hidden;
            border: 2px solid #ddd;
        }

        .objetivo {
            position: absolute;
            width: 50px;
            height: 50px;
            background: radial-gradient(circle, #ff4d4d, #c70000);
            border-radius: 50%;
            cursor: pointer;
            animation: aparecer 0.3s ease;
        }

        .botones button {
            margin: 10px;
            padding: 12px 20px;
            font-size: 16px;
            border: none;
            border-radius: 8px;
            background: #4facfe;
            color: #fff;
            cursor: pointer;
        }

        .botones button:disabled {
            background: #aaa;
        }

        footer {
            margin-top: 20px;
            font-size: 14px;
            color: #888;
        }

        /* ===== ANIMACIONES ===== */
        @keyframes aparecer {
            from { transform: scale(0); opacity: 0; }
            to { transform: scale(1); opacity: 1; }
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
            <h1>Mini Juego Arcade</h1>
            <p>Hola, soy <strong>Ronald Dávila</strong>. Página de prueba de mi servidor web.</p>

            <div class="juego">
                <div class="info">
                    🎯 Puntos: <span id="puntos">0</span> |
                    ⏱️ Tiempo: <span id="tiempo">20</span>s
                </div>

                <div class="area-juego" id="areaJuego"></div>

                <div class="botones">
                    <button id="btnIniciar">Iniciar juego</button>
                </div>
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

        // Juego Arcade
        const area = document.getElementById("areaJuego");
        const puntosSpan = document.getElementById("puntos");
        const tiempoSpan = document.getElementById("tiempo");
        const btnIniciar = document.getElementById("btnIniciar");

        let puntos = 0;
        let tiempo = 20;
        let intervaloTiempo;
        let intervaloObjetivo;

        function crearObjetivo() {
            area.innerHTML = "";
            const obj = document.createElement("div");
            obj.classList.add("objetivo");

            const x = Math.random() * (area.clientWidth - 50);
            const y = Math.random() * (area.clientHeight - 50);

            obj.style.left = x + "px";
            obj.style.top = y + "px";

            obj.addEventListener("click", () => {
                puntos++;
                puntosSpan.textContent = puntos;
                crearObjetivo();
            });

            area.appendChild(obj);
        }

        btnIniciar.addEventListener("click", () => {
            puntos = 0;
            tiempo = 20;
            puntosSpan.textContent = puntos;
            tiempoSpan.textContent = tiempo;
            btnIniciar.disabled = true;

            crearObjetivo();

            intervaloObjetivo = setInterval(crearObjetivo, 1000);

            intervaloTiempo = setInterval(() => {
                tiempo--;
                tiempoSpan.textContent = tiempo;

                if (tiempo === 0) {
                    clearInterval(intervaloTiempo);
                    clearInterval(intervaloObjetivo);
                    area.innerHTML = "";
                    btnIniciar.disabled = false;
                    alert("🎮 Juego terminado\nPuntos obtenidos: " + puntos);
                }
            }, 1000);
        });
    </script>

</body>
</html>
