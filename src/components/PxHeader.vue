<template>
  <div class="text-center">
    <b-row class="title">
      <router-link class="mx-auto pt-4" :to="{ name: 'Home' }">
        <h1>Ecuaciones de Chavín</h1>
      </router-link>
    </b-row>
    <b-row>
      <b-col class="left-item">
        <router-link class="mx-auto" :to="{ name: 'Home' }">
          Videos
        </router-link>
      </b-col>
      <b-col class="right-item">
        <div class="dropdown">
          <div class="dropbtn">Actividades</div>
          <div class="dropdown-content">
            <router-link :to="{ name: 'Home' }">Suma libre</router-link>
            <router-link :to="{ name: 'Home' }">Suma en linea</router-link>
            <router-link :to="{ name: 'Home' }">Series numericas</router-link>
            <router-link :to="{ name: 'Home' }">Suma y compara</router-link>
          </div>
        </div>
      </b-col>
    </b-row>
  </div>
</template>
<script>
export default {
  name: 'pxheader'
}
</script>
<style lang="scss" scoped>
// @import url('https://fonts.googleapis.com/css2?family=Open+Sans:ital,wght@0,300;0,400;0,600;0,700;0,800;1,300;1,400;1,600;1,700;1,800&family=Roboto&display=swap');
// font-family: 'Open Sans', sans-serif;
// font-family: 'Roboto', sans-serif;
@import url('https://fonts.googleapis.com/css2?family=Catamaran:wght@800&display=swap');
.title {
  background-color: #68bc45;
  width: 100%;
  height: 120px;
  margin: 0;
  animation-name: header_colores;
  animation-duration: 4s;
  animation-iteration-count: infinite;
}
.title a {
  text-decoration: none;
}
.title h1 {
  color: white;
  text-transform: uppercase;
  font-size: 3em;
}
@keyframes header_colores {
  0% {
    background-color: #68bc45;
  }
  50% {
    background-color: #5cea20;
  }
}
.left-item {
  background-color: #a4a426;
  display: grid;
  place-items: center;
}
.subtitulos {
  font-size: 2em;
  display: inline-block;
  color: white;
  text-align: center;
  text-decoration: none;
  transition: 0.1s;
  width: 100%;
  font-family: 'Catamaran', sans-serif;
  text-transform: uppercase;
}
.left-item a {
  @extend .subtitulos;
}
.left-item:hover {
  background-color: #a3cc3d;
}
.right-item {
  background-color: #ff7200;
  padding: 0;
}
.right-item a {
  @extend .subtitulos;
}
.right-item:hover {
  background-color: #ff933b;
}
.dropbtn {
  background-color: #ff7200;
  font-size: 2em;
  width: 100%;
  height: 72px;
  color: white;
  text-transform: uppercase;
  font-family: 'Catamaran', sans-serif;
  padding: 15px;
}
.dropdown:hover .dropbtn {
  background-color: #ff933b;
}

.dropdown {
  position: relative;
  display: inline-block;
  width: 100%;
  height: 72px;
}

.dropdown-content {
  display: none;
  position: absolute;
  background-color: #ff7200;
  min-width: 160px;
  box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
  z-index: 1;
  width: 100%;
}

.dropdown-content a {
  font-size: 2em;
  display: inline-block;
  color: white;
  text-align: center;
  text-decoration: none;
  transition: 0.1s;
  width: 100%;
  font-family: 'Catamaran', sans-serif;
  text-transform: uppercase;
  display: block;
}

.dropdown-content a:hover {
  background-color: #ff933b;
}

.dropdown:hover .dropdown-content {
  display: block;
}
</style>
