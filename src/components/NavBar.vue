<template>

<header class="header">
  <nav class="navbar">
<h2 class="brand">
  UniVUE
</h2>

<button class="btn__abrir-menu" aria-label="abrir ou fechar menu" @click="aberto = !aberto">
  <img src="https://img.icons8.com/ios-filled/ffffff/50/menu--v6.png" alt="menu hamburguer" class="icone__menu" />
</button>


<ul class="menu" :class="{ aberto }">
  <li v-for="link in links" :key="link.id">
    <a :href="link.url" @click="" class="link">{{link.label}}</a>
  </li>
</ul>

</nav>

</header>
<HeroUniv/>

</template>


<script setup lang="ts">
import { ref } from 'vue';
import HeroUniv from './HeroUniv.vue';

const aberto = ref(false);

const links = [
{
  id: 1,
  url: "#",
  label: "home"
},
{
  id: 2,
  url: "#",
  label: "serviços"
},
{
  id: 3,
  url: "#",
  label: "portfolio"
},
{
  id: 4,
  url: "#",
  label: "cadastre-se"
},
]

</script>


<style>

*{
padding: 0;
margin: 0;
box-sizing: border-box;
}

.container{
margin: 0 auto;
max-width: 992px;
padding: 0 1rem;
}

.header{
background-color: #9f0712;
color: white;
position: fixed;
width: 100%;
box-shadow: 0 0 6px #00000050;
padding: .5rem 0;
}

.navbar{
display: flex;
justify-content: space-between;
padding: 0 1rem;
margin: 0 auto;
max-width: 992px;
}

li {
list-style: none;
}

.btn__abrir-menu {
border: 0;
background-color: transparent;
cursor: pointer;
}

.menu {
display: none;
}

.menu.aberto {
background-color: #f2f2f2;
padding: 3rem 1rem;
display: flex;
flex-direction: column;
gap: .7rem;
width: 100%;
min-height: 100vh;
position: absolute;
top: 100%;
left: 0;
z-index: 10;
}

.icone__menu {
width: 30px;
}

li:nth-last-child(1){
border-radius: 8px;
background-color: orange;
padding: 5px 1rem;
width: fit-content;

}

li:nth-last-child(1) a{
text-transform: uppercase;
font-size: 13px;
font-weight: bold;
color: white;
width: fit-content;

}

.link{
text-decoration: none;
text-transform: capitalize;
color: #9f0712;
}


@media (min-width:568px) {

.btn__abrir-menu{
  display: none;
}

.menu,
.menu.aberto {
  min-height: 100%;
  display: flex;
  align-items: center;
  flex-direction: row;
  gap: 30px;
  position: static;
  padding: 0;
  background-color: #9f0712;
  justify-content: end;
}
.link{
color: white;
}
}
</style>
