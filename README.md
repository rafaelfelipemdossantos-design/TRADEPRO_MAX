# TradePro Performance

Painel avançado de cálculo de performance (CKO, SOS, MOP e KBDS), pronto para publicar no GitHub Pages e instalar como app no celular.

## Estrutura dos arquivos

```
├── index.html              # Página de acesso
├── app.html                 # A calculadora (app principal)
├── manifest.json            # Configuração do PWA (instalação no celular)
├── service-worker.js        # Permite abrir o app offline
├── icons/
│   ├── icon-192.png
│   ├── icon-512.png
│   ├── icon-maskable-192.png
│   ├── icon-maskable-512.png
│   ├── apple-touch-icon.png
│   ├── apple-touch-icon-152.png
│   ├── apple-touch-icon-120.png
│   ├── favicon.ico
│   └── logo.png
└── README.md
```

## Como publicar no GitHub Pages

1. Crie um repositório novo no GitHub (ex: `TRADEPRO`).
2. Envie **todos** os arquivos desta pasta para a raiz do repositório — **incluindo a pasta `icons/` inteira**, com todos os arquivos dentro dela.
   - No site do GitHub, use **Add file → Upload files** e arraste a pasta `icons` (não os arquivos de dentro dela um por um) — assim o GitHub preserva a estrutura de pastas.
   - Se preferir, use o GitHub Desktop ou `git push`, que preservam pastas automaticamente.
3. No repositório, vá em **Settings → Pages**.
4. Em **Branch**, selecione `main` (ou `master`) e a pasta `/ (root)`. Clique em **Save**.
5. Aguarde alguns minutos. O GitHub vai gerar um link parecido com:
   `https://SEU_USUARIO.github.io/NOME_DO_REPOSITORIO/`
6. Esse link abre automaticamente o `index.html`.

> Se você já tem o repositório `ACESSO_TRADEPRO` publicado, basta substituir os arquivos antigos por estes (o `manifest.json`, o `service-worker.js` e a pasta `icons/` são novos).

## Solução de problemas

**O logo não aparece na tela de acesso:**
Já corrigido nesta versão — o logo agora fica embutido diretamente dentro do `index.html` e do `app.html` (não depende mais de a pasta `icons/` estar no ar). Mesmo que você não suba a pasta `icons/`, o logo aparece normalmente.

**O app não aparece pra instalar no celular:**
Duas causas comuns, já corrigidas nesta versão:
1. Os ícones do `manifest.json` agora também estão embutidos (data URI), então não dependem mais da pasta `icons/` estar publicada corretamente.
2. O `service-worker.js` antes falhava por completo se um único arquivo da pasta `icons/` desse erro 404 — agora ele ignora arquivos ausentes e continua funcionando normalmente.

Se mesmo assim não aparecer a opção de instalar:
- Confirme que está acessando pelo **Chrome** (Android) ou **Safari** (iPhone) — outros navegadores/apps (Instagram, WhatsApp) não permitem instalar.
- No Android, se não aparecer o banner automático, toque nos `⋮` (menu do Chrome) → **Adicionar à tela inicial** / **Instalar app**.
- No iPhone, a instalação é sempre manual: Compartilhar → **Adicionar à Tela de Início** (não existe banner automático no iOS).
- Espere alguns minutos após publicar — o GitHub Pages às vezes demora para atualizar o cache.
- Abra `SEU_LINK/manifest.json` direto no navegador: se der erro 404, o arquivo não foi publicado na raiz do site.

## Como instalar no celular

**Android (Chrome):**
1. Abra o link do GitHub Pages no Chrome.
2. Toque em **Abrir calculadora**.
3. Vai aparecer um banner "Instalar o TradePro no seu celular" — toque em **Instalar**.
   - Se não aparecer automaticamente, toque nos `⋮` (menu do Chrome) → **Adicionar à tela inicial** / **Instalar app**.

**iPhone/iPad (Safari):**
1. Abra o link no Safari (precisa ser no Safari, não funciona pelo app do Instagram/WhatsApp).
2. Toque no ícone de **Compartilhar** (quadrado com seta para cima).
3. Toque em **Adicionar à Tela de Início**.
4. O ícone do TradePro vai aparecer na tela do celular, igual a um app nativo.

Depois de instalado, o ícone abre direto no painel da calculadora, em tela cheia, sem a barra do navegador.

## Sobre o ícone

O ícone foi desenhado especialmente para a ferramenta: barras ascendentes (indicadores de performance) sobre uma régua com marcações — referência direta ao cálculo de espaço em centímetros/ganchos que o app faz. As cores seguem a identidade já usada no app (fundo azul-marinho `#0a0e17`, destaque ciano `#22d3ee`).

## Atualizando o conteúdo

Toda a lógica de cálculo (marcas, metas KBDS, fórmulas) está dentro de `app.html`, dentro da tag `<script type="text/babel">`. Para editar metas ou marcas, procure pelas constantes `GENERAL_BRANDS`, `CKO_BRANDS` e `KBDS_TARGETS` no início do script.
