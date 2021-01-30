<template>
  <div class="card">
    <div>
      <img src="../assets/logo.svg" class="appBrand" />
    </div>
    <div @click="score++" class="scoreCard">
      <div class="title">Score</div>
      <div class="pontuation">{{ this.score }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ScoreCard',
  props: {
    value: {
      type: Number,
      required: true
    }
  },
  computed: {
    score: {
      get () {
        return this.value
      },
      set (val) {
        this.$emit('input', val)
      } 
    }
  }
}
</script>

<style scoped>
.card {
  max-width: 1000px;
  display: flex;
  margin: 0 auto;
  justify-content: space-between;
  align-items: center;
  width: 50%;
  border: 0.3em solid #606e85;
  border-radius: 0.8em;
  padding: 1.5em;
  user-select: none;
}
.appBrand {
  margin-top: 7px;
}
.scoreCard {
  text-align: center;
  background: white;
  border-radius: 0.5em;
  padding: 1em 2em;
}
.scoreCard .title {
  letter-spacing: 0.4em;
  text-transform: uppercase;
  font-size: 0.8em;
  color: #2a46c0;
}
.scoreCard .pontuation {
  font-size: 3em;
  font-weight: 700;
  color: #3b4363;
}

/* Responsive */
@media screen and (max-width: 600px) {
  .card {
    width: 80%;
  }
  .scoreCard {
    padding: 0.5em 1em;
  } 
  .appBrand {
    max-width: 130px;
    margin-top: 10px;
  }
}
</style>
