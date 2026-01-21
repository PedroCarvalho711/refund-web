Refund Web 

Frontend do sistema **Refund**, responsável por fornecer uma interface web moderna e interativa para gerenciar solicitações de reembolso.

---

📝 Sumário
- [Sobre](#sobre)
- [Funcionalidades](#funcionalidades)
- [Arquitetura do Projeto](#arquitetura-do-projeto)
- [Tecnologias Utilizadas](#tecnologias-utilizadas)
- [Autenticação](#autenticacao)
- [Rotas Principais](#rotas-principais)
- [Paginação](#paginacao)
- [Pré-requisitos](#pre-requisitos)
- [Instalação](#instalacao)
- [Executando o Projeto](#executando-o-projeto)
- [Testes](#testes)
- [Aprendizados](#aprendizados)

---

## Sobre
O **Refund Web** é a camada frontend do sistema de reembolso, consumindo a API **refund-api**. Ele fornece telas para registro e login de usuários, visualização de reembolsos, confirmação, criação e gerenciamento de solicitações.

---

## Funcionalidades
- Tela de **Login** e **Cadastro** de usuários  
- Dashboard com lista de reembolsos  
- Visualização de detalhes de cada reembolso  
- Criação e envio de novas solicitações  
- Upload de arquivos relacionados aos reembolsos  
- Paginação em listas longas de reembolsos  
- Layouts diferentes para autenticação e aplicação principal  
- Feedback visual de carregamento e estados de erro  

---

## Arquitetura do Projeto
refund-web/
├─ public/ # Arquivos estáticos
├─ src/
│ ├─ assets/ # Ícones e imagens
│ ├─ components/ # Componentes reutilizáveis
│ ├─ contexts/ # Contextos React (ex: AuthContext)
│ ├─ dtos/ # Tipagens TypeScript (User, Refund, Category)
│ ├─ hooks/ # Hooks customizados (ex: useAuth)
│ ├─ pages/ # Páginas principais (Dashboard, Refund, SignIn, SignUp)
│ ├─ routes/ # Rotas da aplicação
│ ├─ services/ # Comunicação com API (axios)
│ ├─ utils/ # Funções utilitárias (formatCurrency, categories, classMerge)
│ ├─ App.tsx # Componente raiz
│ ├─ main.tsx # Inicialização da aplicação
│ └─ index.css # Estilos globais
├─ package.json
├─ tsconfig.json
└─ vite.config.ts


- **Layouts:**  
  - `AppLayout.tsx` → Layout principal do dashboard  
  - `AuthLayout.tsx` → Layout para telas de login e cadastro  

---

## Tecnologias Utilizadas
- **React 18 + TypeScript**  
- **Vite** como bundler  
- **Tailwind CSS** para estilização  
- **Axios** para comunicação com backend  
- **React Router** para navegação  
- Context API para gerenciamento de autenticação  
- Tipagem forte com TypeScript (DTOs)  

---

## Autenticação
- Implementada via **AuthContext** e hook `useAuth`.  
- Tela de login (`SignIn.tsx`) e cadastro (`SignUp.tsx`)  
- JWT é armazenado no **localStorage** e enviado no header `Authorization` em requisições à API (`api.ts`).  
- Protege rotas privadas usando componentes de rota customizados (`AuthRoutes.tsx`, `EmployeeRoutes.tsx`, `ManagerRoutes.tsx`).  

---

## Rotas Principais
| Página / Rota           | Componente                | Acesso         |
|-------------------------|--------------------------|----------------|
| `/login`                | `SignIn.tsx`             | Público        |
| `/signup`               | `SignUp.tsx`             | Público        |
| `/dashboard`            | `Dashboard.tsx`          | Usuário logado |
| `/refunds/:id`          | `Refund.tsx`             | Usuário logado |
| `/confirm`              | `Confirm.tsx`            | Usuário logado |
| `*`                     | `NotFound.tsx`           | Todos          |

---

## Paginação
- Componente `Pagination.tsx`  
- Usado para listas de reembolsos no Dashboard  
- Permite navegar entre páginas e definir número de itens por página  
- Integração com backend via query params (`?page=1&limit=10`)  

---

## Pré-requisitos
- Node.js ≥ 18  
- npm ou yarn  
- API backend (`refund-api`) rodando e acessível  

---

## Instalação
1. Clone o repositório:

bash
git clone https://github.com/PedroCarvalho711/refund-web.git
cd refund-web 

2.Instale as dependências:

npm install
# ou
yarn install


3.Crie um arquivo .env com a URL da API:

VITE_API_URL=http://localhost:3000

Executando o Projeto
npm run dev
# ou
yarn dev


Acesse http://localhost:5173 no navegador.

Testes
Componente de teste e hooks podem ser testados usando Jest + React Testing Library (caso já configurados):
npm run test
# ou
yarn test

Aprendizados

Estruturação de projeto frontend modular com React + TypeScript
Uso de Context API para gerenciamento de autenticação
Criação de componentes reutilizáveis (Button, Input, Pagination, Upload)
Integração frontend ↔ backend via Axios
Implementação de paginação e tratamento de listas grandes
Boas práticas de tipagem e DTOs para comunicação com API

GitHub: PedroCarvalho711






