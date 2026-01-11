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
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0;
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

        /* Animaciones */
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

    <div class="contenedor">
        <h1>Página de Prueba</h1>
        <p>Hola, mi nombre es <strong>Ronald Dávila</strong>.</p>
        <p>
            Esta es una página de prueba que estoy utilizando para poner a prueba
            mi servidor web.
        </p>
        <p>
            Si estás viendo esta página correctamente, el servidor está funcionando.
        </p>
        <footer>
            © 2026 - Ronald Dávila
        </footer>
    </div>

</body>
</html>
