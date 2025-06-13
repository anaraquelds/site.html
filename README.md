<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Funções em JavaScript</title>
    <style>
        body {
            margin: 0;
            font-family: 'Segoe UI', sans-serif;
            background: linear-gradient(135deg, #e0f7fa, #ffffff);
            color: #333;
        }
        .container {
            max-width: 900px;
            margin: 40px auto;
            background: #ffffffee;
            padding: 30px;
            border-radius: 12px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.1);
        }
        h1 {
            text-align: center;
            color: #007bff;
        }
        .funcao {
            border-left: 5px solid #007bff;
            padding: 20px;
            margin-bottom: 25px;
            background-color: #f9f9f9;
            border-radius: 8px;
            transition: background 0.3s;
        }
        .funcao:hover {
            background-color: #f0f8ff;
        }
        h2 {
            margin-top: 0;
            color: #333;
        }
        input[type="number"], input[type="text"] {
            width: 80px;
            padding: 10px;
            margin: 6px 4px 12px 0;
            border: 1px solid #ccc;
            border-radius: 6px;
            font-size: 16px;
        }
        button {
            padding: 10px 18px;
            font-size: 15px;
            background-color: #007bff;
            color: white;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            transition: background 0.3s;
        }
        button:hover {
            background-color: #0056b3;
        }
        .resultado {
            margin-top: 10px;
            font-weight: bold;
            color: #333;
            transition: all 0.3s ease;
        }
    </style>
</head>
<body>

<div class="container">
    <h1>🧠 Teste de Funções em JavaScript</h1>

    <div class="funcao">
        <h2>🔢 1. Maior e Menor Valor</h2>
        <p>Digite cinco valores:</p>
        <input type="number" id="n1">
        <input type="number" id="n2">
        <input type="number" id="n3">
        <input type="number" id="n4">
        <input type="number" id="n5">
        <br>
        <button onclick="executarMaiorMenor()">Verificar</button>
        <p id="resultado1" class="resultado"></p>
    </div>

    <div class="funcao">
        <h2>🗣️ 2. Verifica Vogal</h2>
        <p>Digite um caractere:</p>
        <input type="text" id="char" maxlength="1">
        <br>
        <button onclick="executarVogal()">Verificar</button>
        <p id="resultado2" class="resultado"></p>
    </div>

    <div class="funcao">
        <h2>🔁 3. Pares em um Intervalo</h2>
        <p>Digite os limites:</p>
        <input type="number" id="li" placeholder="Início">
        <input type="number" id="ls" placeholder="Fim">
        <br>
        <button onclick="executarLimites()">Calcular</button>
        <p id="resultado3" class="resultado"></p>
    </div>

    <div class="funcao">
        <h2>📊 4. Ordenar Valores</h2>
        <p>Digite três números:</p>
        <input type="number" id="o1">
        <input type="number" id="o2">
        <input type="number" id="o3">
        <br>
        <button onclick="executarOrdem()">Ordenar</button>
        <p id="resultado4" class="resultado"></p>
    </div>

    <div class="funcao">
        <h2>➕➖ 5. Positivo ou Negativo</h2>
        <p>Digite um número:</p>
        <input type="number" id="valPosNeg">
        <br>
        <button onclick="executarPositivoNegativo()">Verificar</button>
        <p id="resultado5" class="resultado"></p>
    </div>

    <div class="funcao">
        <h2>⚖️ 6. Par ou Ímpar</h2>
        <p>Digite um número:</p>
        <input type="number" id="valParImpar">
        <br>
        <button onclick="executarParImpar()">Verificar</button>
        <p id="resultado6" class="resultado"></p>
    </div>

</div>

<script>
    function MAIOR_MENOR(a, b, c, d, e) {
        const numeros = [a, b, c, d, e];
        const maior = Math.max(...numeros);
        const menor = Math.min(...numeros);
        return `📈 Maior: ${maior} | 📉 Menor: ${menor}`;
    }

    function executarMaiorMenor() {
        const valores = ['n1','n2','n3','n4','n5'].map(id => parseInt(document.getElementById(id).value));
        if (valores.some(isNaN)) {
            alert("Preencha todos os campos.");
            return;
        }
        document.getElementById('resultado1').innerText = MAIOR_MENOR(...valores);
    }

    function VOGAL(c) {
        const vogais = 'aeiouAEIOU';
        return vogais.includes(c) ? 1 : 0;
    }

    function executarVogal() {
        const char = document.getElementById('char').value;
        if (char.length !== 1) {
            alert("Digite apenas um caractere.");
            return;
        }
        const r = VOGAL(char);
        document.getElementById('resultado2').innerText = r ? "✅ É uma vogal!" : "❌ Não é vogal.";
    }

    function LIMITES(li, ls) {
        let pares = [], soma = 0;
        for (let i = li + 1; i < ls; i++) {
            if (i % 2 === 0) {
                pares.push(i);
                soma += i;
            }
        }
        return `🔢 Pares: [${pares.join(', ')}] | Soma: ${soma}`;
    }

    function executarLimites() {
        const li = parseInt(document.getElementById('li').value);
        const ls = parseInt(document.getElementById('ls').value);
        if (isNaN(li) || isNaN(ls) || li >= ls) {
            alert("Digite um intervalo válido (início < fim).");
            return;
        }
        document.getElementById('resultado3').innerText = LIMITES(li, ls);
    }

    function ORDEM(a, b, c) {
        return [a, b, c].sort((x, y) => x - y);
    }

    function executarOrdem() {
        const valores = ['o1','o2','o3'].map(id => parseInt(document.getElementById(id).value));
        if (valores.some(isNaN)) {
            alert("Preencha todos os três campos.");
            return;
        }
        const ordenado = ORDEM(...valores);
        document.getElementById('resultado4').innerText = `📊 Ordenado: [${ordenado.join(', ')}]`;
    }

    function POSITIVO_NEGATIVO(x) {
        return x >= 0;
    }

    function executarPositivoNegativo() {
        const x = parseInt(document.getElementById('valPosNeg').value);
        if (isNaN(x)) {
            alert("Digite um número.");
            return;
        }
        document.getElementById('resultado5').innerText = POSITIVO_NEGATIVO(x) ? "✅ Positivo ou zero" : "❌ Negativo";
    }

    function PAR_IMPAR(x) {
        return x % 2 === 0;
    }

    function executarParImpar() {
        const x = parseInt(document.getElementById('valParImpar').value);
        if (isNaN(x)) {
            alert("Digite um número.");
            return;
        }
        document.getElementById('resultado6').innerText = PAR_IMPAR(x) ? "✅ Par" : "🔻 Ímpar";
    }
</script>

</body>
</html>