<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Página de Prueba - Ronald Dávila Moraga </title>
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
            width: 8
