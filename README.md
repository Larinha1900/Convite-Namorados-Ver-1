<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Convite Dia dos Namorados</title>
<style>
  body, html {
    margin:0; padding:0; height:100%;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background: #fff0f5;
    display:flex;
    justify-content:center;
    align-items:center;
    overflow: hidden;
  }
  #container {
    width: 100%;
    max-width: 400px;
    text-align: center;
    position: relative;
  }
  /* Tela Inicial */
  #tela-inicial {
    display: block;
  }
  #envelope {
    width: 150px;
    height: 100px;
    margin: 0 auto 20px auto;
    background: #d80000;
    position: relative;
    border-radius: 5px;
    box-shadow: 0 5px 10px rgba(0,0,0,0.3);
    cursor: pointer;
  }
  /* Envelope "bico" */
  #envelope::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    width: 0; height: 0;
    margin: auto;
    border-left: 75px solid transparent;
    border-right: 75px solid transparent;
    border-bottom: 50px solid #a00000;
    border-radius: 5px 5px 0 0;
  }
  h2 {
    color: #900;
    margin-bottom: 30px;
    font-size: 1.3em;
  }
  button {
    font-size: 1.2em;
    padding: 10px 30px;
    margin: 10px;
    border-radius: 25px;
    border: none;
    cursor: pointer;
    font-weight: bold;
    transition: background-color 0.3s ease;
  }
  button#sim {
    background-color: #e60000;
    color: white;
  }
  button#sim:hover {
    background-color: #b30000;
  }
  button#nao {
    background-color: #aaa;
    color: #333;
  }
  button#nao:hover {
    background-color: #888;
    color: white;
  }

  /* Telas de resposta */
  #tela-sim, #tela-nao {
    display: none;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    color: #900;
  }
  #tela-sim emoji, #tela-nao emoji {
    font-size: 6em;
    margin: 20px 0;
  }
  #emoji-sim {
    font-size: 8em;
    margin: 30px 0;
  }
  #emoji-nao {
    font-size: 8em;
    margin: 30px 0;
  }
  /* Corações caindo */
  .coracao {
    position: fixed;
    width: 25px;
    height: 25px;
    background: red;
    transform: rotate(45deg);
    left: 50%;
    animation-name: cair;
    animation-timing-function: linear;
    animation-iteration-count: infinite;
  }
  .coracao::before,
  .coracao::after {
    content: "";
    position: absolute;
    width: 25px;
    height: 25px;
    background: red;
    border-radius: 50%;
  }
  .coracao::before {
    top: -12.5px;
    left: 0;
  }
  .coracao::after {
    left: 12.5px;
    top: 0;
  }
  @keyframes cair {
    0% {
      transform: translateY(-50px) rotate(45deg);
      opacity: 1;
    }
    100% {
      transform: translateY(100vh) rotate(45deg);
      opacity: 0;
    }
  }
</style>
</head>
<body>
  <div id="container">
    <div id="tela-inicial">
      <div id="envelope" title="Clique aqui para abrir o convite"></div>
      <h2>Quer ser meu par de Dia dos Namorados para dormir de dupla igual 2 ratinhos?</h2>
      <button id="sim">Sim</button>
      <button id="nao">Não</button>
    </div>
    <div id="tela-sim">
     <img id="img-sim" src="cat.jpg" alt="Par de Dia dos Namorados" style="max-width:100%; border-radius: 15px;"/>
      <h2>Que legal! Vai ser ótimo dormir juntinhos!</h2>
    </div>
    <div id="tela-nao">
      <img id="img-nao" src="dog.jpg" alt="Resposta Não" style="max-width:100%; border-radius: 15px;"/>
     
    </div>
  </div>

<script>
  const telaInicial = document.getElementById('tela-inicial');
  const telaSim = document.getElementById('tela-sim');
  const telaNao = document.getElementById('tela-nao');
  const botaoSim = document.getElementById('sim');
  const botaoNao = document.getElementById('nao');
  const envelope = document.getElementById('envelope');

  function mostrarTela(tela) {
    telaInicial.style.display = 'none';
    telaSim.style.display = 'none';
    telaNao.style.display = 'none';

    tela.style.display = 'flex';
  }

  // Função para criar corações caindo
  function criarCoracao() {
    const coracao = document.createElement('div');
    coracao.classList.add('coracao');
    coracao.style.left = Math.random() * window.innerWidth + 'px';
    coracao.style.animationDuration = 3 + Math.random() * 3 + 's';
    document.body.appendChild(coracao);
    // Remove o coração após a animação para não acumular muitos elementos
    setTimeout(() => {
      coracao.remove();
    }, 6000);
  }

  botaoSim.addEventListener('click', () => {
    mostrarTela(telaSim);

    // Criar vários corações caindo
    const interval = setInterval(criarCoracao, 300);

    // Para a animação após 6 segundos
    setTimeout(() => clearInterval(interval), 6000);
  });

  botaoNao.addEventListener('click', () => {
    mostrarTela(telaNao);
  });

  // Opcional: clique no envelope também abre o convite com opções
  envelope.addEventListener('click', () => {
    alert('Escolha "Sim" ou "Não" para responder ao convite!');
  });
</script>

</body>
</html>
