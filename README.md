# VitaPep Pharma · GHK-Cu

Página do GHK-Cu 100mg. Um botão leva direto ao WhatsApp e outro abre as
informações técnicas do peptídeo.

## Como rodar

Site estático de arquivo único. Abra o `index.html` no navegador, ou sirva a pasta:

```bash
npx serve .
```

## Estrutura

```
index.html            a página (HTML + CSS + JS, sem dependências)
form.html             questionário de 6 perguntas, fora do ar
assets/ghk-vial.webp  foto do frasco
assets/mark-v.png     símbolo da marca
```

O `form.html` é a versão que monta o tratamento com a pessoa e leva ao WhatsApp
com a mensagem escrita. Está fora do ar, guardado caso volte a ser usado. Para
publicá-lo, acesse `/form.html` ou troque os dois arquivos de nome.

## Configuração

No `<script>` no fim do `index.html`:

```js
var WA_NUMBER = "556731980887";                                        // destino
var MSG       = "Oi! Vim pelo site e quero saber mais sobre o GHK-Cu 100mg."; // mensagem pronta
```

Os dois botões verdes e o ícone do topo usam esse mesmo link.

## Dados do produto

Pureza, quantidade, volume e demais especificações ficam no bloco `.specs`
dentro do modal, em HTML direto. A pureza está como **99%+**, que é o declarado
no rótulo da marca. Se houver laudo com o valor exato do lote, troque ali.

## Meta Pixel

Pixel **PEP HARD** (`2090274458589717`) instalado nas duas páginas:

- `PageView` dispara no carregamento, com fallback em `noscript`.
- `Contact` dispara em todo clique de WhatsApp, com o parâmetro `origem`
  dizendo de onde veio (`botao-principal`, `mais-informacoes`, `topo`).

**Contact é o evento de conversão.** É ele que deve ser escolhido como
resultado da campanha no Gerenciador de Anúncios.

Para trocar o pixel, o ID aparece em três pontos de cada arquivo: no `init`,
na URL do `noscript` e no `src` da imagem de fallback.

## Notas

- Mobile-first. Em telas de 393px ou mais a página cabe inteira sem rolar.
- O modal tem cabeçalho fixo e corpo rolando, e vira bottom sheet no celular.
- Nada é enviado a servidor nenhum. Os botões só abrem um link `wa.me`.
