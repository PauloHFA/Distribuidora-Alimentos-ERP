# PENDÊNCIAS — Distribuidora-Alimentos-ERP

Este documento rastreia o status de validação, o backlog técnico e os requisitos de infraestrutura do sistema ERP de gestão operacional para distribuidora de alimentos.

---

## 1. ✅ Escopo Validado e Concluído
- **Arquitetura Full-Stack:** Frontend em React 18, Vite e Tailwind CSS; Backend em Node.js com Fastify e Prisma ORM em estrutura Monorepo.
- **Divisão de Chunks & Code-Splitting (Rollup):** Configurado `manualChunks` no Vite (`vendor-react`, `vendor-charts`, `vendor-query`, `vendor-icons`), reduzindo o bundle principal de 730 kB para 142 kB.
- **Esteira Completa de CI/CD (GitHub Actions):** Workflow `.github/workflows/ci.yml` configurado cobrindo instalação, testes das regras contábeis, compilação do backend e build do frontend.
- **Banco de Dados & Contabilidade:** PostgreSQL 16 com enums, chaves estrangeiras, tipos monetários `NUMERIC(14,2)` e controle de estoque baseado em Livro-Razão (*Stock Ledger*).
- **Testes Automatizados:** 100% de aprovação na suíte de testes unitários do Node.js Native Test Runner (6/6 suítes passando, cobrindo regras críticas RF-14, RF-23, RF-24 e RF-40).
- **Build de Produção:** Frontend e backend compilados com sucesso (`npm run build`).
- **Módulos Principais Implementados:**
  - Dashboard Executivo com KPIs em tempo real e gráficos Recharts.
  - Estoque com Livro-Razão imutável e prevenção contra saldo negativo.
  - Gestão de Vendas com Pipeline Kanban e Alçada Gerencial para descontos > 10%.
  - Módulo Financeiro Contas a Pagar e Contas a Receber.
  - Central de Emissão de Relatórios (DRE Gerencial, Fluxo de Caixa, Curva ABC e Posição de Estoque).
  - Controle de Acesso por Papel (RBAC) com tela HTTP 403.
  - Gestão de Filiais e Negócios.

---

## 2. 📋 Backlog de Engenharia (Próximas Melhorias Opcionais)
- [ ] Adicionar exportação de relatórios em PDF com layout timbrado nativo via servidor.

---

## 3. ⚙️ Infraestrutura e Dependências Externas (Requer Ação do Desenvolvedor)
- **Banco de Dados PostgreSQL:** Inicializar o contêiner Docker via `npm run db:up` e executar migrações/seed (`npm run prisma:migrate` e `npm run prisma:seed`).
- **Variáveis de Ambiente:** Configurar `DATABASE_URL` e `JWT_SECRET` nos arquivos `.env` do backend e frontend.
