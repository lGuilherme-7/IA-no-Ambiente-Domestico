# IA no Ambiente Doméstico — Projeto Web

> **Resumo:** Este projeto apresenta um site informativo e demonstrativo sobre o uso da Inteligência Artificial no ambiente doméstico. O objetivo é exibir um artigo-jornalístico científico adaptado para web, acompanhado por uma imagem 3D de destaque (casa inteligente) e um vídeo demonstrativo (dia → noite) que ilustra automações e medidas de segurança.

---

## Índice

* [Sobre o projeto](#sobre-o-projeto)
* [Funcionalidades principais](#funcionalidades-principais)
* [Tecnologias utilizadas](#tecnologias-utilizadas)
* [Estrutura de arquivos](#estrutura-de-arquivos)
* [Pré-requisitos](#pr%C3%A9-requisitos)
* [Instalação e execução local](#instala%C3%A7%C3%A3o-e-execu%C3%A7%C3%A3o-local)
* [Como inserir a imagem 3D e gerar o vídeo](#como-inserir-a-imagem-3d-e-gerar-o-v%C3%ADdeo)
* [Configuração do iframe do YouTube (autoplay + loop)](#configura%C3%A7%C3%A3o-do-iframe-do-youtube-autoplay--loop)
* [Melhorias visuais e animações recomendadas](#melhorias-visuais-e-anima%C3%A7%C3%B5es-recomendadas)
* [Boas práticas e acessibilidade](#boas-pr%C3%A1ticas-e-acessibilidade)
* [Deploy / Publicação](#deploy--publica%C3%A7%C3%A3o)
* [Contribuição](#contribui%C3%A7%C3%A3o)
* [Licença](#licen%C3%A7a)
* [Contato / Autor](#contato--autor)

---

## Sobre o projeto

Este repositório contém um site estático (HTML + CSS, leve e responsivo) que apresenta um artigo jornalístico-científico sobre a inserção da Inteligência Artificial no ambiente doméstico. O site inclui:

* Página inicial com *hero* contendo imagem 3D da casa inteligente;
* Seções com introdução, benefícios, desafios éticos e conclusões;
* Área dedicada ao vídeo demonstrativo (dia → noite) com autoplay e loop;
* Rodapé com créditos e referências.

O projeto foi pensado como peça de portfólio e pode ser expandido para incluir recursos interativos (gráficos, estatísticas, formulários, etc.).

---

## Funcionalidades principais

* Layout responsivo (desktop / tablet / mobile);
* Paleta principal em azul (`#2F4273`) — transmite seriedade e profissionalismo;
* Espaço reservado para imagem 3D (casa branca com teto preto e dispositivos inteligentes);
* Suporte para vídeo (YouTube embutido via `iframe`) configurado com autoplay, mute e loop;
* Seções com o texto completo do artigo (expandido e adaptado para leitura web);
* Animações leves com AOS (opcional) e efeitos CSS para hover em botões.

---

## Tecnologias utilizadas

* HTML5
* CSS3 (Flexbox / Grid para layout responsivo)
* (Opcional) Biblioteca AOS para animações on-scroll
* (Vídeo) YouTube embed para vídeo demonstrativo

---

## Estrutura de arquivos (sugerida)

```
projeto-ia-ambiente-domestico/
├── index.html
├── estilo
│   ├── media-query.css
│   │   
└───└─── style.css 
│  
├── video
│   ├── motion2Fast_pode_gerar_um_video_onde_a_casa_3d_branca_e_teto_p_0.mp4
│   └── video-casa-ia.mp4
|
|───.gitattributes
|
│───index.html
│────LICENSE
├── README.md
└── video.hmtl
```

---

## Pré-requisitos

* Navegador moderno (Chrome, Firefox, Edge, Safari atualizados)
* Conexão com internet (para carregar o vídeo via YouTube) — opcional se hospedar vídeo localmente
* (Opcional) Conta em serviços de geração de vídeo  (Pika Labs, Runway, Kaiber) caso queira criar o vídeo automatizado

---

## Instalação e execução local

1. Clone o repositório:

```bash
git clone https://github.com/lGuilherme-7/IA-no-Ambiente-Domestico
cd projeto-ia-ambiente-domestico
```

2. Abra `index.html` no seu navegador (duplo clique) — para testes simples.

3. Para servir localmente (recomendado) e evitar problemas de CORS, use um servidor simples:

* Com Python 3:

```bash
python -m http.server 8000
```

Acesse: `http://localhost:8000`.

* Com Node.js (http-server):

```bash
npx http-server . -p 8000
```

---

## Como inserir a imagem 3D e gerar o vídeo

### 1) Inserir imagem 3D estática

* Salve a imagem gerada (por AI ou por modelagem) em `assets/img/casa-inteligente-3d.png`.
* No `index.html`, use:

```html
<img src="assets/img/casa-inteligente-3d.png" alt="Casa inteligente 3D">
```

### 2) Gerar vídeo 10s (dia → noite) — guia rápido usando Pika Labs

Se você quer um vídeo curto (máx. 10s) com transição dia → noite, recomendo usar **Pika Labs** ou **Runway**. Aqui está um passo a passo simples usando o Pika:

1. Acesse: [https://pika.art](https://pika.art) (crie conta se necessário).
2. Use o prompt abaixo (ajuste detalhes se quiser):

```
A 10-second 3D cinematic render of a modern white smart house with a black roof. Daytime first half: show smart blinds opening, sensors, lights turning on automatically, a robot vacuum moving through rooms, and security cameras visible. Transition to nighttime second half: show exterior security lighting, smart locks engaging, live camera indicators, and subtle blue glows from IoT devices. Clean white background, realistic 3D render, cinematic camera pan, soft shadows.
```

3. Configure duration: 10s. Estilo: 3D render / cinematic. Escolha resolução (720p or 1080p recommended).
4. Gere o vídeo e faça download.
5. Hospede no YouTube (privado ou não listado) e use o `iframe` no site ou use o arquivo local em `<video>`.

> **Observação:** Pika e Runway frequentemente têm créditos gratuitos; dependendo da qualidade/uso, pode haver custo.

---

## Configuração do iframe do YouTube (autoplay + loop)

Use o template abaixo, substituindo `SEU_VIDEO_ID` pelo ID do YouTube:

```html
<iframe 
  width="100%" height="500" 
  src="https://www.youtube.com/embed/SEU_VIDEO_ID?autoplay=1&mute=1&loop=1&playlist=SEU_VIDEO_ID&controls=0&modestbranding=1&rel=0" 
  title="Casa Inteligente - Demo" 
  frameborder="0" 
  allow="autoplay; fullscreen; encrypted-media" 
  allowfullscreen>
</iframe>
```

* `mute=1` é necessário para que `autoplay=1` funcione em navegadores modernos.
* `loop=1` exige também `playlist=SEU_VIDEO_ID` para repetir o mesmo vídeo.

---

## Melhorias visuais e animações recomendadas

1. **AOS (Animate On Scroll):** leve, facilita efeitos `fade-up`, `fade-left` quando o usuário rola a página.
2. **Transições CSS:** use `transition` e `transform` em botões e cards para sentir resposta tátil.
3. **Animação do título (typing effect):** adiciona sofisticação sem poluição visual.
4. **Micro-interações:** pequenos efeitos ao passar o mouse em cards, links e botões.
5. **Lazy loading de imagens:** use `loading="lazy"` para acelerar o carregamento.

Exemplo de botão com hover:

```css
button { transition: all 0.25s ease; }
button:hover { transform: translateY(-4px); box-shadow: 0 8px 20px rgba(47,66,115,0.15); }
```

---

## Boas práticas e acessibilidade

* Sempre inclua `alt` nas imagens.
* Garanta contraste suficiente entre texto e fundo (paleta #2F4273 sobre fundo claro funciona bem).
* Use `aria-label` em elementos interativos se necessário.
* Permita controle do autoplay (botão para pausar o vídeo), pois autoplay pode ser incômodo para alguns usuários.

---

## Deploy / Publicação

Algumas opções fáceis para publicar o site:

* **GitHub Pages:** grátis para sites estáticos.
* **Netlify / Vercel:** deploy contínuo com integração Git.
* **Firebase Hosting:** se quiser HTTPS e CDN.

Exemplo rápido com GitHub Pages:

1. Crie repositório no GitHub e envie os arquivos.
2. Vá em *Settings* → *Pages* → selecione a branch `main` e pasta `/`.
3. Acesse seu site em `https://github.com/lGuilherme-7`.

---

## Contribuição

Contribuições são bem-vindas! Algumas ideias:

* Adicionar interatividade (ex.: simulação de consumo energético em tempo real).
* Implementar seção com dados reais (gráficos) e APIs.
* Melhorar o modelo 3D ou substituir por um glTF interativo.

Se quiser contribuir:

1. Fork este repositório
2. Crie uma branch: `git checkout -b minha-melhora`
3. Faça suas alterações e envie um PR com descrição clara.

---

## Licença

Este projeto está licenciado sob a **MIT License** — sinta-se livre para adaptar e usar no seu portfólio.

> Arquivo `LICENSE` contém o texto completo da MIT.

---

## Contato / Autor

**Guilherme Silva** — Autor do projeto

* GitHub: `https://github.com/lGuilherme-7` 
* E-mail: `ronaldguilherme044@gmail.com`

---

Se precisar, posso também:

* Gerar uma **imagem 3D** estática aqui (PNG) para uso no site;
* Preparar o **vídeo** (guia passo a passo com prompts prontos para Pika/Runway);
* Criar o **arquivo ZIP** final com todos os arquivos do site prontos para deploy.

Quer que eu gere a imagem 3D agora ou que eu já crie o ZIP do projeto pronto para deploy?


