# Projeto de Gerenciamento de Livros

Este projeto é uma API para gerenciamento de livros utilizando Node.js, Express, e MongoDB. A API permite listar, buscar, cadastrar, atualizar e deletar livros no banco de dados.

## Pré-requisitos

- Node.js instalado
- MongoDB instalado e rodando
- NPM ou Yarn para gerenciar pacotes

## Instalação

1. Clone o repositório:
    ```sh
    git clone https://github.com/seu-usuario/nome-do-repositorio.git
    ```
2. Navegue até o diretório do projeto:
    ```sh
    cd nome-do-repositorio
    ```
3. Instale as dependências:
    ```sh
    npm install
    ```
    ou
    ```sh
    yarn install
    ```

## Configuração do Banco de Dados

Crie um arquivo `config/dbConnect.js` e configure sua conexão com o MongoDB:

```js
import mongoose from 'mongoose';

const conectaNaDatabase = async () => {
    try {
        await mongoose.connect('mongodb://localhost:27017/nome-do-banco', {
            useNewUrlParser: true,
            useUnifiedTopology: true,
        });
        console.log("Conexao com o banco feita com sucesso!");
    } catch (erro) {
        console.error("Erro de conexão", erro);
    }
};

export default conectaNaDatabase;
```

## Executando a Aplicação

Para iniciar o servidor, execute:

```sh
npm start
```
ou
```sh
yarn start
```

A aplicação estará disponível em `http://localhost:3000`.

## Endpoints

### Listar todos os livros
```http
GET /livros
```

### Buscar livro por ID
```http
GET /livros/:id
```

### Buscar livros por editora
```http
GET /livros/busca?editora=nome-da-editora
```

### Cadastrar novo livro
```http
POST /livros
```
**Body:**
```json
{
    "titulo": "Nome do Livro",
    "autor": "ID do Autor",
    "editora": "Nome da Editora",
    "anoPublicacao": 2021
}
```

### Atualizar livro
```http
PUT /livros/:id
```
**Body:**
```json
{
    "titulo": "Novo Nome do Livro",
    "autor": "ID do Novo Autor",
    "editora": "Novo Nome da Editora",
    "anoPublicacao": 2022
}
```

### Deletar livro
```http
DELETE /livros/:id
```

## Estrutura do Projeto

- `app.js`: Arquivo principal da aplicação. Configura o servidor Express e as rotas.
- `routes/index.js`: Arquivo que importa e configura todas as rotas da aplicação.
- `routes/livrosRoutes.js`: Arquivo que define as rotas relacionadas aos livros.
- `controllers/livroController.js`: Controlador com as funções de CRUD para os livros.
- `models/Livro.js`: Modelo do Mongoose para o documento de livro.
- `models/Autor.js`: Modelo do Mongoose para o documento de autor.

---

Desfrute do projeto!
