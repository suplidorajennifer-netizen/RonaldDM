<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Página de Prueba </title>
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
            to {
                transform: rotate(360deg);
            }
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
            padding: 35px;
            border-radius: 12px;
            max-width: 600px;
            text-align: center;
            box-shadow: 0 15px 30px rgba(0,0,0,0.2);
            animation: aparecer 1.5s ease-out, flotar 4s ease-in-out infinite;
        }

        h1 {
            color: #333;
            margin-bottom: 15px;
            animation: brillo 3s infinite;
        }

        p {
            color: #555;
            font-size: 18px;
            line-height: 1.6;
        }

        footer {
            margin-top: 25px;
            font-size: 14px;
            color: #888;
        }

        /* ===== ANIMACIONES ===== */
        @keyframes aparecer {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes flotar {
            0%, 100% {
                transform: translateY(0);
            }
            50% {
                transform: translateY(-8px);
            }
        }

        @keyframes brillo {
            0% {
                text-shadow: 0 0 5px rgba(79,172,254,0.5);
            }
            50% {
                text-shadow: 0 0 15px rgba(79,172,254,1);
            }
            100% {
                text-shadow: 0 0 5px rgba(79,172,254,0.5);
            }
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
            <h1> Ronald Dávila Moraga</h1>
            <p>Hola, Estoy Poniendo <strong>Una Pagina Aprueba</strong>.</p>
            <p>
                Esta es una página de prueba que estoy utilizando para poner a prueba
                mi servidor web.
            </p>
            <p>
                Si estás viendo esta página correctamente, el servidor está funcionando.
            </p>
            <footer>
                © 2026 -  Ronald Dávila Moraga CR
            </footer>
        </div>
    </div>

    <script>
        window.addEventListener("load", () => {
            setTimeout(() => {
                document.getElementById("loader").style.opacity = "0";
                document.getElementById("loader").style.visibility = "hidden";
                document.getElementById("contenido").classList.add("mostrar");
                document.body.style.overflow = "auto";
            }, 1500); // tiempo del loader (ms)
        });
    </script>

</body>
</html>
