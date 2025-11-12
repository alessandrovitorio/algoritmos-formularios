# 🧠 Algoritmos com Formulários e DOM

## 🎯 Objetivo

Usar formulários e manipulação do DOM (`createElement`, `innerHTML`) como **formas de entrada e saída** para os algoritmos criados em JavaScript.
O foco é **praticar lógica**, mas agora com **interação visual** no navegador.

---

## 🗂️ Sumário

1. Conceito: Formulário como entrada de dados
2. Processamento: o algoritmo em ação
3. Saída: exibindo resultados com DOM
4. Usando `createElement`
5. Usando `innerHTML` e concatenação
6. Diferença prática entre os dois
7. Exercícios de fixação (com lógica)

---

## 1️⃣ Formulário como **entrada de dados**

Em um algoritmo tradicional, a entrada vem de `prompt()`.
Agora, o formulário será a **interface visual** dessa entrada.

```html
<form id="form-numeros">
  <input type="number" id="num1" placeholder="Número 1">
  <input type="number" id="num2" placeholder="Número 2">
  <button type="submit">Calcular</button>
</form>

<div id="saida"></div>
```

> Cada campo representa uma **variável de entrada** do algoritmo.

---

## 2️⃣ O algoritmo em ação

O evento `onsubmit` captura os dados e executa a lógica.

```js
const form = document.getElementById("form-numeros");
const saida = document.getElementById("saida");

form.onsubmit = function (event) {
  event.preventDefault();

  let n1 = parseFloat(document.getElementById("num1").value);
  let n2 = parseFloat(document.getElementById("num2").value);
  let soma = n1 + n2;

  saida.innerHTML = `<p>A soma é: <strong>${soma}</strong></p>`;
};
```

> 🧩 **Lógica aplicada:** Recebe dois números → processa (soma) → exibe o resultado.
> Este é um **algoritmo clássico**, agora visual.

---

## 3️⃣ A saída no DOM

Podemos apresentar resultados de várias formas:

* **innerHTML** → insere o resultado direto no HTML.
* **createElement** → cria elementos dinamicamente.
* **Concatenação (`+=`)** → acumula novos resultados sem apagar os anteriores.

---

## 4️⃣ Usando `createElement` (modo estruturado)

```js
function mostrarResultado(valor) {
  let p = document.createElement("p");
  p.textContent = `Resultado: ${valor}`;
  saida.appendChild(p);
}
```

> ✅ Bom para algoritmos com múltiplas saídas ou listas (ex: tabuada, lista de nomes).

Exemplo — Tabuada com DOM:

```js
function gerarTabuada(num) {
  saida.innerHTML = ""; // limpa antes de gerar
  for (let i = 1; i <= 10; i++) {
    let li = document.createElement("li");
    li.textContent = `${num} x ${i} = ${num * i}`;
    saida.appendChild(li);
  }
}
```

---

## 5️⃣ Usando `innerHTML` (modo rápido)

```js
function gerarTabuadaInnerHTML(num) {
  let conteudo = "";
  for (let i = 1; i <= 10; i++) {
    conteudo += `<li>${num} x ${i} = ${num * i}</li>`;
  }
  saida.innerHTML = conteudo;
}
```

> 💡 **Concatenação (`+=`)** junta as linhas HTML antes de exibir.
> É mais simples para algoritmos curtos, mas substitui o conteúdo anterior.

---

## 6️⃣ Diferença prática entre os dois

| Método                  | Vantagem                                                    | Quando usar                                                                             |
| :---------------------- | :---------------------------------------------------------- | :-------------------------------------------------------------------------------------- |
| **createElement**       | Manipula cada item individualmente, pode adicionar eventos  | Quando o algoritmo gera listas, itens dinâmicos ou precisa atualizar partes específicas |
| **innerHTML**           | Mais simples e direto                                       | Quando só precisa mostrar o resultado final ou atualizar tudo de uma vez                |
| **Concatenação (`+=`)** | Permite adicionar novos resultados sem apagar os anteriores | Quando quer registrar o “histórico” de execuções                                        |

---

## 7️⃣ Exercícios de Fixação (com lógica)

### 🧩 1. Soma de dois números

Monte um formulário com dois campos e um botão.
Ao enviar, mostre a soma no DOM usando `innerHTML`.

---

### 🧩 2. Verificar maior número

Crie um formulário com dois campos numéricos e exiba no DOM qual é o maior.

---

### 🧩 3. Tabuada visual

Entrada: um número.
Saída: gere a tabuada completa de 1 a 10 usando `createElement`.

---

### 🧩 4. Cadastrar nomes

Monte um formulário com campo de nome e botão “Adicionar”.
Cada envio deve incluir o nome em uma lista (sem apagar os anteriores).

> **Dica:** use `innerHTML +=` ou `appendChild`.

---

### 🧩 5. Média de notas

Crie campos para **3 notas**, e ao enviar o formulário:

* Calcule a média;
* Mostre o resultado;
* Indique se o aluno foi “Aprovado” ou “Reprovado”.

---

### 🧩 Desafio extra (integração)

Monte um **sistema de pedidos simples**:

* Formulário: nome do produto e preço
* Cada envio adiciona um item em uma lista
* Mostre o total acumulado dos valores

> Use `createElement` para a lista e `innerHTML` para o total.
