


# SGCA Backend — Sistema de Gestão de Calendário Acadêmico

![Node](https://img.shields.io/badge/Node.js-18+-339933?style=for-the-badge&logo=node.js&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript)
![Express](https://img.shields.io/badge/Express.js-000000?style=for-the-badge&logo=express)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql)

Backend desenvolvido em **Node.js**, **Express** e **TypeScript** para o **SGCA — Sistema de Gestão de Calendário Acadêmico**, realizando o gerenciamento de anos letivos, calendários e demais estruturas acadêmicas.

---

## 📑 Tabela de Conteúdos
- [🚀 Tecnologias](#-tecnologias)
- [📋 Pré-requisitos](#-pré-requisitos)
- [🔧 Instalação](#-instalação)
- [⚙️ Variáveis de Ambiente](#️-variáveis-de-ambiente)
- [📁 Estrutura do Projeto](#-estrutura-do-projeto)
- [📚 API - Endpoints](#-api---endpoints)
- [🧪 Testando a API](#-testando-a-api)
- [🚨 Troubleshooting](#-troubleshooting)
- [👤 Autores](#-autores)

---

##  Tecnologias

- Node.js  
- Express.js  
- TypeScript  
- PostgreSQL  
- pg (driver)  
- Helmet (segurança)  
- CORS  
- Morgan (logs)

---

##  Pré-requisitos

- Node.js **18+**
- PostgreSQL **12+**
- npm ou yarn

---

##  Instalação

```bash
git clone <seu-repositório>
cd sgca-backend
npm install

# Compilar TypeScript
npm run build

# Rodar em modo desenvolvimento
npm run dev

# Rodar em modo produção
npm start
````

---

##  Variáveis de Ambiente

Crie um arquivo **.env** na raiz do projeto:

```
PORT=3001
NODE_ENV=development

DB_HOST=localhost
DB_PORT=5432
DB_NAME=sistema_academico_ext
DB_USER=postgres
DB_PASSWORD=SUA_SENHA

CORS_ORIGIN=http://localhost:3000
```

---

##  Estrutura do Projeto

```
src/
├── config/
├── controllers/
├── middleware/
├── models/
├── routes/
├── utils/
└── index.ts
```

---

##  API — Endpoints

###  Health Check

```
GET /api/health
```

---

###  Anos Letivos

| Método | Rota                  | Descrição    |
| ------ | --------------------- | ------------ |
| GET    | /api/anos-letivos     | Lista todos  |
| GET    | /api/anos-letivos/:id | Busca por ID |
| POST   | /api/anos-letivos     | Cria         |
| PUT    | /api/anos-letivos/:id | Atualiza     |
| DELETE | /api/anos-letivos/:id | Remove       |

---

###  Calendários

| Método | Rota                 | Descrição    |
| ------ | -------------------- | ------------ |
| GET    | /api/calendarios     | Lista todos  |
| GET    | /api/calendarios/:id | Busca por ID |
| POST   | /api/calendarios     | Cria         |
| PUT    | /api/calendarios/:id | Atualiza     |
| DELETE | /api/calendarios/:id | Remove       |

---

##  Testando a API

### Testar servidor

```bash
curl http://localhost:3001/api/health
```

### Listar anos letivos

```bash
curl http://localhost:3001/api/anos-letivos
```

### Criar ano letivo

```bash
curl -X POST http://localhost:3001/api/anos-letivos \
  -H "Content-Type: application/json" \
  -d '{"id_periodo":2025,"nome_periodo":"2025","data_inicio":"2025-02-01","data_fim":"2025-12-15"}'
```

---

##  Troubleshooting

### ❌ Erro de CORS

* Verifique a variável `CORS_ORIGIN` no `.env`.

### ❌ Backend não conecta ao PostgreSQL

* Confirme que o banco está rodando.
* Teste manualmente:

```bash
psql -U postgres -d sistema_academico_ext
```

### ❌ Porta já está em uso

* Altere `PORT` no `.env`, **ou** mate o processo na porta.

---

##  Autores

* **Gabriel Henrique Silva Duque**
* **Rafael Gonçalves Oliveira**




