<template>
  <main>
    <Navbar id="navbar" />
    <section>
      <Card />
    </section>
  </main>
</template>

<script setup>
import Navbar from '../components/Navbar.vue'
import Card from '../components/Card.vue'
import { ref } from 'vue'
</script>

<style scoped>
main {
  background-color: #151515;
  height: 100vh;
  width: 100vw;
  padding-top: 1rem;
  align-items: center;
  display: flex;
  flex-direction: column;
}
section{
  display: flex;
  flex-wrap: wrap;
  margin-top: 8rem;
  gap: 30px;
  font-family: 'Inter'
}
@media screen and (max-width: 748px){
  main{
    justify-content: center;
  }
  #navbar{
    position: absolute;
    top: 58rem
  }
  
}
</style>