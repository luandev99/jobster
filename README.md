# 🧰 Jobster – Plataforma de Serviços Gerais

**Jobster** é uma plataforma web para conectar clientes a prestadores de serviços gerais. Os usuários podem escolher entre duas formas de contratação: **a combinar** (via chat em tempo real) ou **agendamento online**. O sistema é totalmente modular e escalável, utilizando tecnologias modernas como **.NET 9**, **SignalR**, **PostgreSQL**, **Dapper** no backend e **React + TailwindCSS** no frontend.

---

## 🚀 Visão Geral

- Dois tipos de serviços:  
  ✅ **A Combinar** — o cliente inicia um chat com o profissional  
  ✅ **Agendamento** — cliente escolhe data e horário diretamente online  
- Sem pagamentos online por enquanto  
- Foco na conexão, agilidade e usabilidade

---

## 🧰 Tecnologias Utilizadas

### 💻 Frontend

- [React](https://reactjs.org/)
- [Vite](https://vitejs.dev/)
- [TailwindCSS](https://tailwindcss.com/)
- [ShadCN UI](https://ui.shadcn.dev/)
- [React Router](https://reactrouter.com/)
- [SWR](https://swr.vercel.app/pt-BR/) – parcial
- [Axios](https://axios-http.com/)
- [SignalR](https://www.npmjs.com/package/react-signalr)

### ⚙️ Backend

- [.NET 9 (ASP.NET Core)](https://dotnet.microsoft.com/)
- [SignalR (Real-time Chat)](https://learn.microsoft.com/aspnet/core/signalr)
- [Dapper](https://github.com/DapperLib/Dapper)
- [PostgreSQL](https://www.postgresql.org/)
- [Npgsql](https://www.npgsql.org/) – PostgreSQL Driver
- [FluentValidation](https://docs.fluentvalidation.net/)
- JWT Bearer Authentication

---

## 📂 Estrutura de Pastas

### 📦 Frontend (React)

```
jobster-frontend/
├── src/
│   ├── pages/           # Páginas principais
│   ├── components/      # Componentes reutilizáveis
│   ├── features/        # Chat, Agendamentos, Serviços
│   ├── hooks/           # Hooks customizados
│   ├── lib/             # Configs (axios, auth, etc.)
│   └── router/          # Rotas da aplicação
```

### 🧱 Backend (.NET 9)

```
Jobster.Backend/
├── Api/                # Controllers e SignalR Hubs
│   ├── Controllers/
│   ├── Hubs/
├── Application/        # Handlers, DTOs, Validations
├── Domain/             # Entidades e regras de domínio
├── Infrastructure/
│   ├── Data/           # Repositórios Dapper
│   ├── Services/       # Serviços auxiliares
├── Shared/             # Helpers, Interfaces, Result
└── appsettings.json
```

---

## ✅ Funcionalidades

### 📂 Serviços
- Cadastro de serviços por profissionais
- Tipos: `A Combinar` ou `Agendamento`
- Busca por filtros: cidade, tipo, categoria

### 💬 Chat (A Combinar)
- Chat em tempo real com SignalR
- Histórico de mensagens armazenado
- Interface integrada com o serviço

### 📅 Agendamentos
- Interface com calendário e horários
- Status do agendamento: `Pendente`, `Confirmado`, `Cancelado`
- Visão de agenda para profissional e cliente

### 👤 Autenticação e Perfis
- Autenticação com JWT
- Perfis distintos: `Cliente` e `Profissional`
- Áreas separadas para controle de serviços, agendamentos e mensagens

---

## 🗃️ Estrutura do Banco (PostgreSQL)

### Principais Tabelas:

```sql
users(id, name, email, password_hash, role, created_at)

services(id, user_id, title, description, type, created_at)

appointments(id, service_id, client_id, date, status, created_at)

chats(id, service_id, client_id, professional_id, created_at)

messages(id, chat_id, sender_id, content, sent_at)
```

---

## 📌 Regras de Negócio

- Apenas profissionais podem cadastrar serviços
- Um serviço só pode ter um tipo: “a combinar” ou “agendamento”
- Agendamentos não podem ocorrer em datas passadas
- Chat só é permitido em serviços do tipo “a combinar”
- Profissional define horários disponíveis para agendamento

---

## 🔮 Futuras Extensões

- Integração com Stripe ou MercadoPago para pagamentos online
- Avaliações e comentários dos usuários
- Notificações por e-mail e push
- Geolocalização para encontrar profissionais próximos
- Dashboard com insights para os profissionais
