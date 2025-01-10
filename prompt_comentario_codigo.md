Código:
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Validação de Cartão</title>
    <style>
        /* Estilo básico para a página */
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        .container {
            max-width: 400px;
            margin: auto;
        }
        .form-group {
            margin-bottom: 15px;
        }
        label {
            display: block;
            font-weight: bold;
            margin-bottom: 5px;
        }
        input {
            width: 100%;
            padding: 8px;
            box-sizing: border-box;
        }
        #bandeira {
            margin-top: 10px;
            display: flex;
            align-items: center;
            gap: 10px;
            color: #333;
        }
        img {
            height: 30px;
            width: auto;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Validação de Cartão</h1>

        <!-- Campo para o nome no cartão -->
        <div class="form-group">
            <label for="nome">Nome no Cartão:</label>
            <input type="text" id="nome" placeholder="Digite o nome no cartão">
        </div>

        <!-- Campo para o número do cartão, com evento oninput para verificar a bandeira -->
        <div class="form-group">
            <label for="numero">Número do Cartão:</label>
            <input type="text" id="numero" placeholder="Digite o número do cartão" oninput="atualizarBandeira()">
        </div>

        <!-- Campo para a data de validade, com evento onblur para verificar se está vencido -->
        <div class="form-group">
            <label for="validade">Data de Validade (MM/AA):</label>
            <input type="text" id="validade" placeholder="MM/AA" onblur="verificarValidade()">
        </div>

        <!-- Campo para o código CVV -->
        <div class="form-group">
            <label for="codigo">Código Verificador (CVV):</label>
            <input type="text" id="codigo" placeholder="Digite o CVV">
        </div>

        <!-- Div para exibir a bandeira do cartão ou mensagem de erro -->
        <div id="bandeira">
            <span>Bandeira do cartão:</span>
            <span id="bandeira-icon"></span>
        </div>
    </div>

    <script>
        // URLs dos ícones das bandeiras dos cartões
        const iconesBandeiras = {
            "MasterCard": "https://upload.wikimedia.org/wikipedia/commons/2/2a/Mastercard-logo.svg",
            "Visa": "https://upload.wikimedia.org/wikipedia/commons/4/41/Visa_Logo.png",
            "American Express": "https://upload.wikimedia.org/wikipedia/commons/3/30/American_Express_logo.svg",
            "Diners Club": "https://upload.wikimedia.org/wikipedia/commons/a/a6/Diners_Club_Logo3.svg",
            "Discover": "https://upload.wikimedia.org/wikipedia/commons/6/6a/Discover_Card_logo.png",
            "EnRoute": "https://enroute.aircanada.com/wp-content/themes/enroute/assets/img/svg/Logos/enroute-logo-black.svg",
            "JCB": "https://upload.wikimedia.org/wikipedia/commons/4/40/JCB_logo.svg",
            "Voyager": "https://www.usbank.com/content/dam/usbank/images/commercial-banking/industry-expertise/transportation/fleet/photo-usbank-voyager-fleet-logo-top-centered.png",
            "Hipercard": "https://upload.wikimedia.org/wikipedia/commons/8/89/Hipercard_logo.svg",
            "Aura": "https://d1yjjnpx0p53s8.cloudfront.net/styles/logo-original-577x577/s3/102011/aura_0.gif?itok=tbkAl3Vl",
            "Elo": "https://upload.wikimedia.org/wikipedia/commons/c/c0/Elo_card_logo.png",
        };

        /**
         * Valida o número do cartão com base nas regras predefinidas
         * @param {string} numeroCartao - Número do cartão a ser validado
         * @returns {string|null} - Nome da bandeira ou null se não for válido
         */
        function validarCartao(numeroCartao) {
            const regras = [
                { bandeira: "MasterCard", regex: /^(5[1-5]|222[1-9]|22[3-9]\d|2[3-6]\d{2}|27[01]\d|2720)/ },
                { bandeira: "MasterCard", regex: /^4/ },
                { bandeira: "American Express", regex: /^(34|37)/ },
                { bandeira: "Diners Club", regex: /^3(?:0[0-5]|[68][0-9])[0-9]{11,12}$/ },
                { bandeira: "Discover", regex: /^(6011|65|64[4-9])/ },
                { bandeira: "EnRoute", regex: /^(2014|2149)/ },
                { bandeira: "JCB", regex: /^(?:2131|1800|35\d{3})\d{11}$/ },
                { bandeira: "Voyager", regex: /^8699/ },
                { bandeira: "Hipercard", regex: /^6062/ },
                { bandeira: "Aura", regex: /^50/ },
                { bandeira: "Elo", regex: /^(4011|4312|4389)/ },

            ];

            for (const regra of regras) {
                if (regra.regex.test(numeroCartao)) {
                    return regra.bandeira;
                }
            }

            return null;
        }

        /**
         * Atualiza a exibição da bandeira do cartão com base no número inserido
         */
        function atualizarBandeira() {
            const numeroCartao = document.getElementById("numero").value;
            const bandeira = validarCartao(numeroCartao);
            const bandeiraIcon = document.getElementById("bandeira-icon");

            if (bandeira) {
                // Exibe o ícone da bandeira do cartão
                bandeiraIcon.innerHTML = `<img src="${iconesBandeiras[bandeira]}" alt="${bandeira}">`;
            } else {
                // Exibe mensagem de erro
                bandeiraIcon.textContent = "Cartão não disponível";
            }
        }

        /**
         * Verifica se a data de validade do cartão é válida ou está vencida
         */
        function verificarValidade() {
            const validade = document.getElementById("validade").value;
            const [mes, ano] = validade.split("/").map(num => parseInt(num, 10));
            const dataAtual = new Date();
            const anoAtual = dataAtual.getFullYear() % 100; // Últimos dois dígitos do ano
            const mesAtual = dataAtual.getMonth();

            // Verifica se a data é válida e não está vencida
            if (!mes || !ano || mes < 1 || mes > 12 || ano < anoAtual || (ano === anoAtual && mes < mesAtual)) {
                alert("Cartão vencido!");
            }
        }
    </script>
</body>
</html>

Prompt:
Inclua comentários no código acima para documentar o que é feito em cada trecho