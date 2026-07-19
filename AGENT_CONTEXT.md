# Contexto do site

Este repositório contém o site da **Kris**, consultora financeira da **Poupacred** (CNPJ 07.899.160/0001-63, Presidente Prudente – SP), especializada no **Crédito do Trabalhador** — o consignado do Governo Federal para trabalhadores CLT. Publicado via GitHub Pages em `https://krisconsultora.github.io/`.

## Estrutura do repositório

- `index.html` — landing page principal (HTML, CSS e JS em um único arquivo).
- `credito-trabalhador/` — cluster de guias SEO com `index.html` (hub "Central de guias") + 4 artigos:
  - `o-que-e-o-credito-do-trabalhador.html`
  - `quem-pode-contratar-o-credito-do-trabalhador.html`
  - `como-contratar-o-credito-do-trabalhador.html`
  - `o-que-acontece-se-eu-perder-o-emprego.html`
- `noticias/index.html` — agregador de notícias via RSS do Google Notícias (fetch client-side com 2 proxies CORS em cascata + fallback de erro).
- `robots.txt` — libera buscadores e 8 crawlers de IA (GPTBot, Google-Extended, ClaudeBot, PerplexityBot etc.).
- `sitemap.xml` — todas as páginas; o hub tem prioridade 0.9, notícias `changefreq: daily`.
- `llms.txt` — resumo do site para agentes de IA (padrão llmstxt.org).
- `src/img/` — `kris_consultora.webp` (hero, 880px), `.png` original (usado só como og:image), `logo-poupacred.png`, `avatar/*.webp` (160px, avatares do botão flutuante).

## Jornada da landing page

Quatro etapas navegáveis pelo rail fixo no topo (Conhecer → Objetivo → Entender → Contratar), sem bloqueios reais:

1. **Etapa 1 — Hero** (`#fase-01`): foto da Kris com máscara radial (dissolve nas bordas/base), badge "● Online" pulsante no braço (link WhatsApp), título com saudação personalizável, CTAs "Quero entender melhor" / "Já quero contratar". No mobile, a saudação sobrepõe o final da foto (`margin-top` negativo no `.hero-copy`).
2. **Etapa 2 — Objetivo** (`#fase-02`): cards de objetivo com **Simular em primeiro e painel comparativo já aberto** (slider de R$ 1.000 a R$ 100.000, juros do 1º mês por modalidade). Verde é mantido só na barra "Crédito do Trabalhador"/selo "Menor taxa" (semântica de mais barato).
3. **Etapa 3 — Entender** (`#fase-03`): FAQ em grade de cards com ícones vermelhos + faixa-resumo navy + CTAs no card "Onde solicitar?".
4. **Etapa 4 — Contratar** (`#fase-04`): fundo navy com curva cream no topo (`.phase-03::before`), cartão final com selo dourado, CTA "Contratar agora" (link Poupacred/techconsig) e alternativa WhatsApp. Confete de 💵 dispara uma vez ao chegar.

Fecho: seção "Conheça. Entenda. Decida." e rodapé com links (guias, notícias, contratação, WhatsApp, Instagram `@krisdhya.poupacred`) e bloco institucional da matriz Poupacred.

## Identidade visual

- Paleta: cream `#F6F2E9`, navy `#0A2A3D`, **vermelho Poupacred `#D30000`** (`--red`, cor de CTA/acento extraída da logo), dourado `#D6A94B` em detalhes, verde apenas para semântica de "melhor/online".
- Tipografia: Fraunces (títulos; "Kris" em itálico vermelho no h1), Plus Jakarta Sans (texto), IBM Plex Mono (rótulos).
- O subtítulo do hero ("Consultora financeira" + logo) espelha o estilo do título (Fraunces 600 navy).

## Interações e recursos do index.html

- **Saudação por URL**: `?n=Nome` → "Oi Nome, eu sou a Kris." (inserido via `textContent`, primeira letra de cada palavra maiúscula, máx. 40 chars).
- **Barra de progresso de scroll** na base do rail (gradiente vermelho→dourado) com emoji por etapa: 🤔 🚀 💡 🤑, com animação "pop" na troca.
- **Botão flutuante (FAB)** com avatar da Kris que troca por etapa (`FAB_AVATAR`: 2=final, 3=duvida, 4=dinheiro), oculto no hero, fundo gradiente vermelho com anel pulsante e **balão de conversa** por etapa (`FAB_MSG`, some após 5s, clicável) — tudo abre o WhatsApp.
- **WhatsApp centralizado**: constante `WHATSAPP_NUMBER = "5518920012343"` preenche todos os CTAs (`whatsappBtn`…`whatsappBtn6`).
- **Parallax sutil**: foto do hero (12% da velocidade do scroll, via custom property `--px`) e brilho da etapa 4; atualizado no mesmo rAF da barra de progresso.
- Reveals por IntersectionObserver, `prefers-reduced-motion` respeitado em tudo, fallback `<noscript>` deixa todo o conteúdo visível.

## SEO

- Meta tags com keywords em todas as páginas; título/descrição otimizados para "crédito do trabalhador" e variações ("consignado CLT", "desconto em folha").
- JSON-LD: home tem `WebSite` + `Person` (Kris, com Instagram e Organization/CNPJ) + `FAQPage`; guias têm `Article` + `BreadcrumbList` (o de contratação tem `HowTo`); hub tem `CollectionPage` + `ItemList`.
- Cluster hub-and-spoke: hub → artigos, artigos interligados via "Leia também", home linka tudo no rodapé.
- Pendências manuais do dono: cadastrar em Google Search Console e Bing Webmaster Tools após publicar.

## Convenções para agentes

- Ao criar um novo guia: copiar o template visual de um artigo existente em `credito-trabalhador/`, usar slug com a pergunta completa, adicionar ao `sitemap.xml`, ao rodapé da home, ao hub (`credito-trabalhador/index.html`, card + ItemList do JSON-LD) e aos blocos "Leia também" dos demais guias. Atualizar `llms.txt` se relevante.
- Conteúdo factual sempre com fonte (programa oficial/Caixa) e disclaimer de que condições dependem de análise de crédito.
- Nunca inserir conteúdo de URL/feed via `innerHTML` — usar `textContent`/`DOMParser` (padrões já aplicados em `?n=` e nas notícias).
- Imagens novas: converter para WebP no tamanho de exibição (~2x) com `cwebp`.
