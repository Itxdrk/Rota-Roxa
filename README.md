
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Rota Roxa – Apoio contra Vícios</title>
  <meta name="viewport" content="width=device-width,initial-scale=1.0">
  <style>
    *{margin:0;padding:0;box-sizing:border-box;}
    :root{
      --bg-main:#050307;
      --bg-card:#151020;
      --bg-card-soft:#1d162e;
      --accent:#8b5cf6;
      --accent-soft:#a855f7;
      --accent-muted:#6d28d9;
      --text-main:#f9f5ff;
      --text-soft:#c4b5fd;
      --border-soft:rgba(148,120,255,0.35);
    }
    body{
      font-family:system-ui,-apple-system,BlinkMacSystemFont,"Segoe UI",sans-serif;
      background:radial-gradient(circle at top,#2c1363 0,var(--bg-main) 60%);
      color:var(--text-main);
      min-height:100vh;
      display:flex;
      justify-content:center;
      align-items:center;
      padding:12px;
    }
    #app{
      width:100%;
      max-width:1080px;
      min-height:620px;
      background:rgba(5,3,15,0.96);
      border-radius:18px;
      border:1px solid var(--border-soft);
      box-shadow:0 24px 50px rgba(0,0,0,.8);
      display:flex;
      overflow:hidden;
    }
    /* Lateral */
    aside{
      width:240px;
      background:linear-gradient(180deg,#11071f,#06030a);
      border-right:1px solid var(--border-soft);
      padding:18px 14px;
      display:flex;
      flex-direction:column;
      gap:12px;
    }
    .logo{
      display:flex;
      flex-direction:column;
      gap:2px;
    }
    .logo-main{
      font-size:20px;
      font-weight:700;
      color:var(--text-main);
      letter-spacing:.02em;
    }
    .logo-main span{
      color:var(--accent-soft);
    }
    .logo-sub{
      font-size:12px;
      color:var(--text-soft);
    }
    .nav-title{
      margin-top:10px;
      font-size:11px;
      text-transform:uppercase;
      letter-spacing:.12em;
      color:#7c6fd0;
    }
    .nav-item{
      margin-top:6px;
      padding:8px 10px;
      border-radius:10px;
      font-size:14px;
      color:var(--text-soft);
      display:flex;
      align-items:center;
      gap:8px;
      cursor:pointer;
      transition:background .15s,transform .08s;
    }
    .nav-item span.emoji{
      font-size:17px;
    }
    .nav-item.active{
      background:linear-gradient(90deg,var(--accent),var(--accent-soft));
      color:#0b0617;
      font-weight:600;
    }
    .nav-item:not(.active):hover{
      background:rgba(148,120,255,0.16);
      transform:translateY(-1px);
    }
    .disclaimer{
      margin-top:auto;
      font-size:10px;
      line-height:1.4;
      color:#9a8ff0;
    }
    .disclaimer-strong{
      color:#f97373;
      font-weight:600;
    }

    /* Principal */
    main{
      flex:1;
      display:flex;
      flex-direction:column;
      padding:16px 18px;
      gap:12px;
    }
    header{
      display:flex;
      justify-content:space-between;
      align-items:flex-start;
      gap:8px;
    }
    .page-head{
      display:flex;
      flex-direction:column;
      gap:2px;
    }
    .page-title{
      font-size:18px;
      font-weight:600;
    }
    .page-sub{
      font-size:12px;
      color:var(--text-soft);
    }
    .pill{
      padding:4px 10px;
      border-radius:999px;
      border:1px solid rgba(180,157,255,.6);
      font-size:11px;
      color:var(--text-main);
      background:rgba(21,16,47,0.9);
    }
    .screen{
      flex:1;
      display:none;
      overflow-y:auto;
      padding-right:4px;
    }
    .screen.active{
      display:block;
    }

    /* Cartões */
    .card{
      background:var(--bg-card);
      border-radius:14px;
      border:1px solid rgba(148,120,255,0.3);
      padding:14px 14px 12px;
      margin-bottom:10px;
    }
    .card-soft{
      background:var(--bg-card-soft);
      border-color:rgba(148,120,255,0.22);
    }
    .card-header{
      display:flex;
      justify-content:space-between;
      align-items:center;
      margin-bottom:6px;
      gap:8px;
    }
    .card-title{
      font-size:15px;
      font-weight:600;
    }
    .card-tag{
      font-size:11px;
      color:var(--text-soft);
    }
    p{
      font-size:13px;
      line-height:1.5;
      color:#e9e4ff;
      margin-bottom:6px;
    }
    small{
      font-size:11px;
      color:var(--text-soft);
    }
    h3{
      font-size:14px;
      margin:6px 0 4px;
      color:#e5ddff;
    }
    ul{
      list-style:disc;
      margin-left:18px;
      margin-bottom:4px;
    }
    li{
      font-size:13px;
      color:#ddd2ff;
      margin-bottom:2px;
    }

    /* Inputs */
    label{
      font-size:12px;
      color:var(--text-soft);
      display:block;
      margin-bottom:4px;
    }
    input[type="text"],textarea,select{
      width:100%;
      background:#090514;
      border-radius:10px;
      border:1px solid rgba(148,120,255,0.4);
      padding:7px 9px;
      color:var(--text-main);
      font-size:13px;
      outline:none;
      resize:vertical;
      min-height:34px;
    }
    textarea{
      min-height:70px;
    }
    input:focus,textarea:focus,select:focus{
      border-color:var(--accent-soft);
      box-shadow:0 0 0 1px rgba(148,120,255,0.35);
    }
    button{
      border:none;
      border-radius:999px;
      padding:7px 14px;
      background:linear-gradient(90deg,var(--accent),var(--accent-soft));
      color:#0b0617;
      font-size:13px;
      font-weight:600;
      cursor:pointer;
      margin-top:6px;
      transition:transform .08s,box-shadow .12s,filter .12s;
      box-shadow:0 0 0 1px rgba(250,250,255,0.08);
    }
    button:hover{
      filter:brightness(1.05);
      box-shadow:0 0 12px rgba(139,92,246,0.7);
    }
    button:active{
      transform:scale(0.98);
      box-shadow:0 0 4px rgba(139,92,246,0.5);
    }

    .output{
      margin-top:8px;
      padding:8px 9px;
      border-radius:10px;
      background:#0a0514;
      border:1px solid rgba(148,120,255,0.4);
      font-size:13px;
      color:#e9e4ff;
      white-space:pre-line;
    }

    /* Desafios */
    .challenge-list{
      display:flex;
      flex-direction:column;
      gap:6px;
    }
    .challenge{
      display:flex;
      align-items:flex-start;
      gap:8px;
      font-size:13px;
      color:#e9e4ff;
    }
    .challenge input[type="checkbox"]{
      margin-top:2px;
      accent-color:var(--accent-soft);
    }
    .challenge small{
      display:block;
      margin-top:2px;
    }
    .progress-bar{
      margin-top:8px;
      border-radius:999px;
      background:#090514;
      border:1px solid rgba(148,120,255,0.45);
      overflow:hidden;
      height:10px;
    }
    .progress-inner{
      height:100%;
      width:0%;
      background:linear-gradient(90deg,var(--accent-muted),var(--accent-soft));
      transition:width .18s;
    }
    .progress-text{
      margin-top:4px;
      font-size:11px;
      color:var(--text-soft);
    }

    a{
      color:#c4b5fd;
      text-decoration:none;
    }
    a:hover{
      text-decoration:underline;
    }

    /* Responsivo */
    @media(max-width:780px){
      #app{
        flex-direction:column;
        min-height:610px;
      }
      aside{
        width:100%;
        flex-direction:row;
        flex-wrap:wrap;
        border-right:none;
        border-bottom:1px solid var(--border-soft);
        padding:10px 10px 8px;
        gap:8px;
      }
      .logo{
        flex:1 0 100%;
      }
      .nav-title{
        display:none;
      }
      .nav-item{
        font-size:12px;
        padding:6px 8px;
      }
      main{
        padding:12px 12px 14px;
      }
      header{
        flex-direction:column;
        align-items:flex-start;
      }
    }
  </style>
</head>
<body>
<div id="app">
  <aside>
    <div class="logo">
      <div class="logo-main">Rota <span>Roxa</span></div>
      <div class="logo-sub">Apoio discreto na luta contra vícios</div>
    </div>

    <div class="nav-title">Navegação</div>
    <div class="nav-item active" data-screen="inicio">
      <span class="emoji">🏠</span><span>Início</span>
    </div>
    <div class="nav-item" data-screen="como">
      <span class="emoji">🔁</span><span>Como o vício funciona</span>
    </div>

    <div class="nav-title">Tipos de vício</div>
    <div class="nav-item" data-screen="sexual">
      <span class="emoji">💜</span><span>Vício sexual</span>
    </div>
    <div class="nav-item" data-screen="celular">
      <span class="emoji">📱</span><span>Celular & redes</span>
    </div>
    <div class="nav-item" data-screen="jogos">
      <span class="emoji">🎮</span><span>Jogos</span>
    </div>
    <div class="nav-item" data-screen="outros">
      <span class="emoji">✨</span><span>Outros vícios</span>
    </div>

    <div class="nav-title">Caminho</div>
    <div class="nav-item" data-screen="desafios">
      <span class="emoji">🔥</span><span>Desafios</span>
    </div>
    <div class="nav-item" data-screen="livros">
      <span class="emoji">📚</span><span>Livros & ajuda</span>
    </div>

    <div class="disclaimer">
      <span class="disclaimer-strong">Aviso importante:</span><br>
      Este site é apenas um apoio e não substitui psicólogo, psiquiatra ou médico.
      Se você estiver em risco ou pensando em se machucar, procure ajuda profissional
      imediatamente (ex.: serviços de saúde da sua região ou CVV 188).
    </div>
  </aside>

  <main>
    <header>
      <div class="page-head">
        <div class="page-title" id="pageTitle">Bem-vindo(a)</div>
        <div class="page-sub" id="pageSub">Escolha um tipo de vício ou um desafio para começar.</div>
      </div>
      <div class="pill">Seu espaço discreto de reflexão</div>
    </header>

    <!-- INÍCIO -->
    <section class="screen active" id="screen-inicio">
      <div class="card">
        <div class="card-header">
          <div class="card-title">Você não é o seu vício</div>
        </div>
        <p>
          Rota Roxa é um espaço simples e discreto para quem luta com vício sexual, vício em celular,
          jogos ou outros hábitos que parecem sair do controle.
        </p>
        <p>
          Aqui você encontra explicações em linguagem simples, desafios pequenos e sugestões de leitura
          para caminhar um dia de cada vez. Não é um consultório nem uma rede social:
          é um ponto de apoio silencioso para você pensar na sua rota.
        </p>
        <small>
          Nada do que você escreve aqui é enviado para servidor: tudo fica apenas no seu navegador.
        </small>
      </div>

      <div class="card card-soft">
        <div class="card-header">
          <div class="card-title">Por onde começar?</div>
        </div>
        <p>
          Alguns caminhos possíveis:
        </p>
        <ul>
          <li>Abrir <strong>“Como o vício funciona”</strong> para entender o ciclo.</li>
          <li>Ir direto para um tipo específico: <strong>vício sexual</strong>, <strong>celular</strong> ou <strong>jogos</strong>.</li>
          <li>Ver os <strong>Desafios</strong> e escolher um para hoje.</li>
        </ul>
        <p>
          Avançar devagar também é avançar.
        </p>
      </div>
    </section>

    <!-- COMO FUNCIONA -->
    <section class="screen" id="screen-como">
      <div class="card">
        <div class="card-header">
          <div>
            <div class="card-title">O ciclo do vício</div>
            <div class="card-tag">Serve para vício sexual, celular, jogos e muitos outros</div>
          </div>
        </div>
        <p>
          Muitos vícios seguem um ciclo muito parecido. Entender esse ciclo não resolve tudo,
          mas é um passo importante para aprender a interromper o automático.
        </p>
      </div>

      <div class="card card-soft">
        <h3>1. Gatilho</h3>
        <p>
          Algo dispara a vontade: tédio, solidão, stress, ansiedade, ficar sozinho com o celular,
          lembranças, notificações, horários específicos (noite, madrugada).
        </p>
        <h3>2. Vontade forte (craving)</h3>
        <p>
          Surge uma vontade intensa, quase como se fosse uma “necessidade”: a mente começa a buscar
          justificativas para ceder (“só hoje”, “depois eu compenso”).
        </p>
        <h3>3. Ação / comportamento</h3>
        <p>
          A pessoa entra no vício: conteúdo sexual, rolar rede social sem parar, jogar por horas,
          comprar algo que não precisava, etc.
        </p>
        <h3>4. Alívio rápido</h3>
        <p>
          Por alguns minutos há prazer, excitação ou alívio da emoção difícil. O cérebro registra
          isso como uma “recompensa”.
        </p>
        <h3>5. Culpa e promessa</h3>
        <p>
          Depois, muitas vezes vem culpa, vergonha, tristeza. A pessoa promete que vai parar…
          até que um novo gatilho apareça e o ciclo se repita.
        </p>
        <p>
          O objetivo deste site é te ajudar a enxergar esse ciclo e começar a quebrar algumas voltas,
          com passos pequenos e possíveis.
        </p>
      </div>
    </section>

    <!-- VÍCIO SEXUAL -->
    <section class="screen" id="screen-sexual">
      <div class="card">
        <div class="card-header">
          <div>
            <div class="card-title">Vício sexual</div>
            <div class="card-tag">Quando a sexualidade começa a dominar o dia a dia</div>
          </div>
        </div>
        <p>
          Vício sexual é quando pensamentos, fantasias, conteúdos ou comportamentos ligados ao sexo
          passam a fugir do controle e começam a prejudicar a vida: estudos, trabalho, relacionamentos,
          espiritualidade ou a própria autoestima.
        </p>
        <h3>Sinais comuns</h3>
        <ul>
          <li>Prometer parar e voltar a cair repetidamente.</li>
          <li>Usar sexo ou conteúdo sexual para fugir de solidão, ansiedade ou frustração.</li>
          <li>Sentir vergonha depois e, mesmo assim, repetir.</li>
        </ul>
      </div>

      <div class="card card-soft">
        <div class="card-header">
          <div class="card-title">Reflexão guiada</div>
        </div>
        <label for="sexualTexto">Em 2–3 frases, escreva como o vício sexual tem afetado sua vida:</label>
        <textarea id="sexualTexto" placeholder="Ex.: atrapalha meu foco, minha fé, meu relacionamento, meu sono..."></textarea>
        <button onclick="gerarApoio('sexual')">Gerar mensagem de apoio</button>
        <div id="sexualOutput" class="output" style="display:none;"></div>
      </div>
    </section>

    <!-- CELULAR -->
    <section class="screen" id="screen-celular">
      <div class="card">
        <div class="card-header">
          <div>
            <div class="card-title">Vício em celular & redes sociais</div>
            <div class="card-tag">Quando o scroll nunca acaba</div>
          </div>
        </div>
        <p>
          O vício em celular e redes sociais aparece quando você sente que não consegue mais
          ficar longe do aparelho, rola o feed sem nem perceber o tempo passando e começa a perder
          sono, foco e momentos importantes da vida real.
        </p>
        <h3>Exemplos</h3>
        <ul>
          <li>Primeira coisa do dia e última antes de dormir é o celular.</li>
          <li>Você entra “só para ver uma coisa” e perde 1 ou 2 horas.</li>
          <li>Fica comparando sua vida com a dos outros o tempo todo.</li>
        </ul>
      </div>

      <div class="card card-soft">
        <div class="card-header">
          <div class="card-title">Qual app mais te prende?</div>
        </div>
        <label for="celularApp">Escreva o app ou rede que mais te prende:</label>
        <input type="text" id="celularApp" placeholder="Ex.: Instagram, TikTok, jogos de celular...">
        <button onclick="gerarApoio('celular')">Sugestão de mudança para hoje</button>
        <div id="celularOutput" class="output" style="display:none;"></div>
      </div>
    </section>

    <!-- JOGOS -->
    <section class="screen" id="screen-jogos">
      <div class="card">
        <div class="card-header">
          <div>
            <div class="card-title">Vício em jogos</div>
            <div class="card-tag">Quando o jogo começa a jogar com a sua vida</div>
          </div>
        </div>
        <p>
          Jogar pode ser algo divertido. O problema é quando vira prioridade acima de tudo:
          estudo, trabalho, sono, relacionamentos e até a própria saúde.
        </p>
        <h3>Alguns sinais</h3>
        <ul>
          <li>Você promete “só mais uma partida” e fica horas.</li>
          <li>Fica irritado quando não pode jogar.</li>
          <li>Começa a mentir sobre quanto tempo passa jogando.</li>
        </ul>
      </div>

      <div class="card card-soft">
        <div class="card-header">
          <div class="card-title">O que os jogos têm tirado de você?</div>
        </div>
        <label for="jogosTexto">Escreva em 1–2 frases o que o vício em jogos está tirando de você:</label>
        <textarea id="jogosTexto" placeholder="Ex.: notas da escola, sono, tempo com minha família..."></textarea>
        <button onclick="gerarApoio('jogos')">Ler uma reflexão</button>
        <div id="jogosOutput" class="output" style="display:none;"></div>
      </div>
    </section>

    <!-- OUTROS VÍCIOS -->
    <section class="screen" id="screen-outros">
      <div class="card">
        <div class="card-header">
          <div>
            <div class="card-title">Outros vícios</div>
            <div class="card-tag">Compras, comida, apostas, nicotina e mais</div>
          </div>
        </div>
        <p>
          Nem todo vício aparece nas mesmas categorias. Talvez você esteja lutando com compras
          compulsivas, comida, apostas, nicotina ou outra coisa. O nome muda, mas o ciclo costuma ser parecido.
        </p>
      </div>

      <div class="card card-soft">
        <div class="card-header">
          <div class="card-title">Qual vício você quer trabalhar?</div>
        </div>
        <label for="outrosNome">Escreva o vício/hábito que você quer enfrentar:</label>
        <input type="text" id="outrosNome" placeholder="Ex.: compras, comida, apostas, cigarro...">
        <label for="outrosDescricao" style="margin-top:6px;">Descreva em poucas frases como isso tem afetado você:</label>
        <textarea id="outrosDescricao" placeholder="Ex.: estou me endividando, estou engordando, estou me isolando..."></textarea>
        <button onclick="gerarApoio('outros')">Ver meu ciclo e um conselho</button>
        <div id="outrosOutput" class="output" style="display:none;"></div>
      </div>
    </section>

    <!-- DESAFIOS -->
    <section class="screen" id="screen-desafios">
      <div class="card">
        <div class="card-header">
          <div>
            <div class="card-title">Desafios para hoje</div>
            <div class="card-tag">Pequenos passos que você pode tentar agora</div>
          </div>
        </div>
        <p>
          Escolha alguns desafios que façam sentido para o seu momento. Você não precisa fazer
          todos de uma vez. Marcar um ou dois já é um passo real.
        </p>
      </div>

      <div class="card card-soft">
        <h3>Lista de desafios</h3>
        <div class="challenge-list" id="challengeList">
          <!-- Preenchido via JS -->
        </div>
        <div class="progress-bar">
          <div class="progress-inner" id="challengeProgress"></div>
        </div>
        <div class="progress-text" id="challengeText"></div>
      </div>
    </section>

    <!-- LIVROS -->
    <section class="screen" id="screen-livros">
      <div class="card">
        <div class="card-header">
          <div>
            <div class="card-title">Livros & recursos (exemplos)</div>
            <div class="card-tag">Você pode trocar depois pelos materiais que preferir</div>
          </div>
        </div>
        <p>
          Abaixo estão exemplos de materiais que você pode substituir por nomes e links reais.
          Ler não substitui terapia, mas pode abrir caminhos e novas formas de enxergar a sua história.
        </p>
      </div>

      <div class="card card-soft">
        <h3>Vício sexual</h3>
        <ul>
          <li>
            <strong>Livro 1 sobre vício sexual</strong> – coloque aqui um livro de confiança que
            fale sobre dependência sexual e recuperação.  
            <small>https://www.scielo.br/j/sess/a/8RyYKH8fHyHv5tXjdLF7yBC/?lang=pt</a></small>
          </li>
        </ul>

        <h3>Celular & redes sociais</h3>
        <ul>
          <li>
            <strong>Livro 2 sobre uso saudável de tecnologia</strong> – um livro que fale sobre
            equilíbrio digital e limites com redes sociais.  
            <small>https://www.gov.br/mdh/pt-br/assuntos/noticias/2020-2/agosto/cartilha_uso_tecnologia.pdf</a></small>
          </li>
        </ul>

        <h3>Jogos</h3>
        <ul>
          <li>
            <strong>Livro 3 sobre jogos e equilíbrio</strong> – algo que trate de como colocar o jogo
            no lugar certo na vida.  
            <small>https://pt.scribd.com/document/808769350/Saindo-do-vi-cio-dos-jogos-pdf</a></small>
          </li>
        </ul>

        <h3>Outros vícios</h3>
        <ul>
          <li>
            <strong>Livro 4 sobre dependências em geral</strong> – falando de compulsão, hábitos,
            recuperação e apoio.  
            <small>https://storage.blucher.com.br/book/pdf_preview/9786555061208-amostra.pdf</a></small>
          </li>
        </ul>

        <p style="margin-top:6px;">
          Se você sentir que está perdendo o controle, a melhor leitura pode ser procurar um
          profissional: psicólogo, psiquiatra, médico ou serviço público de saúde da sua região.
        </p>
      </div>
    </section>
  </main>
</div>

<script>
  // Navegação
  const navItems = document.querySelectorAll('.nav-item');
  const screens = document.querySelectorAll('.screen');
  const pageTitle = document.getElementById('pageTitle');
  const pageSub = document.getElementById('pageSub');

  const titles = {
    inicio: {t:"Bem-vindo(a)",s:"Escolha um tipo de vício ou um desafio para começar."},
    como: {t:"Como o vício funciona",s:"Entenda o ciclo que se repete em muitos hábitos compulsivos."},
    sexual: {t:"Vício sexual",s:"Reflexão guiada e primeiros passos para lidar com esse tipo de luta."},
    celular: {t:"Vício em celular & redes",s:"Ideias práticas para reduzir o domínio do aparelho."},
    jogos: {t:"Vício em jogos",s:"Quando o jogo deixa de ser diversão e vira peso."},
    outros: {t:"Outros vícios",s:"Dê nome ao seu vício e veja o ciclo com clareza."},
    desafios: {t:"Desafios",s:"Pequenos passos que você pode tentar hoje."},
    livros: {t:"Livros & ajuda",s:"Sugestões de leitura e lembretes importantes de cuidado."}
  };

  navItems.forEach(item=>{
    item.addEventListener('click',()=>{
      navItems.forEach(i=>i.classList.remove('active'));
      item.classList.add('active');

      const target = item.getAttribute('data-screen');
      screens.forEach(sc=>{
        sc.classList.toggle('active', sc.id === 'screen-'+target);
      });

      if(titles[target]){
        pageTitle.textContent = titles[target].t;
        pageSub.textContent = titles[target].s;
      }
    });
  });

  // Mensagens de apoio simples (simulação de "IA")
  function gerarApoio(tipo){
    if(tipo === 'sexual'){
      const txt = (document.getElementById('sexualTexto').value || "").trim();
      const out = document.getElementById('sexualOutput');
      let base =
`Você não é o único nem a única a lutar com vício sexual. Isso não define o seu valor como pessoa.

Você escreveu:
"${txt || '...' }"

Um ponto de partida possível:
• Observe quais são os horários, lugares e emoções que mais te puxam para esse vício.
• Em vez de prometer perfeição, tente hoje apenas atrasar um pouco a resposta ao impulso e mudar o ambiente (levantar da cama, guardar o aparelho, beber água, respirar fundo).

Se você sentir que está perdendo totalmente o controle, considere procurar um psicólogo, psiquiatra ou serviço de saúde da sua região.

Sugestão de leitura (exemplo):
Livro sobre vício sexual – https://exemplo.com/livro-vicio-sexual`;

      out.textContent = base;
      out.style.display = 'block';
    }

    if(tipo === 'celular'){
      const app = (document.getElementById('celularApp').value || "").trim();
      const out = document.getElementById('celularOutput');
      let appTxt = app || "seu app mais viciante";
      let base =
`Hoje, em vez de tentar “largar o celular para sempre”, escolha um passo pequeno.

• Defina um horário em que você não vai usar ${appTxt} (por exemplo, a primeira hora depois que acordar ou a última antes de dormir).
• Se precisar pegar o celular, faça isso de forma intencional: já sabendo o que vai fazer, e por quanto tempo.

Com o tempo, pequenos limites somados viram uma grande mudança.

Sugestão de leitura (exemplo):
Livro sobre uso saudável de tecnologia – https://exemplo.com/livro-celular`;

      out.textContent = base;
      out.style.display = 'block';
    }

    if(tipo === 'jogos'){
      const txt = (document.getElementById('jogosTexto').value || "").trim();
      const out = document.getElementById('jogosOutput');
      let base =
`Jogos podem ser bons, mas quando passam a roubar estudo, sono, dinheiro ou relacionamentos,
é sinal de que algo precisa mudar.

Você escreveu:
"${txt || '...' }"

Um desafio possível:
• Escolha um horário específico para jogar e um para parar, e cumpra apenas hoje.
• Experimente ter um dia da semana com o jogo bem reduzido ou ausente, preenchendo esse tempo com outra atividade.

Se estiver muito difícil controlar, vale conversar com alguém de confiança e, se possível, com um profissional.

Sugestão de leitura (exemplo):
Livro sobre equilíbrio com jogos – https://exemplo.com/livro-jogos`;

      out.textContent = base;
      out.style.display = 'block';
    }

    if(tipo === 'outros'){
      const nome = (document.getElementById('outrosNome').value || "").trim() || "seu vício";
      const desc = (document.getElementById('outrosDescricao').value || "").trim();
      const out = document.getElementById('outrosOutput');
      let base =
`Você está dando nome àquilo que te faz mal: "${nome}". Isso já é um passo importante.

Descrição que você trouxe:
"${desc || '...' }"

Lembre-se do ciclo:
gatilho → vontade forte → ${nome} → alívio rápido → culpa → repetição.

Hoje, tente:
• Identificar pelo menos um gatilho que puxa para ${nome}.
• Criar uma resposta alternativa: outra ação que você pode fazer quando o gatilho aparecer.

Se esse vício estiver destruindo sua saúde, finanças ou relacionamentos, procurar ajuda profissional é um ato de coragem, não de fraqueza.

Sugestão de leitura (exemplo):
Livro geral sobre dependências – https://exemplo.com/livro-outros`;

      out.textContent = base;
      out.style.display = 'block';
    }
  }

  // Desafios com localStorage
  const desafios = [
    {
      id:'d1',
      texto:'Hoje vou apenas observar e anotar 3 momentos em que a vontade do meu vício apareceu.',
      extra:'Sem se julgar, apenas registrando: horário, lugar e o que você estava sentindo.'
    },
    {
      id:'d2',
      texto:'Quando a vontade vier, vou esperar 10 minutos antes de ceder, fazendo outra coisa nesse tempo.',
      extra:'Levantar, beber água, ir para outro cômodo, alongar, respirar fundo.'
    },
    {
      id:'d3',
      texto:'Vou trocar 15 minutos do meu vício por 15 minutos de uma atividade saudável.',
      extra:'Ler, escrever, caminhar, ouvir uma música calma, falar com alguém confiável.'
    },
    {
      id:'d4',
      texto:'Vou tornar o ambiente um pouco menos favorável ao vício.',
      extra:'Ex.: tirar app da tela inicial, usar bloqueador, não ficar sozinho com o aparelho.'
    },
    {
      id:'d5',
      texto:'Vou ter um “período protegido” do dia sem o meu vício.',
      extra:'Pode ser uma manhã, uma noite, ou algumas horas específicas.'
    }
  ];

  function carregarDesafios(){
    const container = document.getElementById('challengeList');
    const saved = JSON.parse(localStorage.getItem('rotaRoxaDesafios') || '{}');
    container.innerHTML = '';
    desafios.forEach(d=>{
      const wrap = document.createElement('div');
      wrap.className = 'challenge';
      const check = document.createElement('input');
      check.type = 'checkbox';
      check.checked = !!saved[d.id];
      check.dataset.id = d.id;
      const textDiv = document.createElement('div');
      textDiv.innerHTML = `${d.texto}<small>${d.extra}</small>`;
      wrap.appendChild(check);
      wrap.appendChild(textDiv);
      container.appendChild(wrap);

      check.addEventListener('change',()=>{
        const current = JSON.parse(localStorage.getItem('rotaRoxaDesafios') || '{}');
        current[d.id] = check.checked;
        localStorage.setItem('rotaRoxaDesafios', JSON.stringify(current));
        atualizarProgresso();
      });
    });
    atualizarProgresso();
  }

  function atualizarProgresso(){
    const saved = JSON.parse(localStorage.getItem('rotaRoxaDesafios') || '{}');
    const total = desafios.length;
    let done = 0;
    desafios.forEach(d=>{ if(saved[d.id]) done++; });
    const pct = total ? Math.round((done/total)*100) : 0;
    document.getElementById('challengeProgress').style.width = pct + '%';
    document.getElementById('challengeText').textContent =
      `Você concluiu ${done} de ${total} desafios (${pct}%).`;
  }

  carregarDesafios();
</script>
</body>
</html>
