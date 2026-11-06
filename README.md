# HQ Digital Interativa — Comunicação Visual 2

Projeto desenvolvido para a disciplina de **Comunicação Visual 2**, do curso de **Sistemas e Mídias Digitais**.

## 📖 Sobre o projeto

O projeto é uma **história em quadrinhos (HQ) digital e interativa**, construída inteiramente em HTML, CSS e JavaScript puros. A narrativa é apresentada em painéis sequenciais que contam a história de um reencontro e do distanciamento entre duas pessoas, misturando texto, ilustração e **minigames embutidos diretamente nos quadrinhos**, que funcionam como metáforas visuais para os sentimentos da narrativa:

- **Labirintos navegáveis** — o leitor arrasta um personagem por um caminho cuja colisão é calculada a partir dos próprios pixels da arte do quadrinho (sem máscaras externas).
- **Ampulheta de areia e de sangue** — uma simulação de partículas com física simples (gravidade, colisão entre grãos e escoamento) representando a passagem do tempo.
- **Desafio dos dentes** — um quadrinho com "mandíbulas" que se fecham progressivamente, exigindo que o leitor escape antes de ser "esmagado".
- **Labirinto escuro** — um ambiente quase totalmente breu, no qual o jogador precisa clicar em lâmpadas para iluminar temporariamente o caminho.

Dependendo de como o leitor interage com esses desafios (acerto ou erro), a história pode seguir para um **final verdadeiro** (`trueending`) ou ser redirecionada para um **final falso** (`fakeending.html`), reforçando a ideia de tentativa, erro e reconciliação que permeia o roteiro.

A experiência também conta com **trilha sonora própria**, dividida em duas partes que fazem *crossfade* suave conforme o leitor avança pelos quadrinhos, além de um botão para ativar/desativar o áudio.

## ✨ Principais funcionalidades

- Navegação entre quadrinhos por setas na tela, teclado (`←`/`→`) ou toque.
- Textos animados e posicionados de forma responsiva sobre cada quadrinho.
- Colisão de labirinto calculada em tempo real a partir da imagem (leitura de pixels via `<canvas>`).
- Simulação de partículas (areia e sangue) com gravidade e colisão.
- Desafio dinâmico de "dentes" renderizado via canvas com padrão pixelado.
- Labirinto escuro com sistema de iluminação por lâmpadas clicáveis.
- Trilha sonora com *crossfade* automático entre capítulos e controle de mudo.
- Filtro de cor via SVG (`feColorMatrix`) aplicado a quadrinhos específicos.
- Layout responsivo que mantém a proporção original da arte (720×500) em qualquer tela.
- Final alternativo (`fakeending.html`) que retorna o leitor ao início da HQ.

## 🛠️ Tecnologias utilizadas

- **HTML5**
- **CSS3** (`@font-face` com fonte customizada, *container queries*, filtros SVG, `aspect-ratio`)
- **JavaScript puro** (Canvas API, Pointer Events, `ResizeObserver`), sem frameworks ou bibliotecas externas

## 📋 Requisitos para rodar

- Um navegador moderno e atualizado (Google Chrome, Microsoft Edge ou Firefox), com suporte a Canvas, Pointer Events, filtros SVG e *container queries* de CSS.
- JavaScript habilitado no navegador.
- Um **servidor local** para servir os arquivos (recomendado — veja o motivo abaixo). Qualquer um serve:
  - Extensão **Live Server** do VS Code, **ou**
  - **Python** (geralmente já vem instalado), **ou**
  - **Node.js**, caso prefira usar um pacote como `http-server`.
- Manter a pasta `assets/` (imagens dos quadrinhos, fontes e trilhas sonoras) junto dos arquivos `index.html`, `style.css` e `script.js`, pois o projeto depende desses caminhos relativos.

> ⚠️ **Por que usar um servidor local em vez de abrir o `index.html` direto no navegador?**
> O jogo lê os pixels da própria imagem do quadrinho (via `canvas.getImageData`) para calcular as paredes do labirinto. Alguns navegadores bloqueiam essa leitura de pixels por segurança quando a página é aberta diretamente do disco (protocolo `file://`). Servindo os arquivos por `http://localhost`, esse bloqueio não ocorre.

## ▶️ Como rodar

1. Clone o repositório:
   ```bash
   git clone https://github.com/YuriCardosoSMD/trabalhocomunicacaovisual2.git
   ```
2. Entre na pasta do projeto:
   ```bash
   cd trabalhocomunicacaovisual2
   ```
3. Inicie um servidor local. Escolha uma das opções:
   - **Com Python 3:**
     ```bash
     python -m http.server 8000
     ```
     Depois acesse `http://localhost:8000` no navegador.
   - **Com Node.js:**
     ```bash
     npx http-server -p 8000
     ```
     Depois acesse `http://localhost:8000` no navegador.
   - **Com VS Code:** clique com o botão direito em `index.html` e selecione **"Open with Live Server"**.
4. Navegue pela HQ usando as setas da tela, o teclado (`←`/`→`) ou toque na tela (em dispositivos móveis).
5. Nos quadrinhos com desafio, clique e arraste o pequeno ícone do personagem para guiá-lo pelo caminho seguro. No labirinto escuro, clique nas lâmpadas para iluminar o trajeto.

## 📁 Estrutura do projeto

```
trabalhocomunicacaovisual2/
├── index.html        # Página principal com a HQ interativa
├── style.css          # Estilos, responsividade e animações
├── script.js          # Lógica da HQ, minigames, física de partículas e áudio
├── fakeending.html     # Tela de final alternativo/falso
├── assets/             # Imagens dos quadrinhos, fontes e trilhas sonoras
└── README.md
```
