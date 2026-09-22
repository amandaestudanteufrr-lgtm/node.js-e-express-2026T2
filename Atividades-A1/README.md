# Atividades A1 â€” AvaliaÃ§Ã£o Inicial

## OrientaÃ§Ãµes gerais

Esta atividade vale como **A1** e deve ser desenvolvida com base no conteÃºdo estudado atÃ© a **Aula 4**. O aluno deve escolher apenas um nÃ­vel de desafio, de acordo com sua seguranÃ§a e domÃ­nio dos assuntos vistos em sala.

A entrega deve ser organizada dentro da pasta `Atividades-A1`, com uma subpasta contendo o nome do aluno. O envio final deve ser feito em uma branch com o nome do aluno, apÃ³s commit e push para o repositÃ³rio da turma.

## O que revisar

Antes de comeÃ§ar, Ã© recomendado revisar:

- **Aula 1:** Node.js, runtime, Event Loop, instalaÃ§Ã£o e mÃ³dulos.
- **Aula 2:** NPM, `package.json`, scripts e organizaÃ§Ã£o do projeto.
- **Aula 3:** Express, rotas, mÃ©todos HTTP e estrutura inicial de API.
- **Aula 4:** middlewares, `express.json()`, logging e fluxo de execuÃ§Ã£o no Express.

## Regras de entrega

- A atividade deve ser feita em uma **branch com o seu nome completo**.
- Dentro da pasta `Atividades-A1`, crie uma pasta para seu **turno** (`Vespertino` ou `Noturno`).
- Dentro da pasta do turno, crie uma pasta com o seu **nome completo**.
- O projeto deve ser bem organizado, com `README.md` e instruÃ§Ãµes de execuÃ§Ã£o.

## Como clonar e enviar

Siga os passos abaixo para garantir que sua atividade seja enviada corretamente.

### **Contribuindo com Fork e Pull Request (ObrigatÃ³rio)**

Para garantir um processo de revisÃ£o organizado, todas as entregas devem ser feitas atravÃ©s de um **Fork** do repositÃ³rio principal, seguido por um **Pull Request**. Este Ã© o fluxo de trabalho padrÃ£o para contribuir com projetos no GitHub.

**Passo a passo:**

1.  **FaÃ§a o Fork:** No topo da pÃ¡gina do repositÃ³rio original, clique no botÃ£o "Fork". Isso criarÃ¡ uma cÃ³pia do repositÃ³rio na sua prÃ³pria conta do GitHub.

2.  **Clone o seu Fork:** Clone o repositÃ³rio que vocÃª acabou de forkar para a sua mÃ¡quina local.

    ```bash
    git clone https://github.com/SEU-USUARIO/node.js-e-express-2026T2.git
    cd node.js-e-express-2026T2
    ```

3.  **Crie sua Branch:** Crie uma branch especÃ­fica para a sua atividade.

    ```bash
    git checkout -b "seu-nome-completo"
    ```

4.  **Desenvolva sua Atividade:** Crie sua pasta e arquivos de atividade conforme as orientaÃ§Ãµes abaixo.

5.  **Commit e Push para o seu Fork:** ApÃ³s finalizar, envie as alteraÃ§Ãµes para o _seu_ repositÃ³rio (fork).

    ```bash
    git add .
    git commit -m "A1: Atividade de [Seu Nome Completo] - [Seu Turno]"
    git push origin "seu-nome-completo"
    ```

6.  **Abra um Pull Request:** Volte para a pÃ¡gina do seu fork no GitHub. VocÃª verÃ¡ um aviso para "Compare & pull request". Clique nele, revise suas alteraÃ§Ãµes e abra o pull request para o repositÃ³rio original.

## NÃ­vel 1 â€” BÃ¡sico

### Objetivo

Construir uma API simples para treinar mÃ³dulos, rotas e envio de JSON. Esse nÃ­vel Ã© indicado para quem ainda estÃ¡ consolidando os fundamentos.

### Atividade

Criar uma API de **alunos** ou **produtos** com os seguintes requisitos:

- Usar pelo menos **um mÃ³dulo prÃ³prio** para separar uma funÃ§Ã£o da aplicaÃ§Ã£o.
- Criar `GET /alunos` ou `GET /produtos` para listar registros.
- Criar `POST /alunos` ou `POST /produtos` para adicionar registros em memÃ³ria.
- Habilitar `express.json()` para receber corpo em JSON.
- Retornar `200` na listagem e `201` na criaÃ§Ã£o.

### O que entregar

- CÃ³digo-fonte organizado.
- `README.md` com instruÃ§Ãµes de execuÃ§Ã£o.
- Estrutura mÃ­nima de pastas bem definida.
- Pelo menos dois testes manuais feitos com Postman ou Insomnia.

### O que serÃ¡ observado

- Uso correto de mÃ³dulos.
- Funcionamento das rotas.
- OrganizaÃ§Ã£o da aplicaÃ§Ã£o.
- Clareza do cÃ³digo.

### Para te ajudar: aulas para rever

Para realizar esta atividade, os seguintes materiais serÃ£o muito Ãºteis:

- **[Aula 01 - IntroduÃ§Ã£o ao Node.js](../Aula01/README.md)**: Para relembrar como executar scripts Node.js.
- **[Aula 02 - MÃ³dulos e NPM](../Aula02/README.md)**: Essencial para aprender a criar e exportar funÃ§Ãµes em um mÃ³dulo e importÃ¡-las em outro.
- **[Aula 03 - Express: Servidores e Rotas](../Aula03/README.md)**: Para criar o servidor e as rotas `GET` e `POST`.
- **[Aula 04 - Middlewares no Express](../Aula04/README.md)**: Para entender o `express.json()`.

## NÃ­vel 2 â€” IntermediÃ¡rio

### Objetivo

Expandir a API simples com mais rotas e introduzir middleware de exemplo. Esse nÃ­vel avalia o uso do Express com mais controle do fluxo da requisiÃ§Ã£o.

### Atividade

Criar uma API de **alunos** ou **produtos** com os seguintes requisitos:

- Tudo do nÃ­vel bÃ¡sico.
- Criar tambÃ©m `PUT /alunos/:id` ou `PUT /produtos/:id` para atualizar um registro.
- Criar tambÃ©m `DELETE /alunos/:id` ou `DELETE /produtos/:id` para remover um registro.
- Implementar um middleware de exemplo apenas com `console.log()` para mostrar que a requisiÃ§Ã£o passou por ele.
- Manter os dados em memÃ³ria.

### O que entregar

- CÃ³digo-fonte organizado em pastas.
- `README.md` com execuÃ§Ã£o e explicaÃ§Ã£o do fluxo.
- EvidÃªncias dos testes realizados.
- Estrutura do projeto coerente com o que foi visto sobre organizaÃ§Ã£o.

### O que serÃ¡ observado

- Rotas `GET`, `POST`, `PUT` e `DELETE` funcionando.
- Middleware executando corretamente.
- OrganizaÃ§Ã£o do cÃ³digo.
- Uso coerente dos status codes.

### Para te ajudar: aulas para rever

Para realizar esta atividade, os seguintes materiais serÃ£o muito Ãºteis:

- **[Aula 03 - Express: Servidores e Rotas](../Aula03/README.md)**: Cobre tudo sobre a criaÃ§Ã£o de rotas com diferentes mÃ©todos HTTP (`GET`, `POST`, `PUT`, `DELETE`).
- **[Aula 04 - Middlewares no Express](../Aula04/README.md)**: Fundamental para entender como criar um middleware de `console.log` e o papel da funÃ§Ã£o `next()`.

## NÃ­vel 3 â€” AvanÃ§ado

### Objetivo

Montar uma API mais completa, com parÃ¢metros, filtro por id, logging mais elaborado e melhor organizaÃ§Ã£o da aplicaÃ§Ã£o. Esse nÃ­vel exige maior domÃ­nio dos conteÃºdos vistos atÃ© a Aula 4.

### Atividade

Criar uma API de **alunos** ou **produtos** com os seguintes requisitos:

- Tudo do nÃ­vel intermediÃ¡rio.
- Criar rota com **filtro por id** usando parÃ¢metro de rota, como `GET /alunos/:id` ou `GET /produtos/:id`.
- Trabalhar passagem de parÃ¢metros por rota e exibir o valor recebido.
- Implementar logging destacando os status codes por cores usando o pacote ou mÃ³dulo `colors`.
- Manter a aplicaÃ§Ã£o organizada em pastas separadas, conforme a capacidade do aluno.

### O que entregar

- CÃ³digo-fonte completo e organizado.
- `README.md` com explicaÃ§Ã£o dos endpoints e de como executar o projeto.
- EvidÃªncias de testes com sucesso e erro.
- Estrutura de pastas clara e coerente com boas prÃ¡ticas.

### O que serÃ¡ observado

- Uso correto de parÃ¢metros de rota.
- Filtro por id funcionando.
- Logger colorido com status codes.
- OrganizaÃ§Ã£o do projeto e clareza na estrutura.

### Para te ajudar: aulas para rever

Para realizar esta atividade, os seguintes materiais serÃ£o muito Ãºteis:

- **[Aula 03 - Express: Servidores e Rotas](../Aula03/README.md)**: Essencial para aprender a ler parÃ¢metros de rota (`req.params`) para o filtro por ID.
- **[Aula 04 - Middlewares no Express](../Aula04/README.md)**: Para aprofundar a criaÃ§Ã£o de middlewares, como o de logging.

## NÃ­vel Jedi â€” Extra desafio

### Objetivo

Desenvolver a versÃ£o mais completa da atividade, reunindo rotas, organizaÃ§Ã£o, parÃ¢metros, logging avanÃ§ado, autenticaÃ§Ã£o bÃ¡sica e documentaÃ§Ã£o da API. Esse nÃ­vel Ã© indicado para alunos que desejam encarar o mÃ¡ximo da proposta.

### Atividade

Criar uma API de **alunos** ou **produtos** com os seguintes requisitos:

- Tudo do nÃ­vel avanÃ§ado.
- Implementar **autenticaÃ§Ã£o bÃ¡sica** em pelo menos uma rota sensÃ­vel, usando um token fixo no header.
- Proteger pelo menos uma rota `POST`, `PUT` ou `DELETE` com middleware de autenticaÃ§Ã£o.
- Retornar `401` quando o token nÃ£o for enviado ou estiver incorreto.
- Documentar no `README.md` o que a API faz, quais rotas existem e como usar cada uma delas.

### O que entregar

- CÃ³digo-fonte completo e organizado.
- `README.md` documentando a API, os endpoints, headers necessÃ¡rios e instruÃ§Ãµes de execuÃ§Ã£o.
- EvidÃªncias de testes de sucesso e erro, inclusive da autenticaÃ§Ã£o.
- Estrutura bem organizada, com separaÃ§Ã£o de responsabilidades sempre que possÃ­vel.

### O que serÃ¡ observado

- Funcionamento da autenticaÃ§Ã£o bÃ¡sica.
- Clareza da documentaÃ§Ã£o no `README.md`.
- OrganizaÃ§Ã£o geral da API.
- AplicaÃ§Ã£o consistente de tudo que foi pedido no nÃ­vel avanÃ§ado.

### Para te ajudar: aulas para rever

Para este desafio, vocÃª combinarÃ¡ o conhecimento de vÃ¡rias aulas:

- **[Aula 03 - Express: Servidores e Rotas](../Aula03/README.md)**: Essencial para a criaÃ§Ã£o de toda a estrutura da API e rotas.
- **[Aula 04 - Middlewares no Express](../Aula04/README.md)**: Fundamental para implementar o middleware de autenticaÃ§Ã£o para proteger as rotas.

## CritÃ©rios gerais de avaliaÃ§Ã£o

- Funcionamento da aplicaÃ§Ã£o.
- Qualidade da organizaÃ§Ã£o do cÃ³digo.
- Uso dos conteÃºdos vistos atÃ© a Aula 4, com extensÃ£o opcional no NÃ­vel Jedi.
- Clareza do `README.md` e da estrutura de envio.
- CorreÃ§Ã£o na criaÃ§Ã£o da branch e da pasta do aluno.

## ObservaÃ§Ã£o final

O aluno deve escolher o nÃ­vel compatÃ­vel com o prÃ³prio momento de aprendizagem. O objetivo Ã© avaliar de forma justa o que foi assimilado atÃ© a Aula 4 e, para quem quiser ir alÃ©m, oferecer o NÃ­vel Jedi como desafio extra.

