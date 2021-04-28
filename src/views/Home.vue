<template>
  <article id="contenido_recurso">
    <section id="section_video">
      <h2>Suma en línea</h2>
      <section id="suma_libre">
        <div
          class="fila_circulo"
          v-for="(numero, index) in numRandom"
          :key="numero.id"
          :id="numero.id"
        >
          <div v-if="numero.id % 2 == 0" class="circulo">
            {{ numero.numero1 }}
          </div>
          <div v-else class="circulo">
            <input
              v-model="respuesta['suma' + index]"
              class="text_circulo"
              type="text"
              name=""
            />
          </div>
          <div class="mas">+</div>
          <div v-if="numero.id % 2 != 0" class="circulo">
            {{ numero.numero2 }}
          </div>
          <div v-else class="circulo">
            <input
              v-model="respuesta['suma' + index]"
              class="text_circulo"
              type="text"
              name=""
            />
          </div>
          <div class="igual">=</div>
          <div class="circulo">{{ numero.total }}</div>
        </div>
      </section>
    </section>
  </article>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'Home',
  data () {
    return {
      // operacion: [
      //   {
      //     total: 15,
      //     numero1: 10,
      //     numero2: ''
      //   },
      //   {
      //     total: 20,
      //     numero2: 6,
      //     numero1: ''
      //   },
      //   {
      //     total: 14,
      //     numero1: 2,
      //     numero2: ''
      //   },
      //   {
      //     total: 13,
      //     numero2: 7,
      //     numero1: ''
      //   },
      //   {
      //     total: 8,
      //     numero1: 4,
      //     numero2: ''
      //   }
      // ],
      numRandom: [],
      respuesta: {},
      isCorrect: true,
      isError: false
    }
  },
  watch: {
    respuesta: {
      handler (newValue, oldValue) {
        const valores = Object.values(newValue)
        const operaciones = [...this.numRandom]
        for (let i = 0; i < valores.length; i++) {
          if (i % 2 !== 0) {
            // console.log(operaciones[i].numero1)
            if (operaciones[i].numero1 === parseInt(valores[i])) {
              // console.log('correcto', operaciones[i].numero1, valores[i])
              this.playSuccess()
              const element = document.getElementById(i)
              // console.log(element)
              element.classList.add('correcto')
            } else {
              // console.log('fallaste', operaciones[i].numero1, valores[i])
              this.playError()
              const element = document.getElementById(i)
              element.classList.add('incorrecto')
              // console.log(element)
            }
          } else {
            // console.log(operaciones[i].numero2)
            if (operaciones[i].numero2 === parseInt(valores[i])) {
              // console.log('correcto', operaciones[i].numero2, valores[i])
              this.playSuccess()
              const element = document.getElementById(i)
              element.classList.add('correcto')
              // console.log(element)
            } else {
              // console.log('fallaste', operaciones[i].numero2, valores[i])
              this.playError()
              const element = document.getElementById(i)
              // console.log(element)
              element.classList.add('incorrecto')
            }
          }
        }
      }
    }
  },
  methods: {
    playSuccess () {
      var audio = new Audio(require('../assets/audio/correcto.mp3')) // path to file
      audio.play()
    },
    playError () {
      var audio = new Audio(require('../assets/audio/error.mp3')) // path to file
      audio.play()
    }
    // setBackgroundSuccess () {
    //   return 'correcto'
    // },
    // setBackgroundError () {
    //   return 'incorrecto'
    // }
  },
  created () {
    function getRandomInt (min, max) {
      return Math.floor(Math.random() * (max - min)) + min
    }
    // console.log(Math.floor(Math.random() * (20 - 2)) + 2)
    for (let index = 0; index < 4; index++) {
      const total = getRandomInt(2, 21)
      // this.numRandom.push(getRandomInt(2, 20))
      const numero1 = getRandomInt(1, total)
      const newObj = {
        id: index,
        total,
        numero1,
        numero2: total - numero1
      }
      this.numRandom.push(newObj)
    }
  }
}
</script>

<style lang="scss" scoped>
#section_video,
#section_preguntas {
  width: 100%;
  text-align: center;
  margin-top: 16px;
  padding-top: 8px;
  display: grid;
  place-items: center;
}
#section_video video {
  width: 800px;
  height: 400px;
  text-align: center;
}
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

.correcto {
  background-color: lightgreen;
}

.incorrecto {
  background-color: red;
}
</style>
