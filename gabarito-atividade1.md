# 📖 Gabarito Comentado e Guia de Aprendizado: Atividade Prática 1
> **Objetivo Didático:** Este material apresenta a resolução completa da atividade prática passo a passo, detalhando o funcionamento de métodos de array modernos do JavaScript (ES6+), modularização com CommonJS no Node.js e gerenciamento de scripts com NPM.

---

## 📂 Estrutura de Pastas do Projeto

Ao final da atividade, a estrutura do seu projeto deve ficar organizada da seguinte forma:

```text
meu-projeto/
├── funcoes.js         # Módulo que exporta a lógica de manipulação dos dados
├── index.js           # Arquivo principal que consome o módulo e executa os testes
└── package.json       # Manifesto do projeto com dependências e scripts de execução
```

---

## 🛠️ Passo 1: O Módulo de Funções (`funcoes.js`)

Na **Parte 2**, o objetivo era separar a lógica das funções em um módulo reutilizável. Abaixo está o código completo do arquivo `funcoes.js` com explicações linha por linha.

```javascript
/**
 * funcoes.js
 * Módulo com funções utilitárias para filtrar, mapear e buscar dados no catálogo.
 */

// 1. Filtrando itens não assistidos usando .filter()
// O método .filter() percorre cada item do array e retorna um NOVO array
// contendo apenas os elementos que retornarem 'true' para a condição testada.
const listarNaoAssistidos = (catalogo) => {
    // Retornamos true se assistido for falso (!item.assistido ou item.assistido === false)
    return catalogo.filter(item => item.assistido === false);
};

// 2. Extraindo e transformando os títulos em maiúsculas usando .map()
// O método .map() percorre o array e transforma cada elemento em um novo valor,
// gerando um novo array com a mesma quantidade de elementos do original.
const listarTitulosMaiusculos = (catalogo) => {
    // Para cada item, extraímos o título e aplicamos .toUpperCase()
    return catalogo.map(item => item.titulo.toUpperCase());
};

// 3. Buscando um item específico por ID usando .find()
// O método .find() percorre o array e devolve o PRIMEIRO elemento que satisfizer a condição.
// Se não encontrar nenhum elemento com o ID solicitado, retorna 'undefined'.
const buscarPorId = (catalogo, id) => {
    return catalogo.find(item => item.id === id);
};

// 4. Exportação das funções no padrão CommonJS
// Tornamos as funções disponíveis para serem importadas por outros arquivos via require()
module.exports = {
    listarNaoAssistidos,
    listarTitulosMaiusculos,
    buscarPorId
};
```

### 💡 Por que usamos esses métodos?
| Método | O que faz | O que retorna | Quando usar? |
| :--- | :--- | :--- | :--- |
| **`.filter()`** | Filtra elementos com base em uma condição (booleano). | Um **novo array** com os elementos aprovados. | Quando você quer uma lista menor (ex: apenas itens pendentes). |
| **`.map()`** | Transforma cada elemento em outro formato ou valor. | Um **novo array** com o mesmo tamanho do original. | Quando você quer extrair um campo ou alterar formato (ex: só títulos em MAIÚSCULAS). |
| **`.find()`** | Procura o primeiro registro que atenda a um critério. | Um **único objeto** ou `undefined`. | Quando você quer buscar por chave única (ex: buscar por ID). |

---

## 🚀 Passo 2: O Arquivo Principal de Execução (`index.js`)

O arquivo `index.js` contém a base de dados em memória (`catalogo`), importa as funções que foram exportadas em `funcoes.js` e executa testes práticos.

```javascript
/**
 * index.js
 * Ponto de entrada da aplicação.
 */

// 1. Importando as funções do módulo funcoes.js usando require()
// Como é um arquivo local da mesma pasta, usamos o prefixo relativo './'
const { listarNaoAssistidos, listarTitulosMaiusculos, buscarPorId } = require('./funcoes');

// 2. Base de dados em memória: Array de objetos representando filmes/jogos
const catalogo = [
    {
        id: 1,
        titulo: "Interestelar",
        genero: "Ficção Científica",
        ano: 2014,
        assistido: true
    },
    {
        id: 2,
        titulo: "O Poderoso Chefão",
        genero: "Drama / Crime",
        ano: 1972,
        assistido: false
    },
    {
        id: 3,
        titulo: "Matrix",
        genero: "Ação / Ficção",
        ano: 1999,
        assistido: true
    },
    {
        id: 4,
        titulo: "Duna: Parte 2",
        genero: "Ficção Científica",
        ano: 2024,
        assistido: false
    }
];

// ==========================================
// TESTES E EXECUÇÃO DOS MÉTODOS
// ==========================================

console.log("=== 🎬 CATÁLOGO DE FILMES / JOGOS ===");
console.log(`Total de itens cadastrados: ${catalogo.length}
`);

// Teste 1: Filtrar itens não assistidos
console.log("--- 1. Itens Não Assistidos (assistido: false) ---");
const naoAssistidos = listarNaoAssistidos(catalogo);
console.log(naoAssistidos);

// Teste 2: Mapear apenas títulos em maiúsculas
console.log("
--- 2. Lista de Títulos em Maiúsculas ---");
const titulos = listarTitulosMaiusculos(catalogo);
console.log(titulos);

// Teste 3: Buscar por ID existente
console.log("
--- 3. Busca por ID (ID = 2) ---");
const filmeEncontrado = buscarPorId(catalogo, 2);
console.log(filmeEncontrado);

// Teste 4: Busca por ID inexistente (Tratamento de retorno)
console.log("
--- 4. Busca por ID Inexistente (ID = 99) ---");
const filmeInexistente = buscarPorId(catalogo, 99);
if (filmeInexistente) {
    console.log("Filme encontrado:", filmeInexistente);
} else {
    console.log("⚠️ Nenhum filme encontrado com o ID especificado.");
}
```

---

## 📦 Passo 3: Configuração do NPM e `package.json`

### 1. Inicializar o projeto
No terminal, dentro da pasta do projeto:
```bash
npm init -y
```
Isso cria o arquivo `package.json` com as configurações padrão.

### 2. Configurar o script `"start"`
Abra o `package.json` e configure a seção `"scripts"` para utilizar o `--watch` nativo do Node.js:

```json
{
  "name": "atividade1-reforco",
  "version": "1.0.0",
  "description": "Atividade de reforço em JavaScript e Node.js",
  "main": "index.js",
  "scripts": {
    "start": "node --watch index.js"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
```

> **Por que usar `node --watch index.js`?**  
> A flag `--watch` é um recurso nativo do Node.js (versões 18+). Ela reinicia o processo automaticamente toda vez que você salvar qualquer alteração em arquivos `.js`, dispensando a instalação de pacotes de terceiros como o `nodemon` para tarefas simples.

---

## 🖥️ Passo 4: Execução e Saída Esperada no Terminal

Execute o script configurado através do NPM:
```bash
npm run start
```

### Saída Esperada no Console:
```text
=== 🎬 CATÁLOGO DE FILMES / JOGOS ===
Total de itens cadastrados: 4

--- 1. Itens Não Assistidos (assistido: false) ---
[
  {
    id: 2,
    titulo: 'O Poderoso Chefão',
    genero: 'Drama / Crime',
    ano: 1972,
    assistido: false
  },
  {
    id: 4,
    titulo: 'Duna: Parte 2',
    genero: 'Ficção Científica',
    ano: 2024,
    assistido: false
  }
]

--- 2. Lista de Títulos em Maiúsculas ---
[ 'INTERESTELAR', 'O PODEROSO CHEFÃO', 'MATRIX', 'DUNA: PARTE 2' ]

--- 3. Busca por ID (ID = 2) ---
{
  id: 2,
  titulo: 'O Poderoso Chefão',
  genero: 'Drama / Crime',
  ano: 1972,
  assistido: false
}

--- 4. Busca por ID Inexistente (ID = 99) ---
⚠️ Nenhum filme encontrado com o ID especificado.
```

---

## ⚠️ Erros Comuns e Dicas de Ouro

1. **Esquecer o `return` nas Arrow Functions:**
   * ✅ `item => item.id === id` *(retorno implícito: funciona sem chaves `{}`)*.
   * ✅ `item => { return item.id === id; }` *(retorno explícito: obrigatório quando se usa chaves `{}`)*.
   * ❌ `item => { item.id === id; }` *(retorna `undefined` e não filtra nem encontra nada!)*.

2. **Esquecer o ponto e barra no `require('./funcoes')`:**
   * No Node.js, arquivos locais exigem caminho relativo (`./funcoes`). Sem o `./`, o Node tenta procurar dentro de `node_modules` e dispara o erro `MODULE_NOT_FOUND`.

3. **Diferença crucial entre `.filter()` e `.find()`:**
   * O `.filter()` **sempre** retorna uma **lista (array)**, mesmo que encontre apenas 1 item ou nenhum (`[]`).
   * O `.find()` retorna **diretamente o objeto** ou `undefined`. Para buscar por chave única como `id`, o `.find()` é a melhor escolha.
