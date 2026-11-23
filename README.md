<div align="center">

# Neymar Jr. — O Príncipe

**Portfólio web interativo sobre a trajetória de Neymar Jr., de Santos à Seleção Brasileira.**

![React](https://img.shields.io/badge/React-19-61DAFB?logo=react&logoColor=black)
![Vite](https://img.shields.io/badge/Vite-7-646CFF?logo=vite&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?logo=typescript&logoColor=white)
![Express](https://img.shields.io/badge/Express-4-000000?logo=express&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-4-06B6D4?logo=tailwindcss&logoColor=white)
[![Licença: MIT](https://img.shields.io/badge/licen%C3%A7a-MIT-blue.svg)](./LICENSE)

</div>

---

## 📖 Sobre

O **Neymar Jr. — O Príncipe** é um projeto de portfólio web que reúne, de forma estruturada e navegável, a biografia e a carreira esportiva de Neymar da Silva Santos Júnior. A base de conteúdo fica em um único arquivo Markdown (`data/neymar_data.md`), com informações verificáveis sobre clubes, Seleção Brasileira, títulos, prêmios individuais, patrocínios, estilo de jogo, vida pessoal, linha do tempo e frases marcantes.

A aplicação segue uma arquitetura full-stack: o front-end é uma SPA em **React 19 + Vite**, estilizada com **Tailwind CSS 4** e componentes **shadcn/ui** (base **Radix UI**), com animações via **framer-motion** e gráficos via **Recharts**. Em produção, um servidor **Express** entrega os arquivos estáticos gerados pelo build e trata o roteamento do lado do cliente.

O projeto é destinado a fãs, pesquisadores e curiosos que queiram consultar dados consolidados do atleta em uma interface moderna, além de servir como base reutilizável para portfólios temáticos e experiências web interativas.

## ✨ Funcionalidades

- Aplicação SPA com roteamento no cliente (`wouter`), rotas `Home` e `NotFound`, com rota de fallback para caminhos inexistentes.
- Provedor de tema (`ThemeContext`) com suporte a `light`/`dark` e persistência em `localStorage` quando o modo alternável é habilitado.
- `ErrorBoundary` global que exibe a mensagem de erro e permite recarregar a página.
- `TooltipProvider` e sistema de notificações (`Toaster` via `sonner`) disponíveis em toda a aplicação.
- Biblioteca extensa de componentes de interface (`shadcn/ui`) — botões, diálogos, tabelas, formulários, calendário, carrossel, sidebar, tabs e mais.
- Componente `MapView` para integração com o **Google Maps** (bibliotecas `marker`, `places`, `geocoding`, `geometry`).
- Gráficos e visualizações de dados suportados por **Recharts**.
- Base de dados biográficos em `data/neymar_data.md`: identidade, carreira por clube, Seleção, títulos, prêmios, patrocínios, estilo de jogo, vida pessoal, linha do tempo e frases.
- Servidor **Express** que serve o build de produção e redireciona todas as rotas para `index.html`.
- Plugins de desenvolvimento no Vite: coletor de logs de depuração e proxy de armazenamento.
- Verificação de tipos com `tsc` e formatação de código com **Prettier**.

## 🛠️ Tecnologias

![React](https://img.shields.io/badge/React-19-61DAFB?logo=react&logoColor=black)
![React DOM](https://img.shields.io/badge/React_DOM-19-61DAFB?logo=react&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-5.6-3178C6?logo=typescript&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-7-646CFF?logo=vite&logoColor=white)
![Express](https://img.shields.io/badge/Express-4-000000?logo=express&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-4-06B6D4?logo=tailwindcss&logoColor=white)
![shadcn/ui](https://img.shields.io/badge/shadcn%2Fui-Componentes-000000?logo=shadcnui&logoColor=white)
![Radix UI](https://img.shields.io/badge/Radix_UI-1-161618?logo=radixui&logoColor=white)
![Framer Motion](https://img.shields.io/badge/Framer_Motion-12-0055FF?logo=framer&logoColor=white)
![Recharts](https://img.shields.io/badge/Recharts-2-8884D8?logo=react&logoColor=white)

## 📁 Estrutura do projeto

```
neymar_portfolio/
├── client/
│   ├── public/
│   ├── src/
│   │   ├── components/        # componentes reutilizáveis e ui/ (shadcn/ui)
│   │   ├── contexts/          # ThemeContext (tema claro/escuro)
│   │   ├── hooks/             # hooks utilitários (composição, mobile, persistência)
│   │   ├── lib/               # utilitários (cn)
│   │   ├── pages/             # Home.tsx, NotFound.tsx
│   │   ├── App.tsx            # rotas, providers e layout base
│   │   ├── index.css          # tema e tokens do Tailwind
│   │   └── main.tsx           # ponto de entrada do React
│   └── index.html
├── data/
│   └── neymar_data.md         # base de dados biográficos do atleta
├── server/
│   └── index.ts               # servidor Express (entrega do build e SPA fallback)
├── shared/
│   └── const.ts               # constantes compartilhadas
├── patches/                   # patches de dependências (pnpm)
├── components.json            # configuração do shadcn/ui
├── package.json
├── tsconfig.json
└── vite.config.ts
```

## 🚀 Como rodar localmente

O projeto usa **pnpm** como gerenciador de pacotes.

```bash
# Instalar dependências
pnpm install

# Ambiente de desenvolvimento (Vite, porta 3000 por padrão)
pnpm dev

# Build de produção (cliente + bundle do servidor)
pnpm build

# Executar o servidor Express com o build gerado
pnpm start

# Verificação de tipos
pnpm check

# Formatação de código
pnpm format
```

O servidor de desenvolvimento inicia em `http://localhost:3000/`. Em produção, o servidor Express também usa a porta `3000` por padrão, ou a porta definida em `PORT`.

## 🔐 Variáveis de ambiente

As variáveis abaixo são referenciadas pelo código (cliente e servidor). Crie um arquivo `.env` na raiz do projeto, se necessário — ele está no `.gitignore`.

- `VITE_FRONTEND_FORGE_API_KEY`
- `VITE_FRONTEND_FORGE_API_URL`
- `VITE_OAUTH_PORTAL_URL`
- `VITE_APP_ID`
- `VITE_ANALYTICS_ENDPOINT`
- `VITE_ANALYTICS_WEBSITE_ID`
- `BUILT_IN_FORGE_API_URL`
- `BUILT_IN_FORGE_API_KEY`
- `PORT`

## 📄 Licença

Distribuído sob a **Licença MIT**. Veja [`LICENSE`](./LICENSE).
