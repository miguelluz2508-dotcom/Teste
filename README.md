<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sensi Lzz - Script no Canvas</title>
    <style>
        body {
            background-color: #000000; /* Preto */
            color: #FFFFFF; /* Branco */
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            flex-direction: column;
        }
        h1 {
            color: #800080; /* Roxo */
            margin-bottom: 20px;
        }
        canvas {
            border: 2px solid #800080; /* Roxo */
            background-color: #000000;
        }
    </style>
</head>
<body>
    <h1>Sensi Lzz</h1>
    <canvas id="scriptCanvas" width="800" height="600"></canvas>

    <script>
        const canvas = document.getElementById('scriptCanvas');
        const ctx = canvas.getContext('2d');

        // Definir cores
        ctx.fillStyle = '#FFFFFF'; // Branco para texto
        ctx.font = '16px Arial';

        // Código do script original (para exibir no canvas)
        const scriptCode = `
        // Função para detectar o dispositivo baseado no userAgent
        function detectDevice() {
            const userAgent = navigator.userAgent;
            if (/iPhone/i.test(userAgent)) {
                return "iPhone";
            } else if (/Android/i.test(userAgent)) {
                return "Android";
            } else if (/Windows Phone/i.test(userAgent)) {
                return "Windows Phone";
            } else {
                return "Dispositivo Desconhecido";
            }
        }

        // Exibir a mensagem com o dispositivo detectado
        const device = detectDevice();
        document.getElementById('message').innerHTML = \`\${device} esse é seu celular?\`;

        // Botão Sim: Esconder a mensagem e botões
        document.getElementById('yesBtn').addEventListener('click', function() {
            document.getElementById('message').style.display = 'none';
            document.getElementById('buttons').style.display = 'none';
        });

        // Botão Não: Mostrar a caixa de input
        document.getElementById('noBtn').addEventListener('click', function() {
            document.getElementById('inputBox').style.display = 'block';
        });

        // Botão Enviar: Processar o input
        document.getElementById('submitBtn').addEventListener('click', function() {
            const userDevice = document.getElementById('deviceInput').value;
            if (userDevice.trim() !== '') {
                alert(\`Você digitou: \${userDevice}\`);
            } else {
                alert('Por favor, digite o nome do seu celular.');
            }
        });
        `;

        // Quebrar o texto em linhas para exibir no canvas
        const lines = scriptCode.split('\n');
        let y = 30; // Posição Y inicial
        lines.forEach(line => {
            ctx.fillText(line, 10, y);
            y += 20; // Espaçamento entre linhas
        });
    </script>
</body>
</html>
