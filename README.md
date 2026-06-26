# Giro — Gestão para Revenda de Seminovos

Documentação do projeto. Estado atual: **protótipo navegável pronto para apresentação**.
Objetivo: validar a ideia com uma **revenda de seminovos parceira (Ubá-MG)** antes de construir o MVP real.
Visão de longo prazo: transformar em **produto SaaS** para revendas de usados do interior (Zona da Mata e região).

> **Status:** aguardando definição da revenda-piloto. Quando topar, seguir para a seção
> [Próximos passos (quando aprovado)](#-próximos-passos-quando-aprovado).

> Produto irmão do **Wallacy Corretor** (CRM para corretor de imóveis). Mesma tese, outra vertical:
> o gargalo nunca é "vender" — é tudo que acontece **em volta** da venda (estoque, custo, follow-up, documentação, números).

---

## 📁 Arquivos do projeto

| Arquivo | Descrição |
|---|---|
| `index.html` | **Protótipo** completo (HTML + Tailwind via CDN + JS puro). Tudo num arquivo, sem build. |
| `calculadora.html` | Calculadora interativa de unit economics (margem, lucro, ponto de equilíbrio). |
| `proposta.html` | Proposta comercial (formatada para A4/impressão → PDF). |
| `README.md` | Este documento. |

**Stack do protótipo:** HTML único + [Tailwind CSS](https://cdn.tailwindcss.com) (CDN) + [Lucide icons](https://unpkg.com/lucide) (CDN) + JavaScript puro. Sem backend, sem instalação. Dados fictícios embutidos no próprio JS.

---

## 🎯 O conceito

Sistema mobile-first para o **lojista de revenda de seminovos**, com foco em resolver os **gargalos reais**:

1. **Estoque que não gira** — carro parado no pátio é dinheiro dormindo e perdendo valor. Não se sabe há quantos dias cada carro está parado.
2. **Custo total invisível** — o lojista sabe quanto pagou, mas esquece funilaria + revisão + documentação + lavagem. A margem "de cabeça" não é a margem real.
3. **Lead esfria** — o cliente que veio no sábado e disse "vou pensar" cai no caderninho/WhatsApp e some. Semana que vem comprou na concorrência.
4. **Avaliação de troca no feeling** — metade das vendas tem troca; errar a avaliação do usado do cliente come a margem ou perde o negócio.
5. **Financiamento espalhado** — simulação em 3 bancos, esperar aprovação, acompanhar pendência. Lento e desorganizado.
6. **Documentação/prazos** — transferência, DUT, gravame, débito de IPVA/multa que aparece depois. Acompanhado tudo de cabeça.
7. **Anúncios espalhados** — mesmo carro cadastrado em OLX, Webmotors, Mercado Livre e Insta. Ao vender, esquece de tirar e cliente liga atrás de carro que já foi.
8. **Sem números** — não sabe o giro do estoque, a margem média, nem qual canal traz cliente que fecha.

**Os 3 diferenciais que vendem:**
- **Margem real e giro na palma da mão** — cada carro mostra custo total (compra + despesas), margem de verdade e dias no pátio, com **alerta de encalhado**.
- **Nenhum lead esfria + match carro ↔ cliente** — quem procurava "hatch automático até R$ 70 mil" é avisado quando o carro entra; funil com alertas.
- **Feito pra revenda de rua** — celular, simples, em PT-BR, na realidade do interior.

---

## 📱 Telas do protótipo (o que já está demonstrado)

Navegação por barra inferior: **Início · Estoque · Funil · Clientes · Envios · Vendas**.

- **Início** — banner de "leads aguardando resposta", KPIs (carros em estoque, dias médio no pátio, vendas no mês, margem prevista), tarefas do dia, **alerta de carro encalhado** (Corolla, 47 dias) e o card de **match automático** (Fernando procura hatch até R$ 70 mil → entrou o Onix que bate 95%).
- **Estoque** — cards de cada carro com foto, modelo/ano/km, preço de venda, **custo total**, **margem em R$ e %**, **dias no pátio** com selo (verde/amarelo/vermelho-encalhado) e selos de publicação (OLX/Webmotors/ML/Insta). Botão **"Ver clientes que procuram isso"**.
- **Funil** — kanban (Novo → Contatado → Test drive → Proposta → Fechado), com origem de cada lead (WhatsApp/OLX/Webmotors/Insta/Indicação).
- **Clientes** — cada cliente com **intenção de compra** (o que procura em chips: tipo, faixa de preço, câmbio) e status. Botão **"Registrar intenção de compra"** → formulário → **tela de confirmação que já mostra o carro que bate (95%)** pronto pra enviar.
- **Envios (WhatsApp)** — **modelo Click-to-WhatsApp**: lista de mensagens prontas (apontamentos). Cada uma abre a prévia + botão **"Abrir conversa no WhatsApp"**. Banner reforça: *"Seu WhatsApp continua no seu celular, nada fica conectado."*
- **Vendas** — checklist da proposta à transferência (proposta → financiamento → vistoria → documentação → entrega), com barra de progresso, **margem realizada** e alerta de pendência (gravame/débito de IPVA).

**Fluxo "uau" para a demo ao vivo:**
Clientes → *Registrar intenção de compra* → *Salvar* → aparece na hora o carro que bate (95%) → *Enviar no WhatsApp*.

---

## ✅ Decisões de produto (já tomadas)

| Tema | Decisão |
|---|---|
| **Cliente-alvo do piloto** | 1 revenda de seminovos, **Ubá-MG** (definir loja parceira). |
| **Identidade** | Nome "Giro", cor azul (brand/indigo), mobile-first. |
| **Dados de exemplo** | Modelos e preços de seminovos do interior (Onix, HB20, Corolla, Strada, Renegade, HR-V, Gol). |
| **WhatsApp (modelo principal)** | **Click-to-WhatsApp**: o sistema prepara a mensagem e abre o app nativo; **não conecta** no número, sem risco de banimento, sem custo por mensagem. |
| **WhatsApp (upgrade futuro)** | Integração completa (API oficial) com histórico no sistema — fica no plano Profissional. |
| **Modelo de negócio** | SaaS por assinatura. Revenda-piloto entra com **uso gratuito por alguns meses** em troca de feedback + virar case. |

### Estratégia de WhatsApp — os 3 caminhos (referência)

1. **API Oficial (Meta/Cloud API)** — oficial e segura, mas o número **sai do app nativo**. Cobra por mensagem iniciada pelo lojista; **responder cliente em até 24h é grátis**.
2. **Número comercial dedicado** — segundo número só pro negócio na API; o WhatsApp pessoal fica intocado. (Recomendado quando a loja quiser integração de verdade.)
3. **Click-to-WhatsApp (escolhido para o MVP)** — não conecta nada; abre o app nativo com a mensagem pronta. Zero risco, zero custo de mensagem, mais barato/rápido de construir. **Trade-off:** o histórico das conversas não sincroniza para dentro do sistema (compensado movendo o card no funil / botão "registrar contato").

---

## 💰 Precificação

### Planos (preço ao cliente final)

| Plano | Preço/mês | Inclui |
|---|---|---|
| **Essencial** | **R$ 197** | Estoque com custo/margem, funil, clientes, match, **Envio no WhatsApp (1 toque / Click-to-WhatsApp)**, agenda. |
| **Profissional** ⭐ | **R$ 347** | Tudo do Essencial + **WhatsApp integrado + histórico** + publicação nos portais (OLX/Webmotors/ML) + relatórios de giro/margem + simulação de financiamento + 500 disparos/mês inclusos. |
| **Loja** | **R$ 597** | Tudo do Profissional + gestão de equipe (metas e comissão por vendedor) + painel consolidado da loja. |

> **Usuário extra: R$ 89/mês cada — em qualquer plano.** Todo plano inclui **1 usuário**. Cada vendedor/conexão adicional custa R$ 89/mês, independente do plano contratado. É a alavanca de receita que cresce junto com a loja: revenda com 4 vendedores no Profissional = R$ 347 + 3 × R$ 89 = **R$ 614/mês**.

Referência de mercado (gestão de revenda): R$ 100–500/mês (Boom Sistemas, AutoConf, Revenda Mais, AutoGestor, Bndv).
Sugestão tática: **1º mês grátis** para cadastrar o estoque real e sentir o giro.

**Argumento de ROI:** a margem numa única venda de seminovo gira **R$ 3 mil a R$ 10 mil**. O Profissional custa R$ 4.164/ano — **meia venda no ano já paga o sistema inteiro**. E o alerta de encalhado, ao destravar **um** carro parado, paga vários meses de uma vez.

### Unit economics (cenário-base na calculadora)

Premissas: R$ 347/mês · 40 assinantes · 150 disparos/cliente · R$ 0,12/disparo · infra R$ 6 · taxa 5% · fixo R$ 800.

| Métrica | Valor aproximado |
|---|---|
| Custo por cliente | ~R$ 43 |
| **Margem por cliente** | **~R$ 304 (≈88%)** |
| Lucro líquido / mês | **~R$ 11,4 mil** |
| Lucro líquido / ano | **~R$ 136 mil** |
| Ponto de equilíbrio | **~3 assinantes** |

> Custo de WhatsApp é pequeno porque responder cliente (em 24h) é grátis; o custo só incide em disparos iniciados pela loja. Dá pra **embutir no plano** com folga e ainda ter espaço para desconto de lançamento (a R$ 197 a margem segue ~80%).

**Quem paga o WhatsApp:** modelo recomendado = você (plataforma) paga a Meta e **embute no plano** com franquia mensal de disparos (ex: 500 inclusos, excedente R$ 0,15). No MVP com Click-to-WhatsApp, esse custo nem existe.

---

## 🚀 Próximos passos (quando aprovado)

Roteiro para sair do protótipo e construir o **MVP funcional de verdade**.

### Stack sugerida
- **Frontend:** evoluir o protótipo para um app web real (React/Next.js ou manter HTML/Tailwind + Alpine para simplicidade). PWA para "instalar" no celular.
- **Backend/Banco:** **Supabase** (Postgres + Auth + Storage + Realtime). Já há plugin/credenciais no ambiente.
- **WhatsApp (MVP):** Click-to-WhatsApp via link `wa.me` / deep link (sem API, sem custo).
- **Hospedagem:** Vercel/Netlify (frontend) + Supabase (dados). Domínio próprio (~R$ 40/ano).

### Modelo de dados inicial (Supabase)
- `veiculos` (modelo, marca, ano, km, placa, preço_venda, status, canais publicados, data_entrada)
- `despesas_veiculo` (veiculo_id, tipo [compra/funilaria/revisão/documentação/lavagem], valor) → base do **custo total** e da **margem real**
- `clientes` (nome, contato, status, origem)
- `intencoes_compra` (cliente_id, tipo, câmbio, marca/modelo desejado, valor_min, valor_max, km_max) → base do **match**
- `leads` / `funil` (cliente_id, veiculo_id, etapa, origem, timestamps)
- `vendas` (veiculo_id, cliente_id, valor, entrada, financiamento, troca_id, margem, etapa, checklist de documentos com prazos)
- `avaliacoes_troca` (cliente_id, veiculo descrito, FIPE, valor avaliado)
- `tarefas` / `follow_ups` (cliente_id, data, tipo, status)
- **Match:** query/trigger que cruza `veiculos` novos com `intencoes_compra` (tipo + faixa de preço + câmbio + km) e gera apontamentos.

### Fases sugeridas do MVP
1. **Fundação** — auth (login da loja), modelo de dados, deploy.
2. **Estoque inteligente** — CRUD de veículos + despesas → **custo total, margem e dias no pátio** com alerta de encalhado. (É o diferencial nº 1; priorizar.)
3. **Clientes + funil + match + Click-to-WhatsApp** — apontamentos automáticos e envio com mensagem pronta.
4. **Agenda & follow-ups** — lembretes (integração Google Calendar opcional).
5. **Vendas** — checklist da proposta à transferência (financiamento, vistoria, documentação) com prazos/alertas.
6. **Painel** — métricas (giro de estoque, margem média, conversão por etapa, origem dos leads).

### Custos recorrentes esperados (operação)
- Supabase/hospedagem: R$ 0–150/mês no começo (escala com uso).
- WhatsApp: **R$ 0** no MVP (Click-to-WhatsApp). Só há custo se migrar para API oficial.
- Domínio: ~R$ 40/ano.

### Caminho de monetização
1. Revenda-piloto como **uso gratuito** → feedback + depoimento/case.
2. Ajustar o produto ao uso real do pátio.
3. Vender o SaaS para outras revendas da região (Ubá + Zona da Mata).
   - Conta de padaria: **40 revendas × R$ 347/mês ≈ R$ 13,9 mil/mês** recorrente.

---

## 🛠️ Como rodar / editar / republicar

**Rodar local:** basta abrir os arquivos `.html` no navegador (duplo clique). Não precisa de servidor.

**Editar:** os arquivos são autocontidos. No `index.html`, os dados fictícios ficam no bloco
`/* ===================== DADOS FICTÍCIOS ===================== */` (arrays `leads`, `clientes`,
`veiculos`, `matchClientes`, `envios`, `agenda`, `vendas`).

**Regerar o PDF da proposta** (precisa do Google Chrome instalado):
```bash
cd ~/Projects/giro-crm
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" \
  --headless --disable-gpu --no-pdf-header-footer \
  --print-to-pdf="Proposta_Giro.pdf" \
  "file://$(pwd)/proposta.html"
```

---

*Documento mantido por Glauco Araújo · glaucoaraujop@gmail.com*
