```vue
<script setup>
import { ref } from 'vue'

const activeCard = ref(null)
const activeEffect = ref(null)
const quizAnswer = ref(null)

const sources = [
  {
    icon: '🧴',
    title: 'Garrafas',
    text: 'Plásticos podem se desgastar com o tempo e liberar pequenas partículas.'
  },
  {
    icon: '👕',
    title: 'Roupas',
    text: 'Tecidos sintéticos podem liberar fibras plásticas durante as lavagens.'
  },
  {
    icon: '🚗',
    title: 'Pneus',
    text: 'O desgaste dos pneus também contribui para a presença de partículas plásticas no ambiente.'
  },
  {
    icon: '🌊',
    title: 'Oceanos',
    text: 'Grande quantidade de resíduos plásticos chega aos ambientes aquáticos e pode se fragmentar.'
  }
]

const effects = [
  {
    title: 'Inflamação',
    icon: '🔥',
    text: 'Pesquisas investigam a possibilidade de partículas muito pequenas contribuírem para processos inflamatórios.'
  },
  {
    title: 'Sistema respiratório',
    icon: '🫁',
    text: 'Partículas presentes no ar podem ser inaladas. Os possíveis efeitos à saúde ainda estão sendo estudados.'
  },
  {
    title: 'Sistema digestivo',
    icon: '🧬',
    text: 'Microplásticos podem chegar ao organismo por meio da ingestão de água e alimentos contaminados.'
  }
]

const quiz = (answer) => {
  quizAnswer.value = answer
}
</script>

<template>
  <div class="site">

    <!-- HERO -->
    <section class="hero">
      <div class="particles">
        <span v-for="n in 18" :key="n"></span>
      </div>

      <div class="hero-content">
        <div class="mini-label">
          <span class="dot"></span>
          VOCÊ CONSEGUE VÊ-LOS?
        </div>

        <h1>
          Você já comeu
          <em>plástico</em>
          hoje?
        </h1>

        <p>
          Existe um mundo invisível ao nosso redor.
          Descubra o que são os microplásticos e por que
          eles despertam tanta atenção.
        </p>

        <a href="#inicio" class="hero-button">
          Descobrir
          <span>↓</span>
        </a>
      </div>

      <div class="scroll-indicator">
        ROLE PARA DESCOBRIR
        <span>↓</span>
      </div>
    </section>


    <!-- INTRO -->
    <section id="inicio" class="intro section">
      <div class="section-number">01</div>

      <span class="section-label">
        PRIMEIRO: ENTENDER
      </span>

      <h2>
        Afinal...
        <strong>o que são</strong>
        microplásticos?
      </h2>

      <p class="lead">
        São pequenos fragmentos de plástico,
        geralmente menores que 5 milímetros.
      </p>

      <button
        class="outline-button"
        @click="activeCard = activeCard === 'definition' ? null : 'definition'"
      >
        {{ activeCard === 'definition' ? 'Esconder' : 'Quero entender' }}
        <span>→</span>
      </button>

      <Transition name="slide">
        <div
          v-if="activeCard === 'definition'"
          class="explanation-card"
        >
          <div class="big-number">
            5<span>mm</span>
          </div>

          <div>
            <h3>Pequenos, mas importantes</h3>

            <p>
              Microplásticos podem surgir quando objetos maiores
              de plástico se degradam ou podem ser produzidos
              diretamente em tamanhos muito pequenos.
            </p>
          </div>
        </div>
      </Transition>
    </section>


    <!-- CURIOSIDADE -->
    <section class="curiosity">
      <div class="curiosity-inner">
        <span>⚠ VOCÊ SABIA?</span>

        <h2>
          O problema não está
          apenas no oceano.
        </h2>

        <p>
          Essas partículas já foram encontradas em
          diferentes ambientes e são alvo de pesquisas
          científicas em todo o mundo.
        </p>
      </div>
    </section>


    <!-- FONTES -->
    <section class="sources section">
      <div class="section-number">02</div>

      <span class="section-label">
        OLHE AO SEU REDOR
      </span>

      <h2>
        Onde eles
        <strong>aparecem?</strong>
      </h2>

      <p class="lead">
        Toque nos cartões e descubra algumas fontes
        relacionadas aos microplásticos.
      </p>

      <div class="source-grid">
        <button
          v-for="(source, index) in sources"
          :key="source.title"
          class="source-card"
          :class="{ active: activeCard === `source-${index}` }"
          @click="activeCard = activeCard === `source-${index}` ? null : `source-${index}`"
        >
          <div class="source-icon">
            {{ source.icon }}
          </div>

          <h3>{{ source.title }}</h3>

          <span class="plus">
            {{ activeCard === `source-${index}` ? '−' : '+' }}
          </span>

          <Transition name="fade">
            <p v-if="activeCard === `source-${index}`">
              {{ source.text }}
            </p>
          </Transition>
        </button>
      </div>
    </section>


    <!-- INTERACTIVE -->
    <section class="interactive">
      <div class="interactive-header">
        <span class="section-label">
          03 — DESAFIO
        </span>

        <h2>
          Você consegue
          <strong>encontrá-los?</strong>
        </h2>

        <p>
          Existem mais conexões com o plástico no nosso
          cotidiano do que parece.
        </p>
      </div>

      <div class="orbit">
        <div class="orbit-center">
          <span>?</span>
          <small>MICRO</small>
          <small>PLÁSTICO</small>
        </div>

        <div class="orbit-item item-1">💧</div>
        <div class="orbit-item item-2">👕</div>
        <div class="orbit-item item-3">🍽️</div>
        <div class="orbit-item item-4">🚗</div>
        <div class="orbit-item item-5">🌊</div>
      </div>
    </section>


    <!-- CORPO -->
    <section class="body-section section">
      <div class="section-number">04</div>

      <span class="section-label">
        E DEPOIS QUE ELES CHEGAM ATÉ NÓS?
      </span>

      <h2>
        O caminho
        <strong>até o corpo.</strong>
      </h2>

      <p class="lead">
        A exposição humana pode acontecer por diferentes
        vias, como ingestão e inalação.
      </p>

      <div class="body-visual">
        <div class="body-circle circle-one"></div>
        <div class="body-circle circle-two"></div>

        <div class="body-symbol">
          🧍
        </div>

        <div class="body-label label-top">
          <span>01</span>
          INGESTÃO
        </div>

        <div class="body-label label-right">
          <span>02</span>
          INALAÇÃO
        </div>

        <div class="body-label label-bottom">
          <span>03</span>
          PESQUISA
        </div>
      </div>

      <div class="research-note">
        <span>🔬</span>

        <p>
          <strong>A ciência ainda está investigando.</strong>
          Nem todos os efeitos dos microplásticos sobre a saúde
          humana estão completamente estabelecidos.
        </p>
      </div>
    </section>


    <!-- EFEITOS -->
    <section class="effects section">
      <div class="section-number">05</div>

      <span class="section-label">
        O QUE A CIÊNCIA INVESTIGA
      </span>

      <h2>
        Possíveis
        <strong>efeitos.</strong>
      </h2>

      <p class="lead">
        A exposição aos microplásticos é um tema
        que continua sendo estudado.
      </p>

      <div class="effects-list">
        <button
          v-for="(effect, index) in effects"
          :key="effect.title"
          class="effect"
          @click="activeEffect = activeEffect === index ? null : index"
        >
          <div class="effect-icon">
            {{ effect.icon }}
          </div>

          <div class="effect-info">
            <span>0{{ index + 1 }}</span>
            <h3>{{ effect.title }}</h3>
          </div>

          <div class="effect-arrow">
            {{ activeEffect === index ? '−' : '↗' }}
          </div>

          <Transition name="fade">
            <p v-if="activeEffect === index">
              {{ effect.text }}
            </p>
          </Transition>
        </button>
      </div>
    </section>


    <!-- MITO -->
    <section class="myth">
      <div class="myth-card">
        <span class="section-label">
          MITO OU VERDADE?
        </span>

        <div v-if="quizAnswer === null">
          <h2>
            Todo plástico é
            <strong>microplástico?</strong>
          </h2>

          <p>
            Pense antes de responder.
          </p>

          <div class="quiz-buttons">
            <button @click="quiz('verdade')">
              VERDADE
            </button>

            <button @click="quiz('mito')">
              MITO
            </button>
          </div>
        </div>

        <div v-else class="quiz-result">
          <div class="result-icon">
            {{ quizAnswer === 'mito' ? '✓' : '×' }}
          </div>

          <h3>
            {{ quizAnswer === 'mito' ? 'Isso mesmo!' : 'Quase!' }}
          </h3>

          <p>
            Microplásticos são partículas de plástico
            pequenas. Um objeto plástico maior não é,
            por si só, um microplástico.
          </p>

          <button
            class="try-again"
            @click="quizAnswer = null"
          >
            Tentar novamente
          </button>
        </div>
      </div>
    </section>


    <!-- PREVENÇÃO -->
    <section class="prevention section">
      <div class="section-number">06</div>

      <span class="section-label">
        E O QUE PODEMOS FAZER?
      </span>

      <h2>
        Pequenas atitudes.
        <strong>Grandes mudanças.</strong>
      </h2>

      <div class="tips">
        <div class="tip">
          <span>01</span>

          <div>
            <h3>Reduza descartáveis</h3>

            <p>
              Sempre que possível, prefira opções reutilizáveis.
            </p>
          </div>
        </div>

        <div class="tip">
          <span>02</span>

          <div>
            <h3>Reutilize</h3>

            <p>
              Dar mais vida útil aos objetos pode reduzir
              a necessidade de novos produtos.
            </p>
          </div>
        </div>

        <div class="tip">
          <span>03</span>

          <div>
            <h3>Descarte corretamente</h3>

            <p>
              O descarte adequado ajuda a evitar que
              resíduos plásticos cheguem ao ambiente.
            </p>
          </div>
        </div>
      </div>
    </section>


    <!-- FINAL -->
    <section class="final">
      <div class="final-content">
        <span>AGORA VOCÊ SABE.</span>

        <h2>
          O invisível
          <em>também importa.</em>
        </h2>

        <p>
          Os microplásticos ainda levantam muitas perguntas
          para a ciência. E quanto mais aprendemos,
          melhor podemos cuidar do ambiente e de nós mesmos.
        </p>

        <a href="#" class="back-top">
          ↑ VOLTAR AO TOPO
        </a>
      </div>
    </section>


    <!-- CRÉDITOS -->
    <section class="credits">
      <div class="credits-content">

        <span class="credits-label">
          CRÉDITOS
        </span>

        <h2>
          Por trás deste
          <strong>projeto.</strong>
        </h2>

        <p class="credits-intro">
          Este site foi desenvolvido como parte do projeto
          sobre microplásticos.
        </p>

        <div class="credits-grid">

          <!-- DESENVOLVEDOR -->
          <div class="credit-card developer">
            <span class="credit-number">01</span>

            <div class="credit-icon">
              💻
            </div>

            <span class="credit-role">
              DESENVOLVIMENTO E PROGRAMAÇÃO
            </span>

            <h3>
              Davi Novaes Brito
            </h3>

            <p>
              Desenvolvimento, programação, estrutura,
              design e interatividade do site.
            </p>
          </div>


          <!-- INTEGRANTES -->
          <div class="credit-card">
            <span class="credit-number">02</span>

            <div class="credit-icon">
              👥
            </div>

            <span class="credit-role">
              INTEGRANTES DO PROJETO
            </span>

            
<h3 class="integrantes-nomes">
  <span>Adilson Junior</span>
  <span>Bryan Daniel Gonçalves</span>
  <span>Davi Novaes Brito</span>
  <span>Edson Ferreira Souza</span>
  <span>Gabriel Fagundes</span>
  <span>Gustavo Bernardes</span>
  <span>Kauã Gomes Bezerra</span>
  <span>Kauã Victor Lima Silva</span>
</h3>



            <p>
              Integrantes responsáveis pela participação
              e desenvolvimento do projeto.
            </p>
          </div>

        </div>


        <div class="rights">
          <div class="rights-line"></div>

          <p>
  © 2026 — MICROPLÁSTICOS
</p>

<span>
  PROJETO ACADÊMICO — UNIVERSIDADE CRUZEIRO DO SUL
</span>
        </div>

      </div>
    </section>


    <!-- FOOTER -->
    <footer>
      <span>MICROPLÁSTICOS</span>

      <p>
        Informação • Ciência • Consciência
      </p>
    </footer>

  </div>
</template>


<style>
* {
  box-sizing: border-box;
}

html {
  scroll-behavior: smooth;
}

body {
  margin: 0;
  font-family:
    Inter,
    ui-sans-serif,
    system-ui,
    -apple-system,
    BlinkMacSystemFont,
    "Segoe UI",
    sans-serif;
  background: #071c1a;
  color: #10211e;
}

button,
a {
  font-family: inherit;
}

button {
  border: 0;
}

.site {
  overflow: hidden;
}


/* HERO */

.hero {
  min-height: 100svh;
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 35px 24px;
  background:
    radial-gradient(
      circle at 50% 35%,
      #164d40 0%,
      #09251f 38%,
      #04110f 80%
    );
  color: white;
  text-align: center;
}

.hero-content {
  width: 100%;
  max-width: 650px;
  position: relative;
  z-index: 2;
}

.mini-label {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 9px;
  font-size: 10px;
  letter-spacing: 3px;
  color: #65e6b1;
  font-weight: 700;
}

.dot {
  width: 6px;
  height: 6px;
  background: #65e6b1;
  border-radius: 50%;
  box-shadow: 0 0 15px #65e6b1;
}

.hero h1 {
  margin: 28px 0 24px;
  font-size: clamp(48px, 14vw, 92px);
  line-height: .92;
  letter-spacing: -4px;
  font-weight: 700;
}

.hero h1 em {
  display: block;
  color: #65e6b1;
  font-style: normal;
}

.hero p {
  max-width: 520px;
  margin: auto;
  color: rgba(255,255,255,.67);
  line-height: 1.7;
  font-size: 16px;
}

.hero-button {
  display: inline-flex;
  align-items: center;
  gap: 13px;
  margin-top: 34px;
  padding: 16px 25px;
  border-radius: 50px;
  background: #65e6b1;
  color: #061613;
  text-decoration: none;
  font-size: 15px;
  font-weight: 800;
  transition: .3s;
}

.hero-button:hover {
  transform: translateY(-4px);
}

.hero-button span {
  font-size: 19px;
}

.scroll-indicator {
  position: absolute;
  bottom: 25px;
  display: flex;
  flex-direction: column;
  gap: 5px;
  font-size: 8px;
  letter-spacing: 2px;
  opacity: .35;
}

.scroll-indicator span {
  font-size: 15px;
}


/* PARTICLES */

.particles span {
  position: absolute;
  width: 5px;
  height: 5px;
  border-radius: 50%;
  background: #65e6b1;
  opacity: .35;
  animation: particleFloat 5s infinite ease-in-out;
}

.particles span:nth-child(1) { top: 15%; left: 12%; }
.particles span:nth-child(2) { top: 25%; left: 80%; animation-delay: 1s; }
.particles span:nth-child(3) { top: 65%; left: 15%; animation-delay: 2s; }
.particles span:nth-child(4) { top: 80%; left: 82%; animation-delay: 3s; }
.particles span:nth-child(5) { top: 42%; left: 90%; animation-delay: 1.5s; }
.particles span:nth-child(6) { top: 10%; left: 50%; animation-delay: 2.5s; }
.particles span:nth-child(7) { top: 73%; left: 52%; animation-delay: .5s; }
.particles span:nth-child(8) { top: 35%; left: 7%; animation-delay: 3s; }
.particles span:nth-child(9) { top: 55%; left: 88%; animation-delay: 4s; }
.particles span:nth-child(10) { top: 88%; left: 32%; animation-delay: 1s; }
.particles span:nth-child(11) { top: 18%; left: 30%; animation-delay: 2s; }
.particles span:nth-child(12) { top: 90%; left: 72%; animation-delay: 3s; }
.particles span:nth-child(13) { top: 48%; left: 20%; animation-delay: 4s; }
.particles span:nth-child(14) { top: 32%; left: 70%; animation-delay: 2s; }
.particles span:nth-child(15) { top: 70%; left: 70%; animation-delay: 1s; }
.particles span:nth-child(16) { top: 12%; left: 90%; animation-delay: 3s; }
.particles span:nth-child(17) { top: 82%; left: 10%; animation-delay: 2s; }
.particles span:nth-child(18) { top: 50%; left: 45%; animation-delay: 4s; }

@keyframes particleFloat {
  0%, 100% {
    transform: translateY(0) scale(1);
  }

  50% {
    transform: translateY(-25px) scale(1.7);
  }
}


/* SECTIONS */

.section {
  padding: 100px 24px;
  max-width: 1000px;
  margin: auto;
}

.section-number {
  font-size: 72px;
  line-height: 1;
  font-weight: 900;
  color: #dfe9e4;
}

.section-label {
  display: block;
  margin-top: 22px;
  font-size: 10px;
  letter-spacing: 3px;
  font-weight: 800;
  color: #198f68;
}

.section h2 {
  margin: 18px 0;
  max-width: 800px;
  font-size: clamp(42px, 11vw, 76px);
  line-height: .98;
  letter-spacing: -3px;
}

.section h2 strong {
  display: block;
  color: #198f68;
}

.lead {
  max-width: 620px;
  color: #596963;
  font-size: 18px;
  line-height: 1.7;
}


/* INTRO */

.intro {
  background: #f7f9f6;
  max-width: none;
  padding-left: max(24px, calc((100% - 950px) / 2));
  padding-right: max(24px, calc((100% - 950px) / 2));
}

.outline-button {
  margin-top: 28px;
  padding: 14px 20px;
  border: 1px solid #198f68;
  border-radius: 50px;
  background: transparent;
  color: #198f68;
  font-weight: 800;
  cursor: pointer;
}

.outline-button span {
  margin-left: 8px;
}

.explanation-card {
  margin-top: 25px;
  padding: 25px;
  display: flex;
  align-items: center;
  gap: 22px;
  border-radius: 24px;
  background: #eaf5ef;
  max-width: 650px;
}

.big-number {
  flex-shrink: 0;
  font-size: 40px;
  font-weight: 900;
  color: #198f68;
}

.big-number span {
  font-size: 18px;
}

.explanation-card h3 {
  margin: 0 0 8px;
  font-size: 20px;
}

.explanation-card p {
  margin: 0;
  color: #596963;
  line-height: 1.6;
  font-size: 14px;
}


/* CURIOSITY */

.curiosity {
  padding: 100px 24px;
  background: #0b3028;
  color: white;
}

.curiosity-inner {
  max-width: 900px;
  margin: auto;
}

.curiosity span {
  color: #65e6b1;
  font-size: 10px;
  letter-spacing: 3px;
  font-weight: 800;
}

.curiosity h2 {
  max-width: 700px;
  margin: 20px 0;
  font-size: clamp(38px, 10vw, 70px);
  line-height: 1;
  letter-spacing: -3px;
}

.curiosity p {
  max-width: 580px;
  color: rgba(255,255,255,.65);
  line-height: 1.7;
}


/* SOURCES */

.sources {
  background: #f7f9f6;
  max-width: none;
  padding-left: max(24px, calc((100% - 950px) / 2));
  padding-right: max(24px, calc((100% - 950px) / 2));
}

.source-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
  margin-top: 40px;
}

.source-card {
  min-height: 190px;
  position: relative;
  padding: 22px;
  border-radius: 22px;
  background: white;
  text-align: left;
  cursor: pointer;
  transition: .3s;
  border: 1px solid #e3ebe6;
}

.source-card:hover,
.source-card.active {
  transform: translateY(-4px);
  border-color: #65b996;
}

.source-icon {
  font-size: 35px;
  margin-bottom: 22px;
}

.source-card h3 {
  margin: 0;
  font-size: 19px;
}

.plus {
  position: absolute;
  top: 20px;
  right: 20px;
  font-size: 22px;
  color: #198f68;
}

.source-card p {
  color: #687871;
  font-size: 13px;
  line-height: 1.55;
}


/* INTERACTIVE */

.interactive {
  min-height: 700px;
  padding: 100px 24px;
  background: #061613;
  color: white;
  position: relative;
  overflow: hidden;
}

.interactive-header {
  max-width: 850px;
  margin: auto;
  position: relative;
  z-index: 2;
}

.interactive h2 {
  font-size: clamp(43px, 11vw, 78px);
  line-height: .95;
  letter-spacing: -3px;
  margin: 20px 0;
}

.interactive h2 strong {
  display: block;
  color: #65e6b1;
}

.interactive p {
  color: rgba(255,255,255,.6);
  max-width: 550px;
  line-height: 1.6;
}

.orbit {
  width: 310px;
  height: 310px;
  margin: 70px auto 0;
  position: relative;
  border: 1px dashed rgba(101,230,177,.25);
  border-radius: 50%;
}

.orbit::before {
  content: "";
  position: absolute;
  inset: 35px;
  border: 1px dashed rgba(101,230,177,.18);
  border-radius: 50%;
}

.orbit-center {
  position: absolute;
  width: 105px;
  height: 105px;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  border-radius: 50%;
  background: #65e6b1;
  color: #061613;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  box-shadow: 0 0 60px rgba(101,230,177,.18);
}

.orbit-center span {
  font-size: 30px;
  font-weight: 900;
}

.orbit-center small {
  font-size: 7px;
  letter-spacing: 2px;
  font-weight: 900;
}

.orbit-item {
  position: absolute;
  width: 55px;
  height: 55px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  background: #10362e;
  border: 1px solid rgba(101,230,177,.25);
  font-size: 24px;
  animation: orbitFloat 4s infinite ease-in-out;
}

.item-1 {
  top: -25px;
  left: 50%;
  transform: translateX(-50%);
}

.item-2 {
  top: 55px;
  right: -25px;
  animation-delay: 1s;
}

.item-3 {
  bottom: 15px;
  right: 5px;
  animation-delay: 2s;
}

.item-4 {
  bottom: 15px;
  left: 5px;
  animation-delay: 3s;
}

.item-5 {
  top: 55px;
  left: -25px;
  animation-delay: 4s;
}

@keyframes orbitFloat {
  0%, 100% {
    transform: translateY(0);
  }

  50% {
    transform: translateY(-10px);
  }
}


/* BODY */

.body-section {
  background: #f7f9f6;
  max-width: none;
  padding-left: max(24px, calc((100% - 950px) / 2));
  padding-right: max(24px, calc((100% - 950px) / 2));
}

.body-visual {
  height: 450px;
  margin-top: 60px;
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
}

.body-circle {
  position: absolute;
  border: 1px solid #b9d9ca;
  border-radius: 50%;
  animation: pulse 4s infinite ease-in-out;
}

.circle-one {
  width: 270px;
  height: 270px;
}

.circle-two {
  width: 380px;
  height: 380px;
  opacity: .5;
  animation-delay: 1s;
}

@keyframes pulse {
  0%, 100% {
    transform: scale(1);
  }

  50% {
    transform: scale(1.04);
  }
}

.body-symbol {
  font-size: 125px;
  position: relative;
  z-index: 2;
  filter: grayscale(1);
}

.body-label {
  position: absolute;
  padding: 9px 12px;
  border-radius: 30px;
  background: white;
  border: 1px solid #dbe6e0;
  font-size: 9px;
  letter-spacing: 1px;
  font-weight: 800;
  z-index: 3;
}

.body-label span {
  color: #198f68;
  margin-right: 5px;
}

.label-top {
  top: 25px;
  left: 50%;
  transform: translateX(-50%);
}

.label-right {
  right: 0;
  top: 50%;
}

.label-bottom {
  bottom: 25px;
  left: 50%;
  transform: translateX(-50%);
}

.research-note {
  max-width: 700px;
  margin: 20px auto 0;
  padding: 20px;
  display: flex;
  gap: 15px;
  border-radius: 18px;
  background: #eaf5ef;
}

.research-note span {
  font-size: 25px;
}

.research-note p {
  margin: 0;
  color: #5a6b64;
  line-height: 1.6;
  font-size: 13px;
}

.research-note strong {
  color: #163b31;
}


/* EFFECTS */

.effects {
  background: #f7f9f6;
  max-width: none;
  padding-left: max(24px, calc((100% - 950px) / 2));
  padding-right: max(24px, calc((100% - 950px) / 2));
}

.effects h2,
.effects h3 {
  color: #10211e;
}

.effects .lead {
  color: #596963;
}

.effects .section-number {
  color: #dfe9e4;
}

.effects .effect-info span {
  color: #7a8882;
}

.effects .effect-info h3 {
  color: #10211e;
}

.effects .effect p {
  color: #596963;
}

.effects-list {
  margin-top: 45px;
  border-top: 1px solid #dce5df;
}

.effect {
  width: 100%;
  padding: 22px 0;
  display: grid;
  grid-template-columns: 55px 1fr 30px;
  align-items: center;
  text-align: left;
  background: transparent;
  border-bottom: 1px solid #dce5df;
  cursor: pointer;
}

.effect-icon {
  font-size: 26px;
}

.effect-info span {
  color: #8b9993;
  font-size: 9px;
}

.effect-info h3 {
  margin: 5px 0 0;
  font-size: 20px;
}

.effect-arrow {
  color: #198f68;
  font-size: 22px;
}

.effect p {
  grid-column: 2 / 4;
  margin: 15px 0 0;
  color: #687871;
  font-size: 14px;
  line-height: 1.6;
}


/* MYTH */

.myth {
  padding: 90px 24px;
  background: #0b3028;
  color: white;
}

.myth-card {
  max-width: 800px;
  margin: auto;
  padding: 40px 25px;
  border: 1px solid rgba(101,230,177,.2);
  border-radius: 30px;
  text-align: center;
  background: rgba(255,255,255,.025);
}

.myth h2 {
  font-size: clamp(38px, 10vw, 65px);
  line-height: 1;
  letter-spacing: -3px;
  margin: 25px 0 15px;
}

.myth h2 strong {
  color: #65e6b1;
}

.myth-card > p {
  color: rgba(255,255,255,.55);
}

.quiz-buttons {
  display: flex;
  gap: 12px;
  justify-content: center;
  margin-top: 30px;
}

.quiz-buttons button,
.try-again {
  padding: 14px 22px;
  border-radius: 50px;
  cursor: pointer;
  font-weight: 800;
}

.quiz-buttons button:first-child {
  background: #65e6b1;
  color: #061613;
}

.quiz-buttons button:last-child,
.try-again {
  background: transparent;
  border: 1px solid rgba(255,255,255,.25);
  color: white;
}

.result-icon {
  width: 60px;
  height: 60px;
  margin: auto;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  background: #65e6b1;
  color: #061613;
  font-size: 30px;
  font-weight: 900;
}

.quiz-result h3 {
  font-size: 28px;
  margin-bottom: 10px;
}

.quiz-result p {
  max-width: 500px;
  margin: auto auto 25px;
  color: rgba(255,255,255,.65);
  line-height: 1.6;
}


/* PREVENTION */

.prevention {
  background: #f7f9f6;
  max-width: none;
  padding-left: max(24px, calc((100% - 950px) / 2));
  padding-right: max(24px, calc((100% - 950px) / 2));
}

.tips {
  margin-top: 45px;
}

.tip {
  display: flex;
  gap: 20px;
  padding: 25px 0;
  border-bottom: 1px solid #dce5df;
}

.tip > span {
  color: #198f68;
  font-size: 11px;
  font-weight: 900;
}

.tip h3 {
  margin: 0 0 7px;
  font-size: 19px;
}

.tip p {
  margin: 0;
  color: #687871;
  font-size: 14px;
  line-height: 1.5;
}


/* FINAL */

.final {
  min-height: 80vh;
  padding: 100px 24px;
  display: flex;
  align-items: center;
  background:
    radial-gradient(
      circle at 50% 50%,
      #164d40,
      #061613 65%
    );
  color: white;
  text-align: center;
}

.final-content {
  max-width: 800px;
  margin: auto;
}

.final-content > span {
  color: #65e6b1;
  font-size: 10px;
  letter-spacing: 4px;
  font-weight: 900;
}

.final h2 {
  margin: 25px 0;
  font-size: clamp(48px, 13vw, 90px);
  line-height: .9;
  letter-spacing: -4px;
}

.final h2 em {
  display: block;
  color: #65e6b1;
  font-style: normal;
}

.final p {
  max-width: 600px;
  margin: auto;
  color: rgba(255,255,255,.6);
  line-height: 1.7;
}

.back-top {
  display: inline-block;
  margin-top: 35px;
  color: white;
  text-decoration: none;
  font-size: 10px;
  letter-spacing: 2px;
}


/* CRÉDITOS */

.credits {
  padding: 110px 24px 70px;
  background: #071c1a;
  color: #ffffff;
  position: relative;
  overflow: hidden;
}

.credits::before {
  content: "";
  position: absolute;
  width: 350px;
  height: 350px;
  border-radius: 50%;
  background: rgba(101,230,177,.06);
  top: -180px;
  right: -120px;
  filter: blur(10px);
}

.credits-content {
  max-width: 950px;
  margin: auto;
  position: relative;
  z-index: 2;
}

.credits-label {
  display: block;
  color: #65e6b1 !important;
  font-size: 10px;
  letter-spacing: 4px;
  font-weight: 900;
}

.credits h2 {
  margin: 20px 0 15px;
  max-width: 700px;
  font-size: clamp(42px, 10vw, 72px);
  line-height: .95;
  letter-spacing: -3px;
  color: #ffffff !important;
}

.credits h2 strong {
  display: block;
  color: #65e6b1 !important;
}

.credits-intro {
  max-width: 560px;
  color: #c8d5d0 !important;
  line-height: 1.7;
  font-size: 15px;
}

.credits-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 15px;
  margin-top: 50px;
}

.credit-card {
  position: relative;
  padding: 30px 25px;
  min-height: 250px;
  border-radius: 25px;
  background: #0d2924 !important;
  border: 1px solid rgba(101,230,177,.25);
  transition: .3s;
  overflow: hidden;
  color: #ffffff !important;
}

.credit-card:hover {
  transform: translateY(-5px);
  border-color: rgba(101,230,177,.5);
}

.credit-card.developer {
  background: #10352d !important;
}

.credit-number {
  position: absolute;
  top: 20px;
  right: 22px;
  font-size: 11px;
  color: #8fa59d !important;
  font-weight: 900;
}

.credit-icon {
  font-size: 32px;
  margin-bottom: 25px;
}

.credit-role {
  display: block;
  color: #65e6b1 !important;
  font-size: 9px;
  letter-spacing: 2px;
  font-weight: 900;
  margin-bottom: 9px;
}

.credit-card h3 {
  margin: 0;
  font-size: 24px;
  letter-spacing: -1px;
  color: #ffffff !important;
}

.credit-card p {
  max-width: 450px;
  margin: 12px 0 0;
  color: #c8d5d0 !important;
  font-size: 13px;
  line-height: 1.6;
}

.rights {
  margin-top: 65px;
  text-align: center;
}

.rights-line {
  width: 100%;
  height: 1px;
  background: rgba(255,255,255,.2) !important;
  margin-bottom: 25px;
}

.rights p {
  margin: 0 0 8px;
  color: #b8c7c1 !important;
  font-size: 10px;
  letter-spacing: 2px;
}

.rights span {
  color: #8fa59d !important;
  font-size: 8px;
  letter-spacing: 1.5px;
}


/* FOOTER */

footer {
  padding: 30px 24px;
  background: #030c0a;
  color: white;
  text-align: center;
}

footer span {
  color: #65e6b1;
  font-size: 11px;
  letter-spacing: 3px;
  font-weight: 900;
}

footer p {
  margin: 10px 0 0;
  font-size: 11px;
  color: rgba(255,255,255,.35);
}


/* TRANSITIONS */

.fade-enter-active,
.fade-leave-active,
.slide-enter-active,
.slide-leave-active {
  transition: .3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.slide-enter-from,
.slide-leave-to {
  opacity: 0;
  transform: translateY(15px);
}


/* DESKTOP */

@media (min-width: 768px) {
  .section {
    padding-top: 140px;
    padding-bottom: 140px;
  }

  .source-grid {
    grid-template-columns: repeat(4, 1fr);
  }

  .source-card {
    min-height: 250px;
  }

  .myth-card {
    padding: 70px;
  }

  .credits {
    padding-top: 150px;
    padding-bottom: 90px;
  }

  .credits-grid {
    grid-template-columns: 1fr 1fr;
  }

  .credit-card {
    min-height: 280px;
    padding: 35px;
  }
}


/* MOBILE */

@media (max-width: 420px) {
  .hero h1 {
    font-size: 50px;
  }

  .source-grid {
    gap: 8px;
  }

  .source-card {
    min-height: 175px;
    padding: 17px;
  }

  .source-icon {
    font-size: 29px;
  }

  .source-card h3 {
    font-size: 16px;
  }

  .orbit {
    width: 270px;
    height: 270px;
  }

  .circle-two {
    width: 330px;
    height: 330px;
  }

  .credits {
    padding-left: 20px;
    padding-right: 20px;
  }

  .credits h2 {
    letter-spacing: -2px;
  }

  .credit-card {
    padding: 25px 20px;
  }
}
.integrantes-nomes {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.integrantes-nomes span {
  display: block;
}
</style>

