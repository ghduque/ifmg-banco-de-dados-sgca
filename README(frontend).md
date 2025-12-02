# SGCA Frontend — Sistema de Gestão de Calendário Acadêmico

![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react)
![Next.js](https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=next.js)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript)

Frontend desenvolvido em **React/Next.js** para consumir a API do **SGCA (Sistema de Gestão de Calendário Acadêmico)**, permitindo gerenciar de forma visual anos letivos e calendários.

##  Tabela de Conteúdos

- [🚀 Tecnologias](#-tecnologias)
- [📋 Pré-requisitos](#-pré-requisitos)
- [🔧 Instalação](#-instalação)
- [⚙️ Variáveis de Ambiente](#️-variáveis-de-ambiente)
- [🔗 Integração com o Backend](#-integração-com-o-backend)
- [📁 Estrutura do Projeto](#-estrutura-do-projeto)
- [🧪 Testando o Frontend](#-testando-o-frontend)
- [🚨 Problemas Comuns](#-problemas-comuns)
- [👤 Autor](#-autor)

---

##  Tecnologias

- React  
- Next.js  
- TypeScript  
- Axios  
- CSS/Components do projeto

---

##  Pré-requisitos

- Node.js 18+
- Backend rodando em: `http://localhost:3001`

---

##  Instalação

```bash
git clone <seu-repositório>
cd sgca-frontend
npm install
````

Rodar em desenvolvimento:

```bash
npm run dev
```

Acessar:

```
http://localhost:3000
```

---

##  Variáveis de Ambiente

Crie o arquivo `.env.local`:

```
NEXT_PUBLIC_API_URL=http://localhost:3001/api
```

---

##  Integração com o Backend

Arquivo responsável pelas requisições:

```
/lib/api.ts
```

Exemplo (anos letivos):

```ts
const API_BASE_URL = process.env.NEXT_PUBLIC_API_URL;

export const api = {
  getAnosLetivos: () => axios.get(`${API_BASE_URL}/anos-letivos`),
};
```

Exemplo no componente:

```ts
useEffect(() => {
  api.getAnosLetivos()
     .then(res => setAnosLetivos(res.data))
     .catch(err => console.error(err));
}, []);
```

---

##  Estrutura do Projeto

```
src/
├── app/
│   ├── anos-letivos/
│   └── calendarios/
├── components/
├── lib/
│   └── api.ts
└── styles/
```

---

##  Testando o Frontend

1. Rodar backend:

```bash
npm run dev
```

2. Rodar frontend:

```bash
npm run dev
```

3. Acessar navegador:

```
http://localhost:3000
```

Testes importantes:

* Criar ano letivo
* Editar ano letivo
* Excluir registro
* Conferir requests no DevTools

---

##  Problemas Comuns

### ❌ Frontend sem exibir dados

* Backend pode não estar rodando
* Variável `NEXT_PUBLIC_API_URL` incorreta

### ❌ Erro de CORS

* Ajustar `CORS_ORIGIN` no backend

### ❌ 404 nas rotas

* Confirmar endpoints no backend
* Verificar porta e URL configurada

---

##  Autores

**Gabriel Henrique Silva Duque**


**Rafael Gonçalves Oliveira**
