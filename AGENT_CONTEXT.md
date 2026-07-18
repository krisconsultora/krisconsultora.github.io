# Contexto do site

Este repositório contém a landing page da consultora financeira **Kris**, especializada em orientar clientes sobre o **Crédito do Trabalhador**.

## Objetivo principal

O site foi desenvolvido como uma experiência de jornada de desbloqueio, com foco em:

- Apresentar a Kris de forma humana, profissional e acolhedora.
- Conduzir o visitante por uma progressão visual: conhecer, entender e contratar.
- Criar um storytelling de scroll que revele fases com animações suaves.
- Oferecer um momento de celebração ao chegar na etapa de contratação.
- Manter a navegação livre, sem bloqueios artificiais.

## Estrutura da jornada

O site é organizado em fases sequenciais:

1. **Fase 01 — Quem sou eu?**
   - Título: "Oi, eu sou a Kris."
   - Subtítulo: "Eu posso ajudar você a entender melhor suas opções de crédito antes de tomar uma decisão."
   - Texto explicativo sobre tornar o crédito mais simples e claro.
   - CTA: "Quero entender melhor" que faz scroll suave para a próxima seção.

2. **Fase 02 — Entenda o Crédito do Trabalhador**
   - Tema: "Agora, vamos entender"
   - Título: "O que é o Crédito do Trabalhador?"
   - Subtítulo: "Antes de contratar, é importante entender como funciona."
   - Bloco de explicação com três etapas: conhecer, tirar dúvidas, decidir.
   - Cards de informação e comparativo de modalidades de crédito.
   - Botão link para página oficial da Caixa sobre Crédito do Trabalhador.

3. **Fase 03 — Contratar**
   - Tema: "Você chegou ao último nível"
   - Título: "Pronto para dar o próximo passo?"
   - Subtítulo: "Se você já entendeu o processo e deseja prosseguir, pode acessar o ambiente de contratação."
   - CTA principal: "Contratar agora" abrindo em nova aba.
   - CTA alternativo: "Entre em contato" via WhatsApp com mensagem pré-preenchida.
   - Mensagem de conclusão da jornada: "Jornada desbloqueada."

## Indicador de progresso

O site tem uma barra fixa no topo que representa a jornada:

- Fase atual destacada.
- Fases futuras com aparência mais discreta.
- Cadeado sutil que desaparece ao desbloquear.
- Animação de confirmação em cada fase.

## Direção visual

A identidade visual segue os seguintes conceitos:

- Moderna, elegante e profissional.
- Humana, confiável e levemente divertida.
- Paleta: azul-marinho / azul-petróleo, branco, verde de ação, dourado em detalhes.
- Grandes títulos, tipografia moderna, cards minimalistas e microinterações.

## Animação e tecnologia

O site é construído como uma única página HTML com CSS e JavaScript embutidos.

Principais elementos técnicos:

- `scroll-behavior: smooth`.
- Observers de interseção para revelar elementos durante o scroll.
- Animações que respeitam `prefers-reduced-motion`.
- Canvas de confete para celebração da fase de contratação.
- Botões de navegação entre fases e links externos.

## Links importantes

- Página oficial Caixa: https://www.caixa.gov.br/voce/credito-financiamento/emprestimo/consignado/credito-do-trabalhador/paginas/default.aspx
- Link de contratação: https://poupacred.techconsig.com.br/privado/autocontratacao?ui=CxiYRMZxpTIwTwnk:TZU8zohdGenmTTW3USOHyw==:rxH6PVA&upi=vJLXPZQP7lVpfDrt:XxQfDJOF19rqaI4X6J-GVQ==:TDSV

## Observações para agentes

- O WhatsApp está configurado com o número real da Kris (`5518920012343`) na constante `WHATSAPP_NUMBER` do `index.html`.
- O site já inclui a animação de confetes, mas ela dispara apenas uma vez por visita.
- Embora exista um bloco de seleção de objetivos de crédito, a narrativa principal permanece focada em conhecer, entender e contratar.
- A página atual usa um fluxo visual que inclui um conteúdo de objetivo e um comparativo de crédito antes de chegar à fase final.

## Como usar

Este arquivo serve como referência para agentes que precisam entender rapidamente o propósito, estrutura e funcionalidades do site.
