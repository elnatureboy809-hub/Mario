<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>¿Me perdonas?</title>
    <style>
        /* Evita que aparezcan barras de scroll si el botón se sale un poco */
        body { 
            text-align: center; 
            font-family: 'Arial', sans-serif; 
            background-color: #ffebee; 
            margin: 0;
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            overflow: hidden; 
        }
        #figura { font-size: 100px; transition: transform 0.3s; }
        h1 { color: #d32f2f; margin-bottom: 20px; padding: 0 10px; }
        .botones { position: relative; width: 100%; height: 100px; }
        button { 
            padding: 15px 30px; 
            font-size: 18px; 
            cursor: pointer; 
            border: none; 
            border-radius: 10px; 
            transition: all 0.2s ease;
        }
        #btnSi { background-color: #4caf50; color: white; }
        #btnNo { 
            background-color: #f44336; 
            color: white; 
            position: absolute; /* Importante para que se mueva por toda la pantalla */
            left: 55%; /* Posición inicial */
        }
    </style>
</head>
<body>

    <div id="figura">🧸</div>
    <h1>Feliz San Valentín, te casarias conmigo?</h1>

    <div class="botones">
        <button id="btnSi" onclick="perdonado()">Sí</button>
        <button id="btnNo" onmouseover="moverBoton()" onclick="moverBoton()">No</button>
    </div>

    <script>
        let intentos = 0;

        function moverBoton() {
            const btnNo = document.getElementById("btnNo");
            const figura = document.getElementById("figura");
            
            intentos++;

            // Calculamos posiciones aleatorias dentro del ancho y alto de la pantalla
            // Restamos parte del tamaño del botón para que no se salga del borde
            const x = Math.random() * (window.innerWidth - btnNo.offsetWidth);
            const y = Math.random() * (window.innerHeight - btnNo.offsetHeight);

            btnNo.style.position = "fixed"; // Cambia a fixed para moverse por TODA la pantalla
            btnNo.style.left = x + "px";
            btnNo.style.top = y + "px";

            // Efecto extra: La figura hace un pequeño salto cada vez que fallan
            figura.style.transform = `scale(${1 + (intentos * 0.05)})`;
            
            // Si lo intenta muchas veces, el botón se vuelve más pequeño (opcional)
            if(intentos > 5) {
                btnNo.style.padding = "5px 10px";
                btnNo.style.fontSize = "12px";
            }
        }

        function perdonado() {
            document.body.innerHTML = `
                <div style="font-size: 100px;">❤️</div>
                <h1 style="color: #d32f2f;">¡Sabía que dirías que sí!</h1>
                <p>Ya que insistes, pues nos casamos, preparate!</p>
            `;
        }
    </script>
</body>
</html>
