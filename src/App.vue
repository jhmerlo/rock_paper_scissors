<template>
  <div id="app">
    <!-- Placar -->
    <score-card v-model="score" />

    <div class="triangle">
      
      <!-- Background do Triângulo -->
      <img
        :class="!playerChoice ? '' : 'fadeOut'"
        src="./assets/bg-triangle.svg"
      />

      <!-- Botões da Primeira Etapa -->
      <hand-button
        @click.native="stage === 1 ? handleSelection('paper') : ''"
        :player-choice="playerChoice"
        :stage="stage"
        type="paper"
      />
      <hand-button
        @click.native="stage === 1 ? handleSelection('scissors') : ''"
        :player-choice="playerChoice"
        :stage="stage"
        type="scissors"
      />
      <hand-button
        @click.native="stage === 1 ? handleSelection('rock') : ''"
        :player-choice="playerChoice"
        :stage="stage"
        type="rock"
      />

      <!-- Escolha do Computador -->
      <hand-button
        :class="houseChoice ? 'fadeIn' : 'fadeOut'"
        :stage="stage"
        :type="houseChoice"
        house-choice
      />

      <j-button
        v-if="stage === 2"
      />

    </div>

  </div>
</template>

<script>
import ScoreCard from './components/ScoreCard.vue'
import HandButton from './components/HandButton.vue'
import JButton from './components/JButton.vue'
export default {
  name: 'App',
  components: {
    ScoreCard,
    HandButton,
    JButton
  },
  data: () => ({
    score: 0,
    stage: 1,
    playerChoice: '',
    houseChoice: '',
    types: ['paper', 'scissors', 'rock']
  }),
  methods: {
    handleSelection (type) {
      this.playerChoice = type
      this.stage = 2
      setTimeout(() => {
        const randomElement = this.types[Math.floor(Math.random() * this.types.length)]
        this.houseChoice = randomElement
      }, 2000)
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Barlow+Semi+Condensed:wght@600;700&display=swap');
html {
  background: rgb(31,55,86);
  background: radial-gradient(circle, rgba(31,55,86,1) 0%, rgba(20,21,57,1) 120%);
}
.triangle {
  position: relative;
  margin: 0 auto;
  width: 380px;
  max-width: 100%;
  top: 3em;
  text-align: center;
}
.triangle img {
  position: relative;
  top: 4em;
}
.fadeOut {
  opacity: 0;
  transition: 300ms;
}
.fadeIn {
  opacity: 1;
  transition: 300ms;
}
#app {
  font-family: 'Barlow Semi Condensed', sans-serif;
  color: white;
  padding: 3em 0;
}
</style>
