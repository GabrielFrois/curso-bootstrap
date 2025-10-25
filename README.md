# Curso de Bootstrap

Landing page feita assistindo ao [Curso de Bootstrap](https://www.youtube.com/playlist?list=PLnDvRpP8Bnexu5wvxogy6N49_S5Xk8Cze), de [Matheus Battisti](https://www.youtube.com/@MatheusBattisti)

---

## 1. Estrutura e Framework

O projeto é todo construído sobre o Bootstrap, um framework front-end que agiliza a criação de layouts responsivos.

- **Grid System:** Você usou extensivamente o sistema de grid do Bootstrap (`<div class="row">` e `<div class="col-md-4">`, `<div class="col-12">`, etc.). Este é o conceito central para organizar o conteúdo em colunas que se adaptam automaticamente a diferentes tamanhos de tela (desktop, tablet, mobile).
- **Componentes Nativos:** Você utilizou vários componentes prontos do Bootstrap:
  - **Navbar:** A barra de navegação (`navbar`, `navbar-expand-lg`, `fixed-top`) que se transforma em um menu "hambúrguer" (`navbar-toggler`) em telas menores.
  - **Carousel (Slider):** O slider principal (`#mainSlider`) com indicadores, controles de "anterior/próximo" e legendas (`carousel-caption`).
  - **Cards:** Usados na seção "Nosso time" para exibir os perfis.
  - **Formulários:** Estilização de inputs (`form-control`) nas seções de Newsletter e Contato.
- **Classes Utilitárias:** Você usou classes de ajuda do Bootstrap para economizar CSS, como `img-fluid` (para imagens responsivas), `w-100` (largura 100%), e `d-md-block` (para exibir elementos apenas em dispositivos médios ou maiores).
- **CDN (Content Delivery Network):** O projeto carrega o Bootstrap (CSS e JS), jQuery, Popper.js e Font Awesome a partir de uma CDN, o que otimiza o carregamento para o usuário.

## 2. Estilização e Responsividade

- **Classes Reutilizáveis:** Uso de classes globais para manter a consistência, como `.main-title` (com o sublinhado feito por `::after`) e `.main-btn` (o botão azulado customizado).
- **Efeitos de Hover:** O uso de `transition` e a pseudo-classe `:hover` é visto em vários elementos (botões, links, ícones de serviços) para dar feedback visual ao usuário.
- **Background Images:** Uso de `background-image` para seções, uma técnica que é combinada com o Parallax (visto no JS).
- **Design Responsivo (Media Queries):** Uso de `@media (max-width: ...)` para:
  - Ajustar fontes e espaçamentos.
  - Mudar a altura do slider para `auto`.
  - Ocultar elementos desnecessários no mobile (como a imagem `#company-img`).
  - Reorganizar o grid (ex: fazer os círculos de dados terem `width: 50%` em telas pequenas).

## 3. Interatividade

É utilizado `jQuery` para adicionar dinamismo à página, que seria estática apenas com HTML e CSS.

- **Manipulação do DOM:** Você selecionou elementos (`$()`), adicionou/removeu classes (`.addClass()`, `.removeClass()`), e alterou sua visibilidade (`.fadeIn()`, `.fadeOut()`).
- **Manipulação de Eventos:**
  - `$(document).ready()`: Garante que o script só rode após o HTML estar completamente carregado.
  - `.on('click', ...)`: Usado para criar o **Filtro do Portfólio**. Ao clicar em um botão, o script verifica o `id` do botão, esconde todos os projetos (`.project-box`) e exibe (`.fadeIn()`) apenas aqueles que possuem a classe correspondente (`.dev`, `.dsg`, `.seo`).
  - `$(window).scroll()`: Usado para detectar quando o usuário rola a página.

## 4. Integração de Bibliotecas JS

O projeto vai além do Bootstrap e jQuery, integrando outras bibliotecas para efeitos mais avançados.

- **ProgressBar.js**: Usado na seção "Dados" para criar os quatro **círculos de progresso animados**. É instanciado um novo `ProgressBar.Circle` para cada `div` e define suas opções (cor, duração, etc.).
- **Animação na Rolagem (Scroll Spy)**: O código que usa `$(window).scroll()` é uma forma de "scroll spy". Ele:
  1. Pega a posição da seção "Dados" (`$('#data-area').offset()`).
  2. Verifica se a rolagem do usuário (`$(window).scrollTop()`) ultrapassou um certo ponto.
  3. Dispara a animação dos `ProgressBar.js` (`circleA.animate(1.0)`) apenas quando o usuário vê a seção.
  4. Usa uma variável `stop = 1` para garantir que a animação não dispare múltiplas vezes.
- **Parallax.js:** Esta biblioteca é usada para aplicar o **efeito parallax** (onde a imagem de fundo se move mais devagar que o conteúdo) em duas seções. O `setTimeout` é usado para garantir que as imagens de fundo já tenham sido carregadas antes de aplicar o efeito.
- **Navegação Suave (Smooth Scrolling)**: O código final no seu JS faz com que, ao clicar em um link do `navbar` (ex: "Time"), a página role suavemente até a seção correspondente, em vez de dar um "salto" instantâneo. Isso é feito usando a função `.animate({ scrollTop: ... })` do jQuery.
