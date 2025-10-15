# MoodFlix

**Encontre o filme perfeito para a sua vibe do momento. Sem spoilers, sem complicação.**

MoodFlix é um SaaS criado para resolver o problema universal da indecisão ao escolher um filme. Com base no seu humor, o MoodFlix sugere um título, apresenta um resumo de uma única frase, mostra o pôster e informa onde ele está disponível para streaming.

<!-- ![Exemplo de Interface do MoodFlix](https://i.imgur.com/8Q7gYq9.png)
*(Imagem de exemplo. Substitua por um screenshot do seu projeto quando estiver pronto!)* -->


## Funcionalidades

* **Seleção por Humor:** Escolha entre categorias como "Feliz e Otimista", "Nostálgico", "Para Refletir", etc.
* **Resumo em Uma Frase:** Tenha uma ideia clara do enredo sem nenhum spoiler.
* **Pôster e Título:** Visualização rápida e identificação imediata do filme.
* **Onde Assistir:** Logos dos serviços de streaming onde o filme está disponível no Brasil.
* **Nova Sugestão:** Não gostou da primeira? Peça outra sugestão com a mesma vibe com apenas um clique.


## Tecnologias Utilizadas

* **Frontend:**
    * **[React.js](https://reactjs.org/)**
    * **[Tailwind CSS](https://tailwindcss.com/)**

* **Backend:**
    * **[Node.js](https://nodejs.org/)**
    * **[Express.js](https://expressjs.com/)**

* **Banco de Dados:**
    * **[PostgreSQL](https://www.postgresql.org/)**

* **APIs Externas:**
    * [**The Movie Database (TMDb) API**](https://www.themoviedb.org/documentation/api)


## Como Funciona

1.  **Seleção do Usuário:** O usuário clica em um botão de humor na interface React.
2.  **Chamada à API:** O frontend faz uma requisição `GET` para a API Express (ex: `/api/sugestao?humor=nostalgico`).
3.  **Consulta ao Banco de Dados:** O servidor Express consulta o banco de dados PostgreSQL para buscar um filme aleatório que corresponda à categoria de humor solicitada.
4.  **Resposta da API:** A API retorna os dados do filme (ex: `tmdb_id`, `resumo`, `titulo`) para o cliente.
5.  **Enriquecimento de Dados:** O cliente React usa o `tmdb_id` para fazer chamadas à API externa do TMDb, buscando o pôster e os provedores de streaming.
6.  **Exibição:** Os componentes React são atualizados dinamicamente para exibir a sugestão completa ao usuário.


## Como Executar o Projeto

1.  **Clone o repositório:**
    ```bash
    git clone https://github.com/heyguspedrosa/moodflix.git
    cd moodflix
    ```

2.  **Setup do Banco de Dados:**
    * Acesse o PostgreSQL e crie um novo banco de dados (ex: `moodflix_db`).
    * Execute os scripts de migração (ex: `CREATE TABLE...`) para criar as tabelas `humores` e `filmes`.
    * Popule as tabelas com os dados iniciais dos filmes e seus humores correspondentes.

3.  **Configuração do Backend:**
    * Navegue até a pasta do servidor: `cd server`
    * Instale as dependências: `npm install`
    * Crie um arquivo `.env` na raiz da pasta `server` e adicione as variáveis de ambiente:
        ```env
        # Configuração do Banco de Dados
        DB_USER=seu_usuario_postgres
        DB_HOST=localhost
        DB_DATABASE=moodflix_db
        DB_PASSWORD=sua_senha_postgres
        DB_PORT=5432
        ```
    * Inicie o servidor backend:
        ```bash
        npm run dev 
        ```
    O servidor estará rodando em `http://localhost:3001`.

4.  **Configuração do Frontend:**
    * Em outro terminal, navegue até a pasta do cliente: `cd client`
    * Instale as dependências: `npm install`
    * Crie um arquivo `.env` na raiz da pasta `client` para a chave da API do TMDb:
        ```env
        REACT_APP_TMDB_API_KEY="SUA_CHAVE_DE_API_AQUI"
        ```
    * Inicie a aplicação React:
        ```bash
        npm start
        ```
    A aplicação estará disponível em `http://localhost:3000`.



## Estrutura do Projeto

```bash
moodflix/
├── client/                    # Frontend (React + Tailwind)
│   ├── src/
│   │   ├── components/        
│   │   ├── App.js
│   │   └── index.js
│   ├── public/
│   │   └── index.html         
│   ├── package.json
│   └── .env                   
│
├── server/                    # Backend (Node.js + Express + PostgreSQL)
│   ├── index.js               
│   ├── routes/                
│   ├── controllers/           
│   ├── models/                
│   ├── config/                
│   ├── package.json
│   └── .env                   
│
├── database/                  
│   ├── migrations/            
│   └── seeds/                 
│
├── .gitignore                 
└── README.md
``` 

## Próximos Passos e Melhorias

* [ ] Criar um painel de administração para adicionar/editar filmes e categorias.
* [ ] Permitir que usuários se cadastrem e salvem filmes em uma "watchlist".
* [ ] Implementar um sistema de avaliação comunitária para a "frase-resumo".
* [ ] Adicionar mais filtros (gênero, ano de lançamento, diretor).
* [ ] Otimizar as consultas ao banco de dados para sugestões mais personalizadas.


## Autor

* **GitHub:** [@heyguspedrosa](https://github.com/seu-usuario)
* **LinkedIn:** [Gustavo Pedrosa](https://www.linkedin.com/in/guspedrosa/)


## Licença

Este projeto está sob a licença MIT. Veja o arquivo `LICENSE` para mais detalhes.