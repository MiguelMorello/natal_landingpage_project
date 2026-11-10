# Meu Natal com Jesus: página de vendas

Site estático (HTML + CSS + JS puros). Não precisa de build, de Node nem de instalar nada.

## Estrutura

```
.
├── index.html                  # a página
├── vercel.json                 # configuração da Vercel (cache e segurança)
├── robots.txt
└── assets/
    ├── css/styles.css          # todo o visual
    ├── js/config.js            # >>> AQUI você coloca o link do checkout <<<
    ├── js/main.js              # contagem regressiva, barra fixa e botões
    └── img/
        ├── hero.webp           # imagem do topo da página
        ├── og.jpg              # imagem que aparece ao compartilhar o link (1200x630)
        └── favicon.svg         # ícone da aba
```

## 1. Colocar o link do checkout

Abra `assets/js/config.js` e preencha:

```js
checkoutUrl: "https://seu-checkout.com/abc123",
```

Todos os botões da página passam a usar esse link. Se você anunciar com UTM ou
Pixel, os parâmetros `utm_*` e `fbclid` são repassados ao checkout automaticamente
(para desligar, use `passTrackingParams: false`).

## 2. Testar no computador

Dê dois cliques em `index.html`. Ou, se tiver Node instalado: `npx serve .`

## 3. Subir no GitHub

Pelo terminal:

```bash
git init
git add .
git commit -m "Primeira versão do site"
git branch -M main
git remote add origin https://github.com/SEU-USUARIO/meu-natal-com-jesus.git
git push -u origin main
```

Sem terminal: crie o repositório em github.com/new, clique em **uploading an existing file**
e arraste **o conteúdo** da pasta (o `index.html`, a pasta `assets` e os demais arquivos).

## 4. Publicar na Vercel

1. Entre em vercel.com e faça login com a sua conta do GitHub.
2. **Add New → Project** e escolha o repositório.
3. Em **Framework Preset** deixe **Other**. Não preencha *Build Command* nem *Output Directory*.
4. Clique em **Deploy**. Em cerca de 30 segundos o site estará no ar em `nome.vercel.app`.

A cada `git push`, a Vercel publica a versão nova sozinha.

## 5. Depois do primeiro deploy

- **Imagem de compartilhamento:** em `index.html`, troque `https://seu-site.vercel.app`
  (na linha `og:image`) pelo endereço real do seu site.
- **Domínio próprio:** na Vercel, **Settings → Domains → Add** e siga as instruções de DNS.
- **Pixel da Meta ou Google Analytics:** cole o código fornecido pela plataforma antes de `</head>`
  no `index.html`.

## Onde editar cada coisa

| O que mudar | Onde |
|---|---|
| Link de compra | `assets/js/config.js` |
| Textos, depoimentos, perguntas frequentes | `index.html` |
| Cores e fontes | começo de `assets/css/styles.css` (bloco `:root`) |
| Imagem do topo | troque `assets/img/hero.webp` mantendo o nome |
| Data da contagem regressiva | `assets/js/main.js` (primeiro bloco) |

## Importante

Os 3 depoimentos de `index.html` (seção "O que as famílias estão dizendo") precisam
refletir o que cada pessoa realmente disse e autorizou publicar.
