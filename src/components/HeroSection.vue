<script setup>
const scrollToNext = () => {
  document
    .getElementById('o-que-sao')
    ?.scrollIntoView({
      behavior: 'smooth'
    })
}
</script>

<template>

  <section class="hero">

    <!-- partículas -->
    <div class="particle particle-1"></div>
    <div class="particle particle-2"></div>
    <div class="particle particle-3"></div>
    <div class="particle particle-4"></div>
    <div class="particle particle-5"></div>

    <div class="hero-content">

      <span class="tag">
        MICROPLÁSTICOS
      </span>

      <h1>
        Você já comeu
        <strong>plástico</strong>
        hoje?
      </h1>

      <p>
        Existe um mundo invisível ao nosso redor.
        E talvez você esteja ingerindo pequenas partes dele.
      </p>

      <button @click="scrollToNext">
        Descobrir
        <span>↓</span>
      </button>

    </div>

    <div class="scroll">
      role para descobrir
    </div>

  </section>

</template>

<style scoped>

.hero {

  min-height: 100vh;

  position: relative;

  overflow: hidden;

  display: flex;

  justify-content: center;

  align-items: center;

  padding: 30px;

  background:
    radial-gradient(
      circle at 50% 30%,
      #123d35,
      #061613 65%
    );

  color: white;

}

/* conteúdo */

.hero-content {

  max-width: 650px;

  text-align: center;

  position: relative;

  z-index: 2;

}

.tag {

  display: inline-block;

  font-size: 11px;

  letter-spacing: 4px;

  color: #65e6b1;

  margin-bottom: 25px;

}

h1 {

  margin: 0;

  font-size: clamp(
    48px,
    13vw,
    90px
  );

  line-height: 0.95;

  letter-spacing: -3px;

}

h1 strong {

  display: block;

  color: #65e6b1;

}

p {

  max-width: 520px;

  margin: 30px auto 0;

  font-size: 18px;

  line-height: 1.6;

  color: rgba(
    255,
    255,
    255,
    0.7
  );

}

/* botão */

button {

  margin-top: 35px;

  padding: 17px 30px;

  border: none;

  border-radius: 100px;

  background: #65e6b1;

  color: #061613;

  font-size: 16px;

  font-weight: bold;

  cursor: pointer;

  transition: all 0.3s ease;

}

button:hover {

  transform: translateY(-4px);

  box-shadow:
    0 10px 30px
    rgba(101, 230, 177, 0.25);

}

button span {

  margin-left: 10px;

}

/* partículas */

.particle {

  width: 7px;

  height: 7px;

  border-radius: 50%;

  background: #65e6b1;

  position: absolute;

  opacity: 0.4;

  animation:
    float 6s infinite ease-in-out;

}

.particle-1 {

  top: 15%;

  left: 15%;

}

.particle-2 {

  top: 25%;

  right: 18%;

  animation-delay: 1s;

}

.particle-3 {

  bottom: 25%;

  left: 20%;

  animation-delay: 2s;

}

.particle-4 {

  bottom: 15%;

  right: 15%;

  animation-delay: 3s;

}

.particle-5 {

  top: 50%;

  right: 5%;

  animation-delay: 4s;

}

/* animação */

@keyframes float {

  0%,
  100% {

    transform:
      translateY(0)
      scale(1);

  }

  50% {

    transform:
      translateY(-25px)
      scale(1.4);

  }

}

/* indicador */

.scroll {

  position: absolute;
                                                            
  bottom: 25px;

  font-size: 10px;

  letter-spacing: 2px;

  opacity: 0.3;

}

</style>