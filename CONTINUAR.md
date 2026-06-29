# ▶️ Continuar de onde paramos — Giro

> Documento de retomada. Abra este arquivo primeiro quando voltar ao projeto.
> **Atualizado em:** 29/06/2026

---

## 📍 Onde está tudo

- **Pasta local:** `~/Projects/giro-crm`
- **Repositório (GitHub):** https://github.com/glaucoaraujop-sketch/giro-crm
- **Conta GitHub:** `glaucoaraujop-sketch`

### Links publicados (GitHub Pages — já no ar)

| O quê | Link |
|---|---|
| **Protótipo** (app navegável) | https://glaucoaraujop-sketch.github.io/giro-crm/ |
| **Calculadora de lucro** | https://glaucoaraujop-sketch.github.io/giro-crm/calculadora.html |
| **Proposta comercial** (web) | https://glaucoaraujop-sketch.github.io/giro-crm/proposta.html |

> 💡 Se uma página parecer "desatualizada" no navegador, é cache (10 min). Force recarregar: **Cmd+Shift+R** (Chrome/Edge) ou **Cmd+Option+R** (Safari).

---

## ✅ Estado atual: **protótipo completo, publicado e funcionando**

O que já foi feito (igual ao pacote do Wallacy Corretor, agora para **revenda de seminovos**):

- [x] **README.md** — estratégia completa (conceito, gargalos, diferenciais, pricing, unit economics, roadmap MVP).
- [x] **index.html** — protótipo navegável, 6 telas (Início · Estoque · Funil · Clientes · Envios · Vendas), mobile-first, dados fictícios de Ubá-MG.
- [x] **calculadora.html** — unit economics interativo, **já com a receita de usuários extras (R$ 89)**.
- [x] **proposta.html** — proposta comercial de 5 páginas (A4 → PDF).
- [x] **Proposta_Giro.pdf** — PDF pronto para enviar (regenerado com o R$ 89).
- [x] Publicado no **GitHub Pages** + repositório público.
- [x] **Pricing:** usuário extra **R$ 89/mês em qualquer plano** (README + proposta + calculadora).

---

## 💰 Decisões de produto travadas

- **Marca:** Giro · cor azul (indigo) · mobile-first.
- **Alvo:** revenda de seminovos do interior (piloto em Ubá-MG).
- **Planos:** Essencial **R$ 197** · Profissional **R$ 347** ⭐ · Loja **R$ 597**.
- **Usuário extra:** **R$ 89/mês cada**, em qualquer plano (todo plano inclui 1 usuário).
- **WhatsApp:** Click-to-WhatsApp no MVP (sem conectar número, sem custo, sem risco de banimento).
- **Piloto:** revenda parceira entra com uso gratuito por alguns meses → feedback + virar case.
- **Cenário-base de lucro:** ~R$ 200 mil/ano com 40 lojas (assinatura R$ 347 + média de 1,5 usuário extra).

---

## ⏭️ Próximos passos (escolher quando voltar)

Em aberto / ideias na mesa:
1. **Definir a revenda-piloto real** — hoje está com placeholder "Premium Multimarcas". Ao definir, trocar o nome em todos os arquivos e republicar (`git push`).
2. **(Opcional) Refletir o cenário "com usuários extras" na tabela de unit economics do README** — hoje o README mostra o cenário só com assinatura base; a calculadora já tem o cenário completo.
3. **Quando o piloto aprovar:** seguir o roadmap de MVP do `README.md` → seção *"Próximos passos (quando aprovado)"* (stack Supabase + React/Next.js, modelo de dados, 6 fases).

---

## 🛠️ Comandos úteis (copiar e colar)

```bash
# entrar no projeto
cd ~/Projects/giro-crm

# abrir o protótipo no navegador
open index.html

# republicar após editar (vai ao ar em ~1 min)
git add -A && git commit -m "ajustes" && git push

# regerar o PDF da proposta (precisa do Google Chrome)
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" \
  --headless --disable-gpu --no-pdf-header-footer \
  --print-to-pdf="Proposta_Giro.pdf" \
  "file://$(pwd)/proposta.html"
```

> Onde editar os dados fictícios do protótipo: bloco `/* DADOS FICTÍCIOS */` no `index.html`
> (arrays `veiculos`, `leads`, `clientes`, `matchClientes`, `envios`, `agenda`, `vendas`).

---

*Projeto irmão do Wallacy Corretor (CRM de imóveis) em `~/Projects/chave-crm`. Mesma tese, vertical de veículos.*
*Glauco Araújo · glaucoaraujop@gmail.com*
