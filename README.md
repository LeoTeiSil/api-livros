# 📚 API de Livros

Projeto da disciplina **SW-II (Sistemas Web II)** — API para gerenciamento de livros, construída em quatro etapas: banco de dados, CRUD completo e interface web.

## 🧩 Sobre o projeto

Aplicação para cadastrar, consultar, atualizar e excluir livros, com:

- **Back End**: API REST em FastAPI
- **Banco de dados**: MySQL (via XAMPP / phpMyAdmin)
- **Front End**: HTML, CSS e JavaScript puro, consumindo a API via `fetch`

Cada livro possui os campos:

| Campo | Tipo | Descrição |
| --- | --- | --- |
| `id` | int | Identificador único |
| `titulo` | string | Título do livro |
| `autor` | string | Autor do livro |
| `ano_publicacao` | int | Ano de publicação |
| `disponivel` | bool | Situação de disponibilidade |

## 🛠️ Tecnologias

`Python` · `FastAPI` · `Uvicorn` · `SQLAlchemy` · `PyMySQL` · `MySQL` · `XAMPP` · `phpMyAdmin` · `HTML` · `CSS` · `JavaScript`

## 📂 Estrutura do projeto

```
.
├── app/
│   ├── main.py         # Rotas da API (POST, GET, PUT, DELETE)
│   ├── models.py        # Modelo Livro (SQLAlchemy)
│   ├── schemas.py        # Schemas LivroCriacao e LivroResposta (Pydantic)
│   └── database.py       # Conexão e sessão do banco
├── database/
│   └── biblioteca_db.sql # Estrutura e dados do banco
├── frontend/
│   ├── index.html
│   ├── style.css
│   └── script.js
├── requirements.txt
├── .env                  # Credenciais locais (não versionado)
└── README.md
```

## 🔁 Endpoints da API

| Método | Rota | Corpo | Descrição |
| --- | --- | --- | --- |
| `POST` | `/livros` | `titulo`, `autor`, `ano_publicacao`, `disponivel` | Cadastra um livro |
| `GET` | `/livros` | — | Lista todos os livros |
| `GET` | `/livros/{id_livro}` | — | Consulta um livro pelo id |
| `PUT` | `/livros/{id_livro}` | `titulo`, `autor`, `ano_publicacao`, `disponivel` | Atualiza um livro |
| `DELETE` | `/livros/{id_livro}` | — | Exclui um livro |

## ▶️ Como rodar o projeto

### 1. Clonar o repositório

```bat
git clone <url-do-repositorio>
```

### 2. Criar e ativar o ambiente virtual

```bat
python -m venv .venv
.venv\Scripts\activate.bat
```

### 3. Instalar as dependências

```bat
pip install -r requirements.txt
```

### 4. Configurar o `.env`

Criar um arquivo `.env` na raiz com:

```dotenv
DB_USER=root
DB_PASSWORD=sua_senha
DB_HOST=localhost
DB_PORT=3306
DB_NAME=biblioteca_db
```

### 5. Subir o banco de dados

1. Abrir o painel do XAMPP e iniciar **Apache** e **MySQL**.
2. Acessar `http://localhost/phpmyadmin`.
3. Criar/selecionar o banco `biblioteca_db`.
4. Importar o arquivo `database/biblioteca_db.sql`.

### 6. Rodar a API

```bat
uvicorn app.main:app --reload
```

Documentação interativa (Swagger): `http://127.0.0.1:8000/docs`

### 7. Abrir o Front End

Abrir `frontend/index.html` no navegador (ou usar a extensão Live Server do VS Code).

## 🧱 Padrão de código

Nomes em português para classes, funções e variáveis: `Livro`, `LivroCriacao`, `LivroResposta`, `criar_livro`, `listar_livros`, `atualizar_livro`, `excluir_livro`.

## ✅ Etapas do projeto

- [x] Etapa 1 — Fundação: ambiente, banco `biblioteca_db` e conexão com MySQL
- [x] Etapa 2 — Modelo `Livro`, schemas e rotas `POST`/`GET`
- [x] Etapa 3 — Rotas `PUT`/`DELETE` e CRUD completo
- [ ] Etapa 4 — Front End em HTML, CSS e JavaScript

## 📌 Observações

- O arquivo `.env` **não é versionado** (contém a senha local do MySQL).
- O arquivo `database/biblioteca_db.sql` é versionado para permitir reconstruir o banco entre as aulas.
- O banco é administrado exclusivamente pelo **phpMyAdmin** (não é utilizado o MySQL Workbench).
