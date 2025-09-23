# PRD – Plataforma de Feedback, Roadmap, Suporte e Help Center (Estilo Featurebase)

## 1. Visão Geral do Produto
Criar uma plataforma SaaS de gestão de feedback, suporte e documentação, inspirada na Featurebase, com design moderno (glassmorphism estilo iOS), UI responsiva e suporte a múltiplos idiomas.  
O objetivo é centralizar:
- Coleta de feedback de usuários (ideias, votos, comentários)
- Roadmap público com status de desenvolvimento
- Base de conhecimento e help center
- Changelog e notificações de novas features
- Caixa de entrada de suporte (tickets)
- Surveys e coleta de insights
- Integrações externas (Slack, Jira, GitHub, etc.)

## 2. Público-alvo
- Empresas SaaS e startups
- Equipes de produto e suporte
- Usuários finais que desejam participar da evolução do produto

## 3. Funcionalidades Principais

### 3.1 Feedback & Roadmap
- Fórum de ideias: criar, votar, comentar
- Detecção de duplicados (IA - usar embeddings + similaridade)
- Roadmap público (planejado, em progresso, lançado)
- Widget de feedback embutível em outras apps/sites

### 3.2 Suporte / Inbox
- Caixa de entrada para tickets
- Respostas internas, menções, macros
- Integração e-mail → ticket
- Notificações em tempo real (WebSocket)

### 3.3 Help Center
- CRUD de artigos de conhecimento (rich text + imagens)
- Busca inteligente
- Multi-idioma
- Domínio customizado + branding (logo, cores)

### 3.4 Changelog
- Página pública de changelog
- Widget in-app para novidades
- Notificação para quem votou em funcionalidades afetadas

### 3.5 Surveys
- Criador de surveys no-code
- Segmentação de usuários (perfil, plano, tags)
- Relatórios de resultados

### 3.6 Integrações
- Slack, Intercom, Jira, GitHub, Hubspot, Linear
- API pública (REST ou GraphQL) para leitura/escrita de feedback, tickets, artigos, changelog

### 3.7 Usuários & Permissões
- Autenticação (NextAuth.js)
- Papéis: Admin, Suporte, Moderador, Usuário
- Convite de membros da equipe
- Controle de acesso granular (RBAC)

### 3.8 Notificações
- E-mail (via Resend ou Postmark)
- In-app (toast, banner, modal)
- WebSocket/Realtime para eventos críticos

### 3.9 Dashboard & Analytics
- Painel para admins com métricas:
  - Ideias mais votadas
  - Volume de tickets e tempo médio de resposta
  - Engajamento dos usuários
  - Participação em surveys

---

## 4. Requisitos Técnicos

### 4.1 Frontend
- **Framework:** Next.js 14 (App Router)
- **UI:** TailwindCSS + HeadlessUI + Framer Motion
- **Design:** Glassmorphism (borda translúcida, blur, sombra suave)
- **State Management:** Zustand ou Context API
- **Visualizações:** React Flow para roadmap interativo e fluxos visuais

### 4.2 Backend
- **ORM:** Prisma
- **Banco:** PostgreSQL (Neon) USE O MCP para criar a base de dados e configurar o prima
- **API:** Next.js API Routes (REST) ou tRPC (se preferir tipagem end-to-end)
- **Autenticação:** NextAuth.js
- **Background Jobs:** Queue (ex.: BullMQ ou QStash)

### 4.3 Infraestrutura
- Deploy no Vercel
- Neon para banco de dados (serverless Postgres)
- CDN para assets estáticos
- Integração com serviços de email e WebSocket (p.ex. Ably ou Pusher)

### 4.4 Segurança
- Proteção CSRF/XSS
- RBAC
- Rate limiting para API
- Logs e auditoria de ações administrativas

---

## 5. Arquitetura & Modelagem de Dados
- **Entidades principais:** Usuário, Empresa, Ideia, Voto, Comentário, Ticket, Artigo, Changelog, Survey, Resposta, Notificação
- **Relacionamentos:**  
  - Usuário pertence a Empresa  
  - Ideia tem muitos Votos e Comentários  
  - Ticket tem histórico de mensagens  
  - Artigo pertence a categoria  
  - Survey tem várias perguntas e respostas

(Definir no Prisma Schema)

---

## 6. Roadmap de Desenvolvimento (Sprints)

### Sprint 1 (MVP)
- Autenticação + Gestão de usuários
- CRUD de ideias + votos + comentários
- Roadmap básico (colunas Kanban)
- Help center simples
- Painel admin básico
- Deploy no Vercel + DB Neon

### Sprint 2
- Inbox de tickets
- Notificações e e-mails
- Branding customizado + domínio próprio
- React Flow para roadmap avançado
- Integração Slack e GitHub

### Sprint 3
- Surveys avançadas com segmentação
- Changelog com widget in-app
- Busca inteligente (vector search)
- Análises e métricas

---

## 7. Critérios de Aceitação
- Interface responsiva e performática
- UX clean, estilo iOS (glass, blur, animações suaves)
- Usuário consegue enviar feedback, votar, ver roadmap e docs sem fricção
- Admin consegue gerenciar tudo via dashboard

---

## 8. Inspirações Visuais
- Featurebase (UI clean)
- Linear.app (minimalismo + glass)
- Notion (tipografia e leveza)
- Vercel Dashboard (dark mode elegante)

---

## 9. Métricas de Sucesso
- % de usuários que interagem com feedback
- Tempo médio de resposta em tickets
- NPS de usuários após implantação
- Engajamento no roadmap (visualizações, votos)

