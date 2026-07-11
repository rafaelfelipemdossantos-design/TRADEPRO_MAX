# TradePro™ — Calculadora de Performance (SOS / MOP / KBDS)

App web (PWA) para cálculo de share de gôndola (SOS), penetração de checkout (CKO) e metas por categoria (KBDS). Pode ser instalado como aplicativo no celular (Android e iPhone) direto pelo navegador, sem precisar de loja de aplicativos.

## 📁 Estrutura do projeto

```
tradepro-app/
├── index.html          → app principal (React, tudo em um arquivo)
├── manifest.json        → configuração do PWA (nome, ícones, cores)
├── service-worker.js     → permite instalar e funcionar offline
├── icons/                → ícones em todos os tamanhos necessários
└── README.md
```

## 🚀 Como publicar no GitHub Pages (gratuito)

1. Crie um repositório novo no GitHub (ex: `tradepro-app`).
2. Envie **todos os arquivos desta pasta** para a raiz do repositório (mantendo a pasta `icons/` junto).
3. No repositório, vá em **Settings → Pages**.
4. Em "Branch", selecione `main` (ou `master`) e a pasta `/ (root)`. Clique em **Save**.
5. Aguarde 1–2 minutos. Seu app vai ficar disponível em:
   `https://SEU-USUARIO.github.io/tradepro-app/`

> Importante: o GitHub Pages já serve o site via **HTTPS**, o que é obrigatório para o app funcionar como PWA instalável (Service Worker só funciona em HTTPS ou localhost).

## 📲 Como instalar no celular

**Android (Chrome):**
1. Abra o link do app no Chrome.
2. Toque no menu (⋮) → **"Adicionar à tela inicial"** (ou vai aparecer um banner automático de instalação).
3. Pronto — o ícone do TradePro™ aparece na tela inicial como um app normal.

**iPhone (Safari):**
1. Abra o link do app no Safari (tem que ser no Safari, não funciona no Chrome do iPhone).
2. Toque no ícone de compartilhar (o quadrado com a seta para cima).
3. Toque em **"Adicionar à Tela de Início"**.
4. Pronto — abre em tela cheia, sem barra do navegador.

**Desktop (Chrome/Edge):**
1. Abra o link.
2. Clique no ícone de instalação que aparece na barra de endereço (ou menu ⋮ → "Instalar app").

## 🔑 Chave de API (upload com IA)

O botão de "Upload" nas abas SOS e CKO usa a API do Google Gemini para ler a tabela/imagem automaticamente. A chave fica na variável `apiKey` dentro do `index.html`:

```javascript
const apiKey = "SUA_CHAVE_AQUI";
```

Gere uma chave gratuita em: https://aistudio.google.com/apikey

⚠️ **Atenção:** como é um app 100% client-side (sem servidor por trás), essa chave fica visível no código-fonte para quem inspecionar a página. Isso é seguro para uso pessoal, mas **não é recomendado se o link for compartilhado publicamente** — qualquer pessoa poderia copiar a chave e usá-la por conta própria. Se for compartilhar o app, o ideal é criar um pequeno backend/proxy para esconder a chave (posso te ajudar com isso se precisar).

Sem chave configurada, os botões de upload continuam funcionando normalmente através do **modo manual** (preenchimento das metas na mão).

## 🎨 Sobre o ícone

O ícone foi desenhado do zero (gráfico de barras ascendente + linha de tendência) nas cores da identidade do app (azul-marinho, ciano e rosa), já nos formatos exigidos por Android, iOS e desktop, incluindo a versão "maskable" (para os ícones adaptativos do Android).
