<template>
  <article id="contenido_recurso">
    <section id="section_video">
      <h2>Suma en línea</h2>
      <section id="suma_libre">
        <div
          class="fila_circulo"
          v-for="numero in numRandom"
          :key="numero.id"
          :id="numero.id"
        >
          <FilaSuma :number="numero"/>
        </div>
      </section>
    </section>
  </article>
</template>

<script>
// @ is an alias to /src
import FilaSuma from '@/components/FilaSuma'
export default {
  name: 'Home',
  components: {
    FilaSuma
  },
  data () {
    return {
      numRandom: [],
      respuesta: {},
      isCorrect: true,
      isError: false
    }
  },
  watch: {
  },
  created () {
    function getRandomInt (min, max) {
      return Math.floor(Math.random() * (max - min)) + min
    }
    for (let index = 0; index < 4; index++) {
      const total = getRandomInt(2, 21)
      const numero1 = getRandomInt(1, total)
      const newObj = {
        id: index,
        total,
        numero1,
        numero2: total - numero1
      }
      this.numRandom.push(newObj)
    }
  },
  methods: {

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
  width: 100%;
  display: flex;
  flex-direction: row;
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
