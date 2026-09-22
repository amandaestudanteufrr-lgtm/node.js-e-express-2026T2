# ⚡ Fundamentos de JavaScript para o Express: Guia Pré-Aula 03

> **Para que serve este guia?**  
> Antes de colocarmos a mão na massa com o **Express.js** na Aula 03, é fundamental dominar alguns recursos essenciais do JavaScript moderno (ES6+). Este documento foi preparado para você revisar a sintaxe e entender **onde e por que** usamos cada um desses conceitos ao construir APIs.

---

## 1. Funções Tradicionais vs. Arrow Functions (`=>`)

No Express, quase tudo o que você escreve são funções que respondem a requisições. As **Arrow Functions** são o padrão moderno mais utilizado.

### 🔹 Sintaxe Comparativa

```javascript
// 1. Função Tradicional (palavra-chave 'function')
function saudacao(nome) {
    return "Olá, " + nome + "!";
}

// 2. Arrow Function (com chaves e retorno explícito)
const saudacaoArrow = (nome) => {
    return `Olá, ${nome}!`;
};

// 3. Arrow Function Concisa (retorno implícito de linha única)
const saudacaoCurta = nome => `Olá, ${nome}!`;
```

### 🔹 O Retorno Implícito (Cuidado com as Chaves!)
* **Sem chaves `{}`:** O valor após a seta `=>` é retornado **automaticamente**.
  ```javascript
  const somar = (a, b) => a + b; // Retorna o resultado da soma
  ```
* **Com chaves `{}`:** O corpo da função exige a palavra-chave `return`.
  ```javascript
  const somar = (a, b) => {
      return a + b; // Obrigatório usar 'return' aqui!
  };
  ```

### 🔹 Diferença do `this` (Explicado de Forma Simples)
* **Funções tradicionais (`function`):** O valor de `this` muda dependendo de **quem** chamou a função (contexto dinâmico).
* **Arrow Functions (`=>`):** Elas **não** criam seu próprio `this`. Elas herdam o `this` do lugar onde foram declaradas (contexto léxico).
* **No Express:** Como raramente usamos classes com `this` ao definir rotas simples, a Arrow Function é preferida por ser mais limpa, legível e moderna.

### 🚀 Onde você verá isso no Express hoje?
Toda rota no Express recebe uma função de retorno (callback) escrita quase sempre como Arrow Function:

```javascript
// Exemplo que veremos na Aula 03:
app.get('/usuarios', (req, res) => {
    res.send("Lista de usuários!");
});
```

---

## 2. Interpolação de Strings (Template Literals / Template Strings)

Chega de fazer concatenações confusas usando o operador `+` e aspas! O JavaScript moderno permite criar strings delimitadas por **crases ( \`\` )**.

### 🔹 Comparativo

```javascript
const porta = 3000;
const status = "online";

// ❌ Modo Antigo (Concatenação com '+'): fácil de errar espaços
console.log("Servidor rodando na porta " + porta + " e status: " + status + ".");

// ✅ Modo Moderno (Template String com `${}`): muito mais legível
console.log(`Servidor rodando na porta ${porta} e status: ${status}.`);
```

### 🔹 Vantagens:
1. **Interpolar variáveis e expressões:** Você pode colocar qualquer código JS dentro de `${}` (ex: `${preco * 1.10}`).
2. **Múltiplas linhas sem quebra de código:**
   ```javascript
   const html = `
       <div>
           <h1>Bem-vindo!</h1>
           <p>Servidor conectado com sucesso.</p>
       </div>
   `;
   ```

### 🚀 Onde você verá isso no Express hoje?
Ao inicializar o servidor e imprimir mensagens no terminal:
```javascript
const PORT = 3000;

app.listen(PORT, () => {
    console.log(`🚀 Servidor rodando com sucesso em http://localhost:${PORT}`);
});
```

---

## 3. Desestruturação de Objetos (Destructuring)

A **desestruturação** permite extrair propriedades de dentro de um objeto diretamente para variáveis individuais, com uma sintaxe elegante e direta.

### 🔹 Exemplo Prático

```javascript
const usuario = {
    id: 1,
    nome: "Ana Souza",
    email: "ana@email.com",
    cargo: "Desenvolvedora"
};

// ❌ Modo Tradicional: repetitivo
const nome = usuario.nome;
const email = usuario.email;

// ✅ Com Desestruturação: extrai as propriedades em uma linha só!
const { nome, email } = usuario;

console.log(nome);  // "Ana Souza"
console.log(email); // "ana@email.com"
```

### 🚀 Onde você verá isso no Express hoje e nas próximas aulas?
Nas requisições HTTP, quando os clientes enviarem dados ou parâmetros na URL:

```javascript
// Ao receber dados enviados no corpo da requisição (POST):
app.post('/produtos', (req, res) => {
    // Extrai direto do req.body
    const { titulo, preco, categoria } = req.body;
    
    console.log(`Criando produto: ${titulo} por R$ ${preco}`);
});

// Ao receber parâmetros na URL (ex: /produtos/42):
app.get('/produtos/:id', (req, res) => {
    const { id } = req.params; // Extrai o id direto de req.params
});
```

---

## 4. Callbacks: Funções como Argumentos

No JavaScript, funções são tratadas como **cidadãs de primeira classe**. Isso significa que uma função pode ser guardada em uma variável e **passada como parâmetro para outra função**. Essa função que é passada chama-se **Callback**.

### 🔹 Analogia da Vida Real: O Restaurante
1. Você vai a uma lanchonete e faz um pedido (Requisição).
2. O garçom anota seu número e diz: *"Vá se sentar, quando o prato estiver pronto, eu te chamo"*.
3. O garçom não trava a fila esperando o cozinheiro fritar o hambúrguer. Ele atende os outros clientes.
4. Quando o lanche fica pronto, ele dispara o aviso (Callback) e entrega o prato para você.

### 🚀 Onde você verá isso no Express?
O Express é 100% orientado a callbacks:
```javascript
// Você entrega para o Express:
// 1º argumento: O caminho ('/sobre')
// 2º argumento: O callback (a função que ele deve executar quando alguém acessar essa URL)
app.get('/sobre', (req, res) => {
    res.send("Página Sobre Nós!");
});
```

---

## 5. Objetos JavaScript vs. JSON (JavaScript Object Notation)

Uma API web conversa com o mundo externo (frontends em React/Vue, aplicativos de celular, outros servidores). O formato universal dessa conversa é o **JSON**.

### 🔹 A Diferença:
* **Objeto JavaScript:** É uma estrutura viva na memória do Node.js. Chaves podem não ter aspas, suporta funções, datas, tipos complexos.
  ```javascript
  const produto = {
      nome: "Teclado Mecânico",
      preco: 250,
      disponivel: true
  };
  ```
* **JSON:** É um formato puramente **textual** padronizado. Todas as chaves **obrigatoriamente** têm aspas duplas, e os valores são apenas dados puros (texto, números, booleanos, arrays, objetos ou null).
  ```json
  {
      "nome": "Teclado Mecânico",
      "preco": 250,
      "disponivel": true
  }
  ```

### 🚀 Onde você verá isso no Express?
Para responder ao cliente com dados estruturados, o Express possui o método helper `res.json()`:
```javascript
app.get('/produto', (req, res) => {
    // O Express converte o objeto JavaScript em texto JSON e define os headers corretos automaticamente!
    res.json({
        id: 101,
        nome: "Mouse Gamer",
        emEstoque: true
    });
});
```

---

## 6. O Modelo Mental do Express: `req` (Requisição) e `res` (Resposta)

Sempre que vir a assinatura `(req, res) => { ... }`, lembre-se do ciclo cliente-servidor:

```text
       Cliente (Navegador / Postman)
                   │  ▲
 1. Envia Pedido   │  │  2. Devolve Prato
    (REQUEST: req) │  │     (RESPONSE: res)
                   ▼  │
             Servidor Express
```

* **`req` (Request / Requisição):** Representa tudo o que vem de fora para dentro.
  * O que o cliente quer? (`req.method`, `req.url`)
  * Parâmetros na URL? (`req.params`, `req.query`)
  * Dados enviados no formulário/JSON? (`req.body`)
  * Headers / Tokens? (`req.headers`)

* **`res` (Response / Resposta):** Representa tudo o que o seu servidor devolve para o cliente.
  * Devolver texto puro: `res.send("Olá!")`
  * Devolver dados estruturados: `res.json({ sucesso: true })`
  * Definir o código HTTP de status: `res.status(201).json(...)` ou `res.status(404).send(...)`

---

## 🧠 Resumo Rápido para a Aula

| Conceito | Exemplo Rápido | Uso no Express |
| :--- | :--- | :--- |
| **Arrow Function** | `(req, res) => { ... }` | Controladores de rotas e callbacks |
| **Template String** | `` `Porta: ${PORT}` `` | Logs e URLs dinâmicas |
| **Destructuring** | `const { nome } = req.body;` | Captura de dados limpa |
| **res.json()** | `res.json({ ok: true })` | Envio de respostas da API |
| **res.status()** | `res.status(404).send()` | Códigos de resposta HTTP |

Agora você está com a bagagem pronta para aproveitar ao máximo a **Aula 03: Introdução ao Express e Primeiro Servidor**! 🚀
