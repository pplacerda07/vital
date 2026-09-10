# VitaPep Pharma · Formulário de captura GHK-Cu

Formulário de captação de leads para o GHK-Cu 100mg. A pessoa responde seis
perguntas, o resumo do tratamento é montado na tela e ela é levada ao WhatsApp
com a mensagem já escrita.

## Como rodar

É um site estático de arquivo único. Basta abrir o `index.html` no navegador,
ou servir a pasta:

```bash
npx serve .
```

## Estrutura

```
index.html          página inteira (HTML + CSS + JS, sem dependências)
assets/ghk-vial.webp  foto do frasco
assets/mark-v.png     símbolo da marca
```

Fontes vêm do Google Fonts (Poppins + Inter). Sem framework, sem build.

## Configuração

No topo do `<script>` do `index.html`:

```js
var WA_NUMBER = "556731980887";                                   // destino do lead
var OPENING   = "Oie vim pelo forms, e quero usar o ghk cu para"; // abertura da mensagem
```

As perguntas ficam no array `STEPS`, logo abaixo. Cada opção tem um `label`
(o que aparece na tela) e um `msg` (o trecho que entra na mensagem do WhatsApp).
Para adicionar, remover ou reordenar perguntas, basta mexer nesse array: a barra
de progresso, o contador de passos e o resumo final se ajustam sozinhos.

## Notas

- Mobile-first: a navegação e o botão do WhatsApp são fixos no rodapé no celular.
- A aplicação do GHK-Cu é subcutânea, o único formato trabalhado, e isso aparece
  fixo no resumo e na mensagem.
- Nada é enviado a servidor nenhum. O formulário só monta um link `wa.me`.
