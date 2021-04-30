<template>
  <div>
    <div v-if="number.id % 2 == 0" class="circulo">
      {{ number.numero1 }}
    </div>
    <div v-else class="circulo">
      <input
        v-model="number1"
        class="text_circulo"
        type="text"
        name=""
      />
    </div>
    <div class="mas">+</div>
    <div v-if="number.id % 2 != 0" class="circulo">
      {{ number.numero2 }}
    </div>
    <div v-else class="circulo">
      <input
        v-model="number2"
        class="text_circulo"
        type="text"
        name=""
      />
    </div>
    <div class="igual">=</div>
    <div class="circulo">
      {{ number.total }}
    </div>
      <svg v-if="isSuccess" xmlns="http://www.w3.org/2000/svg" width="48" height="48" fill="blue" class="bi bi-check-circle" viewBox="0 0 16 16">
        <path d="M8 15A7 7 0 1 1 8 1a7 7 0 0 1 0 14zm0 1A8 8 0 1 0 8 0a8 8 0 0 0 0 16z"/>
        <path d="M10.97 4.97a.235.235 0 0 0-.02.022L7.477 9.417 5.384 7.323a.75.75 0 0 0-1.06 1.06L6.97 11.03a.75.75 0 0 0 1.079-.02l3.992-4.99a.75.75 0 0 0-1.071-1.05z"/>
      </svg>
      <svg v-if="isError" xmlns="http://www.w3.org/2000/svg" width="48" height="48" fill="red" class="bi bi-x-circle" viewBox="0 0 16 16">
        <path d="M8 15A7 7 0 1 1 8 1a7 7 0 0 1 0 14zm0 1A8 8 0 1 0 8 0a8 8 0 0 0 0 16z"/>
        <path d="M4.646 4.646a.5.5 0 0 1 .708 0L8 7.293l2.646-2.647a.5.5 0 0 1 .708.708L8.707 8l2.647 2.646a.5.5 0 0 1-.708.708L8 8.707l-2.646 2.647a.5.5 0 0 1-.708-.708L7.293 8 4.646 5.354a.5.5 0 0 1 0-.708z"/>
      </svg>
  </div>
</template>
<script>
// import _, { debounce } from 'lodash'
import _ from 'lodash'
export default {
  name: 'FilaSuma',
  props: {
    number: {
      required: true,
      type: Object
    }
  },
  data () {
    return {
      number1: '',
      number2: '',
      isError: false,
      isSuccess: false
    }
  },
  watch: {
    number1: _.debounce(function (newNumber1) {
      this.number.numero1 === parseInt(newNumber1)
        ? this.playSuccess()
        : this.playError()
    }, 500),
    number2: _.debounce(function (newNumber2) {
      this.number.numero2 === parseInt(newNumber2)
        ? this.playSuccess()
        : this.playError()
    }, 500)
  },
  methods: {
    playSuccess () {
      var audio = new Audio(require('../assets/audio/correcto.mp3')) // path to file
      audio.play()
      this.isSuccess = true
      this.isError = false
    },
    playError () {
      var audio = new Audio(require('../assets/audio/error.mp3')) // path to file
      audio.play()
      this.isError = true
      this.isSuccess = false
    }
  }
}
</script>
<style lang="scss" scoped>
.fila_circulo {
  margin: 15px 0;
}

.circulo,
.mas,
.igual {
  display: inline-block;
  height: 70px;
  width: 70px;
  font-size: 2.5em;
}

.circulo {
  background-color: #ff5a00;
  border-radius: 50%;
  color: #fff;
  margin: 0 5px;
}

.text_circulo {
  height: 60px;
  width: 60px;
  border-radius: 50%;
  text-align: center;
  margin-top: 5px;
  font-size: 1em;
  font-family: 'Catamaran', sans-serif;
  border: 0;
}

.circulo_pequeno {
  display: inline-block;
  height: 40px;
  width: 40px;
  font-size: 1.5em;
  background-color: #ae4200;
  border-radius: 50%;
  color: #fff;
}

.validate-icons {
  display: flex;
  flex-direction: row;
}
</style>
