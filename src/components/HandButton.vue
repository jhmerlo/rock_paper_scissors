<template>
  <div v-if="houseChoice">
    <p class="housePicked fadeOut">THE HOUSE PICKED</p>
    <div :class="houseChoiceClass">
      <div class="centralPlayerChoice centralDiv">
        <img style="width: 50%; top: 0" :src="iconUrl" />
      </div>
    </div>
  </div>
  <div v-else :class="stage === 1 || isPlayerChoice ? '' : 'fadeOut'">
    <p :class="isPlayerChoice ? 'youPicked' : 'fadeOut'">YOU PICKED</p>
    <div :class="`${type} handButton ` + selectedClass ">
      <div :class="isPlayerChoice ? 'centralPlayerChoice centralDiv' : 'centralDiv'">
        <img :style="isPlayerChoice ? 'width: 50%; top: 0' : 'top: 0'" :src="iconUrl" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HandButton',
  props: {
    type: {
      type: String
    },
    houseChoice: {
      type: Boolean
    },
    playerChoice: {
      type: String
    },
    stage: {
      type: Number
    }
  },
  data: () => ({}),
  computed: {
    iconUrl () {
      switch (this.type) {
        case 'paper':
          return 'icon-paper.svg'
        case 'scissors':
          return 'icon-scissors.svg'
        default:
          return 'icon-rock.svg'
      }
    },
    isPlayerChoice () {
      return this.type === this.playerChoice
    },
    selectedClass () {
      if (this.isPlayerChoice) return 'playerChoice'
      else if (this.houseChoice) return 'houseChoice'
      else return ''
    },
    houseChoiceClass () {
      if (this.type) return `${this.type} handButton ` + this.selectedClass
      else return 'typePlaceholder handButton ' + this.selectedClass 
    }
  }
}
</script>

<style scoped>
.paper {
  position: absolute;
  transition: all 1s linear;
  top: 0;
  left: 0;
  height: 150px;
  width: 150px;
  border-radius: 50%;
  background: rgb(72,101,244);
  background: radial-gradient(circle, rgba(72,101,244,1) 0%, rgba(86,113,245,1) 120%);
}
.scissors {
  position: absolute;
  transition: all 1s linear;
  top: 0;
  left: 250px;
  height: 150px;
  width: 150px;
  border-radius: 50%;
  background: rgb(236,158,14);
  background: radial-gradient(circle, rgba(236,158,14,1) 0%, rgba(236,169,34,1) 120%);
}
.rock {
  position: absolute;
  transition: all 1s linear;
  left: 30%;
  top: 200px;
  height: 150px;
  width: 150px;
  border-radius: 50%;
  background: rgb(220,46,78);
  background: radial-gradient(circle, rgba(220,46,78,1) 0%, rgba(221,64,93,1) 120%);
}
.typePlaceholder {
  position: absolute;
  transition: all 1s linear;
  left: 30%;
  top: 200px;
  height: 150px;
  width: 150px;
  border-radius: 50%;
  background: lightgrey;
}
.centralDiv {
  box-shadow: inset 0em 0.4em lightgrey;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 120px;
  width: 120px;
  border-radius: 50%;
  background: white;
}
.handButton {
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  user-select: none;
}
.handButton:hover {
  box-shadow: 0px 5px 20px #0d1335;
  transition: 300ms
}
.playerChoice {
  top: 90px;
  left: -200px;
  height: 180px;
  width: 180px;
}
.houseChoice {
  top: 90px;
  left: 400px;
  height: 180px;
  width: 180px;
}
.centralPlayerChoice {
  height: 150px;
  width: 150px;
}
.youPicked { 
  opacity: 1;
  transition: 500ms;
  position: absolute;
  font-weight: 700;
  top: 0px;
  left: -147px;
}
.housePicked { 
  opacity: 1;
  transition: 500ms;
  position: absolute;
  font-weight: 700;
  top: 0px;
  width: 130px;
  left: 430px;
}
</style>