<p align="center">
  <img src="public/uzu-logo.png" alt="UzU Dev" width="120" />
</p>

<h1 align="center">Metha Gestão Pública</h1>

<p align="center">
  <strong>Sistema de Gestão de Cursos e Capacitação para Servidores Públicos</strong><br/>
  Documentação técnica desenvolvida por <a href="https://www.uzu.com.br">UzU Dev</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/React-18.3-61DAFB?logo=react" />
  <img src="https://img.shields.io/badge/TypeScript-5.8-3178C6?logo=typescript" />
  <img src="https://img.shields.io/badge/Vite-5.4-646CFF?logo=vite" />
  <img src="https://img.shields.io/badge/Supabase-Backend-3ECF8E?logo=supabase" />
  <img src="https://img.shields.io/badge/Tailwind_CSS-3.4-06B6D4?logo=tailwindcss" />
</p>

---

## 📋 Sobre o Sistema

O **Metha Gestão Pública** é uma plataforma web completa para gestão de cursos e capacitação voltada para servidores públicos do Legislativo e Executivo. O sistema oferece:

- **Gestão de Cursos**: Cadastro, edição e publicação de cursos presenciais
- **Inscrições Online**: Fluxo completo de inscrição com aprovação administrativa
- **Módulo Palestrante**: Cadastro de palestrantes com mini-currículo, bio, Lattes e LinkedIn. Palestrantes têm dashboard próprio para gerenciar cursos e gerar palavras-chave de presença
- **Sistema de Presença por Palavra-Chave**: Palestrante gera uma palavra do dia (com validade configurável), alunos registram presença pelo PWA digitando a palavra. Relatório completo no painel admin
- **Certificados Digitais**: Emissão e validação pública de certificados com QR Code
- **Blog Institucional**: Publicação de artigos sobre gestão pública
- **Área do Aluno (PWA)**: Dashboard pessoal com cursos, certificados, presença e downloads. Instalável no celular como app nativo
- **Painel Administrativo**: Dashboard completo com módulos de gestão
- **Integrações com IA**: Geração de conteúdo com Gemini, OpenAI e Perplexity para blog, sugestões de cursos e análise de licitações
- **Monitor de Licitações**: Radar automático de oportunidades via PNCP com scoring por IA
- **Notificações Automáticas**: Gatilhos configuráveis (pagamento, lembrete, certificado, NF-e, novos cursos, inscrição aprovada) via WhatsApp e Email
- **Automação WhatsApp**: Envio de mensagens via plataforma Uzu Omni com rotação de tokens
- **NFS-e**: Emissão de notas fiscais de serviço eletrônicas
- **Newsletter**: Captura e gestão de assinantes
- **SEO Otimizado**: Meta tags, JSON-LD, sitemap dinâmico
- **PWA (Progressive Web App)**: Aplicação instalável no celular dos alunos com suporte offline

---

## 🛠 Tecnologias Utilizadas

| Tecnologia | Versão | Descrição |
|---|---|---|
| React | 18.3 | Biblioteca de interface |
| TypeScript | 5.8 | Tipagem estática |
| Vite | 5.4 | Build tool e dev server |
| Tailwind CSS | 3.4 | Framework de estilos |
| shadcn/ui | - | Componentes de interface |
| Supabase | 2.x | Backend (Auth, DB, Storage, Edge Functions) |
| Framer Motion | 12.x | Animações |
| React Router | 6.x | Navegação SPA |
| React Query | 5.x | Cache e estado do servidor |
| React Hook Form | 7.x | Formulários |
| Zod | 3.x | Validação de esquemas |
| Recharts | 2.x | Gráficos e dashboards |
| React Helmet | 2.x | SEO e meta tags |

---

## ✅ Pré-requisitos

Antes de começar, você precisa ter instalado:

- **Node.js** v18+ → [Download](https://nodejs.org)
- **npm** v9+ (incluído com Node.js)
- **Git** → [Download](https://git-scm.com)
- Uma conta no **Supabase** (gratuita) → [supabase.com](https://supabase.com)
- Uma conta no **Vercel** (gratuita) → [vercel.com](https://vercel.com) *(para deploy)*

---

## 🗃 Passo a Passo: Criar Conta no Supabase

1. Acesse [supabase.com](https://supabase.com) e clique em **"Start your project"**
2. Faça login com GitHub, Google ou e-mail
3. Clique em **"New Project"**
4. Preencha:
   - **Organization**: Selecione ou crie uma organização
   - **Name**: `metha-gestao-publica`
   - **Database Password**: Crie uma senha forte (guarde-a!)
   - **Region**: `South America (São Paulo)` — escolha a mais próxima
5. Clique em **"Create new project"** e aguarde (~2 minutos)
6. Após criado, vá em **Settings → API** e copie:
   - **Project URL** → será o `VITE_SUPABASE_URL`
   - **anon/public key** → será o `VITE_SUPABASE_PUBLISHABLE_KEY`

---

## 🌐 Passo a Passo: Criar Conta no Vercel

1. Acesse [vercel.com](https://vercel.com) e clique em **"Sign Up"**
2. Faça login com sua conta do **GitHub**
3. Clique em **"Add New..." → "Project"**
4. Selecione o repositório `metha-gestao-publica` da lista
5. Em **"Environment Variables"**, adicione:

| Variável | Valor |
|---|---|
| `VITE_SUPABASE_URL` | URL do projeto Supabase |
| `VITE_SUPABASE_PUBLISHABLE_KEY` | Chave pública (anon key) |

6. Clique em **"Deploy"**
7. Após o deploy, sua aplicação estará disponível em `https://seu-projeto.vercel.app`

### Domínio Personalizado (opcional)

1. No painel do Vercel, vá em **Settings → Domains**
2. Adicione seu domínio (ex: `www.methagestaopublica.com.br`)
3. Configure o DNS no seu provedor conforme instruções do Vercel

---

## 🗃 Configurar o Banco de Dados (Migrations)

### Opção A: Via Supabase Dashboard (recomendado)

1. No painel do Supabase, vá em **SQL Editor**
2. Clique em **"New Query"**
3. Copie e cole o conteúdo do arquivo `supabase/setup.sql`
4. Clique em **"Run"**
5. Repita com o arquivo `supabase/seed.sql`

### Opção B: Via Supabase CLI (desenvolvedores)

```bash
# Instalar Supabase CLI
npm install -g supabase

# Login
supabase login

# Linkar ao projeto
supabase link --project-ref SEU_PROJECT_REF

# Executar migrations
supabase db push
```

### Opção C: Script automatizado

```bash
chmod +x scripts/setup.sh
./scripts/setup.sh
```

---

## 🔐 Primeiro Acesso

### 1. Criar o Usuário Administrador

1. No Supabase Dashboard, vá em **Authentication → Users**
2. Clique em **"Add User" → "Create New User"**
3. Preencha:
   - **Email**: seu e-mail de admin
   - **Password**: uma senha forte
   - **Auto Confirm User**: ✅ marcar
4. Clique em **"Create User"**
5. Copie o **UUID** do usuário criado (coluna "UID")

### 2. Atribuir Role de Admin

No **SQL Editor** do Supabase, execute:

```sql
INSERT INTO public.user_roles (user_id, role)
VALUES ('COLE-O-UUID-AQUI', 'admin');
```

### 3. Acessar o Sistema

1. Acesse a URL do sistema
2. Clique em **"Login"** ou acesse `/login`
3. Use o e-mail e senha cadastrados
4. Acesse o painel admin em `/admin`

### 4. Cadastrar Outros Usuários

Novos usuários se cadastram pelo formulário de inscrição do site. Eles recebem automaticamente o role de `aluno`. Para promover a admin, use o SQL acima.

---

## 🔑 Variáveis de Ambiente

| Variável | Obrigatória | Descrição | Exemplo |
|---|---|---|---|
| `VITE_SUPABASE_URL` | ✅ | URL do projeto Supabase | `https://xxx.supabase.co` |
| `VITE_SUPABASE_PUBLISHABLE_KEY` | ✅ | Chave pública (anon key) | `eyJhbGci...` |

> **Nota**: Chaves de API de terceiros (OpenAI, WhatsApp, etc.) são configuradas via **Supabase Secrets** (Dashboard → Settings → Edge Functions → Secrets) e acessadas apenas nas Edge Functions.

---

## 📁 Estrutura do Projeto

```
metha-gestao-publica/
├── public/                    # Arquivos estáticos
│   ├── favicon.png           # Ícone do site
│   ├── uzu-logo.png          # Logo UzU Dev
│   ├── manifest.json         # PWA manifest
│   └── images/               # Imagens do blog/site
├── scripts/
│   └── setup.sh              # Script de instalação automatizada
├── src/
│   ├── assets/               # Assets importados (logo, etc)
│   ├── components/
│   │   ├── admin/            # Componentes do painel admin
│   │   ├── ajuda/            # Manuais de ajuda (admin e aluno)
│   │   ├── attendance/       # Registro de presença do aluno
│   │   ├── certificates/     # Preview de certificados
│   │   ├── courses/          # Reviews de cursos
│   │   ├── home/             # Seções da homepage
│   │   ├── layout/           # Header, Footer, Layout
│   │   ├── profile/          # Edição de perfil
│   │   ├── ui/               # Componentes shadcn/ui
│   │   ├── UzuDevBadge.tsx   # Badge da UzU Dev
│   │   └── WhatsAppButton.tsx # Botão flutuante WhatsApp
│   ├── hooks/                # Hooks customizados (auth, toast, etc)
│   ├── integrations/
│   │   └── supabase/         # Client e types do Supabase
│   ├── lib/                  # Utilitários
│   ├── pages/                # Páginas da aplicação
│   ├── App.tsx               # Rotas da aplicação
│   ├── main.tsx              # Entry point
│   └── index.css             # Design tokens e estilos globais
├── supabase/
│   ├── config.toml           # Configuração Supabase
│   ├── setup.sql             # Script completo de criação do banco
│   ├── seed.sql              # Dados iniciais
│   ├── migrations/           # Migrations incrementais
│   └── functions/            # Edge Functions (backend)
│       ├── ai-generate/      # Geração de conteúdo com IA
│       ├── create-checkout/  # Checkout de pagamento
│       ├── generate-sitemap/ # Sitemap dinâmico
│       ├── nfse-emit/        # Emissão de NFS-e
│       ├── payment-webhook/  # Webhook de pagamento
│       ├── pncp-search/      # Busca de licitações no PNCP
│       ├── s3-storage/       # Armazenamento S3
│       └── send-whatsapp/    # Envio via WhatsApp
├── .env                      # Variáveis de ambiente (NÃO versionar)
├── package.json
├── tailwind.config.ts
├── vite.config.ts
└── vercel.json               # Configuração de deploy Vercel
```

---

## 🔧 Desenvolvimento Local

```bash
# Clonar o repositório
git clone <URL_DO_REPOSITORIO>
cd metha-gestao-publica

# Instalar dependências
npm install

# Configurar variáveis de ambiente
cp .env.example .env
# Edite o .env com suas credenciais

# Iniciar servidor de desenvolvimento
npm run dev
# Acesse http://localhost:8080

# Build de produção
npm run build

# Executar testes
npm run test
```

---

## 🎤 Módulo Palestrante

O sistema possui um role dedicado para **Palestrantes**, com dashboard próprio (`/palestrante`):

- **Perfil editável**: Bio, especialidades, mini-currículo, LinkedIn e Lattes
- **Cursos vinculados**: Visualização dos cursos em que o palestrante atua
- **Geração de palavras-chave**: O palestrante gera palavras do dia para controle de presença
- O admin cadastra palestrantes pelo painel (aba Cursos → Palestrantes) e os vincula aos cursos

---

## 📋 Sistema de Presença

Controle de presença dos alunos baseado em **palavra-chave**:

1. O palestrante gera uma palavra-chave com validade configurável (15 min a 8h)
2. O palestrante anuncia a palavra em sala
3. O aluno abre o PWA → aba "Presença" → digita a palavra
4. O sistema valida: palavra correta + dentro da janela de tempo + aluno inscrito
5. Admin visualiza relatórios completos por curso (aba Cursos → Presença)

---

## 🔔 Notificações Automáticas

O sistema possui **gatilhos configuráveis** que enviam notificações via WhatsApp e Email:

| Gatilho | Descrição |
|---|---|
| Pagamento Confirmado | Quando o pagamento do aluno é processado |
| Lembrete do Curso | X dias antes do início do curso |
| Certificado Emitido | Quando o certificado é gerado |
| NF-e Emitida | Quando a nota fiscal é emitida |
| Novo Curso Disponível | Quando um novo curso é publicado |
| Inscrição Aprovada | Quando a inscrição é aprovada pelo admin |

Cada gatilho pode ser ativado/desativado independentemente para cada canal (WhatsApp e Email) pelo painel admin (aba Mensageria → Gatilhos).

---

## 🤖 Integrações com IA

O sistema integra múltiplos provedores de IA para geração de conteúdo:

- **OpenAI (GPT-4o)**: Geração de artigos, descrições e conteúdo programático
- **Google Gemini**: Análise de licitações e geração de conteúdo
- **Perplexity (Sonar Pro)**: Pesquisa e análise de tendências

Configuração feita pelo painel admin (aba IA → Configuração IA).

---

## 📱 PWA (Progressive Web App)

O sistema é uma **PWA instalável** no celular dos alunos:

- Instalável via "Adicionar à Tela Inicial" no navegador
- Funciona offline para consulta de dados já carregados
- Experiência nativa no celular (sem barra do navegador)
- Registro de presença rápido pelo celular

---

## 🔄 Manutenção e Atualizações

### Para Desenvolvedores

- **Adicionar novas tabelas**: Crie um novo arquivo em `supabase/migrations/` seguindo o padrão `YYYYMMDDHHMMSS_descricao.sql`
- **Alterar componentes**: Os componentes seguem o padrão shadcn/ui com Tailwind CSS
- **Adicionar páginas**: Crie o componente em `src/pages/` e registre a rota em `src/App.tsx`
- **Edge Functions**: Adicione em `supabase/functions/nome-da-funcao/index.ts`
- **Design tokens**: Todas as cores e estilos estão em `src/index.css` e `tailwind.config.ts`
- **Palestrantes**: Cadastre pelo admin, vincule a cursos e defina o role como `palestrante`

### Boas Práticas

- Sempre use tokens semânticos do design system (nunca cores hardcoded)
- Mantenha RLS ativo em todas as tabelas
- Use `SECURITY DEFINER` em funções que verificam roles
- Teste as Edge Functions localmente com `supabase functions serve`

---

## 📞 Suporte

<p align="center">
  <img src="public/uzu-logo.png" alt="UzU Dev" width="80" />
</p>

<p align="center">
  Este sistema foi desenvolvido por <strong>UzU Dev</strong>.<br/>
  Para suporte, manutenção ou novas funcionalidades, acesse:<br/><br/>
  <a href="https://www.uzu.com.br"><strong>🌐 www.uzu.com.br</strong></a>
</p>

---

<p align="center">
  <sub>© 2025 UzU Dev. Todos os direitos reservados.</sub>
</p>
