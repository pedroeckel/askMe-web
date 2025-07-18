# AskMe Web

Interface web para criar salas de perguntas e respostas em tempo real utilizando inteligência artificial.

## Tecnologias Principais

- **React 19** com **TypeScript**
- **Vite** para bundling e servidor de desenvolvimento
- **Tailwind CSS 4** com componentes do [shadcn/ui](https://ui.shadcn.com/)
- **React Router 7** para roteamento
- **React Query 5** para gerenciamento de requisições e cache
- **React Hook Form** + **zod** para formulários e validações
- **dayjs** para datas

## Estrutura do Projeto

```
src/
├── app.tsx               # Configuração do React Query e rotas
├── main.tsx              # Entrypoint da aplicação
├── index.css             # Estilos globais com Tailwind
├── components/           # Componentes reutilizáveis
│   ├── create-room-form.tsx
│   ├── question-form.tsx
│   ├── question-item.tsx
│   ├── question-list.tsx
│   ├── room-list.tsx
│   └── ui/               # Componentes base (Button, Card, Form, ...)
├── pages/                # Páginas de navegação
│   ├── create-room.tsx   # Tela inicial
│   ├── room.tsx          # Página de perguntas e respostas
│   └── record-room-audio.tsx  # Envio de áudio para a sala
├── http/                 # Hooks de comunicação com a API
│   ├── use-create-room.ts
│   ├── use-create-question.ts
│   ├── use-room-questions.ts
│   ├── use-rooms.ts
│   └── types/            # Tipos de request/response
└── lib/                  # Utilidades
    ├── dayjs.ts
    └── utils.ts
```

A aplicação espera uma API rodando em `http://localhost:3333` com as rotas:
- `POST /rooms` – criação de salas
- `GET /rooms` – listagem de salas
- `POST /rooms/:roomId/questions` – criação de perguntas
- `GET /rooms/:roomId/questions` – listagem de perguntas
- `POST /rooms/:roomId/audio` – envio de áudio gravado

## Como Executar

1. Instale as dependências:
   ```bash
   npm install
   ```
2. Inicie o servidor de desenvolvimento:
   ```bash
   npm run dev
   ```
   O Vite exibirá a URL (geralmente `http://localhost:5173`).
3. Certifique-se de que o backend esteja rodando em `http://localhost:3333`.
4. Acesse a URL indicada para utilizar a aplicação.

Para gerar uma build de produção utilize:
```bash
npm run build
```
O resultado será criado em `dist/`.

## Observações

Durante a build é necessário que o módulo de idioma do **dayjs** esteja disponível. Caso ocorra erro ao importar `dayjs/locale/pt-BR`, verifique se a dependência está instalada corretamente.
