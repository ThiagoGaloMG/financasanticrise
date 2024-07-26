<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Contador Regressivo</title>
    <style>
        /* Estilos CSS (personalize conforme necessário) */
        #contador {
            font-size: 24px;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <div id="contador"></div>

    <script>
        // Data final para o contador (substitua com a data do seu evento ou prazo)
        const dataFinal = new Date('2023-12-31 23:59:59').getTime();

        function atualizarContador() {
            const agora = new Date().getTime();
            const diferenca = dataFinal - agora;

            const dias = Math.floor(diferenca / (1000 * 60 * 60 * 24));
            const horas = Math.floor((diferenca % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            const minutos = Math.floor((diferenca % (1000 * 60 * 60)) / (1000 * 60));
            const segundos = Math.floor((diferenca % (1000 * 60)) / 1000);

            document.getElementById('contador').textContent = `${dias}d ${horas}h ${minutos}m ${segundos}s`;

            if (diferenca <= 0) {
                clearInterval(interval);
                document.getElementById('contador').textContent = 'Contagem encerrada!';
            }
        }

        const interval = setInterval(atualizarContador, 1000);
    </script>
</body>
</html>
