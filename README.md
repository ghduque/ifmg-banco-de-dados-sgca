SGCA — Sistema de Gestão de Calendário Acadêmico

![Node](https://img.shields.io/badge/Node.js-18+-339933?style=for-the-badge&logo=node.js&logoColor=white)
![Typescript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)
![IFMG](https://img.shields.io/badge/Instituição-IFMG-green?style=for-the-badge)

Repositório destinado ao **SGCA — Sistema de Gestão de Calendário Acadêmico**, contemplando **backend em Node.js/Express** com **TypeScript** e **frontend em React/Next.js**, integrados ao banco de dados **PostgreSQL**.

O sistema permite gerenciar **anos letivos**, **calendários**, categorias de datas e demais informações acadêmicas exigidas pelo fluxo institucional.

---

##  Tabela de Conteúdos

- [🚀 Tecnologias](#-tecnologias)
- [📁 Estrutura do Backend](#-estrutura-do-backend)
- [🔧 Configuração do Ambiente](#-configuração-do-ambiente)
  - [Configuração do Banco de Dados](#configuração-do-banco-de-dados)
  - [Configuração do Backend](#configuração-do-backend)
  - [Configuração do Frontend](#configuração-do-frontend)
- [🔗 Integração Frontend ↔ Backend](#-integração-frontend--backend)
- [📚 API — Endpoints Implementados](#-api--endpoints-implementados)
- [🧪 Testando o Sistema](#-testando-o-sistema)
- [🚨 Problemas Comuns e Soluções](#-problemas-comuns-e-soluções)
- [📝 Próximos Passos](#-próximos-passos)
- [👤 Autor](#-autor)

---

##  Tecnologias

### **Backend**
- Node.js  
- Express.js  
- TypeScript  
- PostgreSQL  
- pg (driver)  
- CORS  
- Helmet  
- Morgan (logs HTTP)

### **Frontend**
- React  
- Next.js  
- Axios  
- Variáveis de ambiente para integração com a API  

---

##  Estrutura do Backend

```

src/
├── config/          # Configurações gerais e do banco
├── controllers/     # Controladores de rotas
├── middleware/      # Middlewares de segurança e erros
├── models/          # Tipos e modelos em TypeScript
├── routes/          # Definição das rotas da API
├── utils/           # Funções auxiliares
└── index.ts         # Inicialização do servidor

````

---

##  Configuração do Ambiente

###  Configuração do Banco de Dados

Pré-requisitos:
- PostgreSQL instalado
- Acesso administrativo

Passos:

```bash
psql -U postgres
psql -U postgres -f trabalho_2_melhorado.sql

\c sistema_academico_ext
\dt
````

---

###  Configuração do Backend

```bash
cd sgca-backend
npm install
cp .env.example .env
```

Variáveis importantes:

```
PORT=3001
DB_HOST=localhost
DB_NAME=sistema_academico_ext
DB_USER=postgres
DB_PASSWORD=SUA_SENHA
CORS_ORIGIN=http://localhost:3000
```

Rodando o servidor:

```bash
npm run dev        # Desenvolvimento (hot reload)
npm start          # Produção
```

---

###  Configuração do Frontend

```bash
cd sgca-frontend
npm install
```

Criar `.env.local`:

```
NEXT_PUBLIC_API_URL=http://localhost:3001/api
```

Executar:

```bash
npm run dev
```

Acessar pelo navegador:

```
http://localhost:3000
```

---

## 🔗 Integração Frontend ↔ Backend

O frontend se comunica com o backend usando o arquivo:

```
/lib/api.ts
```

O sistema utiliza `NEXT_PUBLIC_API_URL` como base das requisições.

Trecho de exemplo (anos letivos):

```ts
useEffect(() => {
  const fetchData = async () => {
    try {
      const response = await api.getAnosLetivos();
      setAnosLetivos(response.data);
    } catch (error) {
      console.error('Erro ao carregar anos letivos:', error);
    }
  };

  fetchData();
}, []);
```

---

##  API — Endpoints Implementados

###  Health Check

* `GET /api/health`

###  Anos Letivos

* `GET /api/anos-letivos`
* `GET /api/anos-letivos/:id`
* `POST /api/anos-letivos`
* `PUT /api/anos-letivos/:id`
* `DELETE /api/anos-letivos/:id`

###  Calendários

* `GET /api/calendarios`
* `GET /api/calendarios/:id`
* `POST /api/calendarios`
* `PUT /api/calendarios/:id`
* `DELETE /api/calendarios/:id`

---

##  Testando o Sistema

Exemplos rápidos:

```bash
curl http://localhost:3001/api/health
curl http://localhost:3001/api/anos-letivos
```

Criar novo ano letivo:

```bash
curl -X POST http://localhost:3001/api/anos-letivos \
  -H "Content-Type: application/json" \
  -d '{"id_periodo": 2025,"nome_periodo": "Período 2025","data_inicio": "2025-02-01","data_fim": "2025-12-15"}'
```

---

##  Problemas Comuns e Soluções

### ❗ Erro de CORS

* Verificar variável `CORS_ORIGIN`
* Em desenvolvimento: `*` (não recomendado em produção)

### ❗ Backend sem acessar o banco

* Verificar se o PostgreSQL está rodando
* Conferir `.env`
* Testar conexão via `psql`

### ❗ Frontend carregando dados mockados

* Checar `NEXT_PUBLIC_API_URL`
* Confirmar se o backend está rodando na porta correta

---

## 📝 Próximos Passos

### Endpoints a implementar:

* `/api/categorias-datas`
* `/api/datas`
* `/api/equalizacao`
* `/api/eventos-obrigatorios`
* `/api/prazos-eventos`

### Melhorias sugeridas:

* Validação avançada (Joi, Zod)
* Autenticação
* Paginação
* Cache (Redis)
* Logs robustos
* Testes unitários e de integração

---

##  Autores

**Gabriel Henrique Silva Duque**

**Rafael Gonçalves Oliveira**
