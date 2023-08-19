<template>
  <main>
    <Navbar id="navbar" />

    <div class="consulta-container">
      <h1>CONSULTA</h1>

      <div class="inputs-container">
        <Lixeira @click="clear" v-show="showIcon" style="width: 20px; position: absolute; right: 35rem; color: #7b7b7b; cursor: pointer;" />
        <input @input="lixeira" :disabled="disabled" :value="inputValue" :type="type" v-model="inputValue" :placeholder="placeholder">
        <button type="submit">BUSCAR</button>
      </div>

      <div v-auto-animate class="selection-area">
        <div @click="toggle()" class="select-area">
            <span id="input">{{ spanContent }}</span>
            <DropDown style="width: 20px;" />
        </div>
        <div v-show="show" class="opcoes">
            <span @click="nome">Nome completo</span>
            <span @click="cpf">Cadastro de Pessoa Física (CPF)</span>
            <span @click="numero" class="last">Número de celular</span>
        </div>
      </div>
    </div>
  </main>
</template>

<script setup>
import Navbar from '../components/Navbar.vue'
import DropDown from '../components/icons/DropDown.vue';
import { ref } from 'vue'
import Lixeira from '../components/icons/Lixeira.vue'
import { vAutoAnimate } from '@formkit/auto-animate'


const inputValue = ref('')

const showIcon = ref(false)

const lixeira = (event) => {
      inputValue.value = event.target.value;
      showIcon.value = inputValue.value.length > 0;
    };

const placeholder = ref('Selecione uma forma de consulta')
const spanContent = ref('Selecione uma opção')
const disabled = ref(true)
const type = ref('text')
const maxLenght = ref(40)

const show = ref(false)
const toggle = () => (show.value = !show.value)

const nome = () => {
    spanContent.value = 'Nome completo'
    show.value = false
    placeholder.value = 'Digite o nome completo'
    disabled.value = false
    maxLenght.value = 40
    inputValue.value = ''
    showIcon.value = false
}
const cpf = () => {
    spanContent.value = 'Cadastro de Pessoa Física (CPF)'
    show.value = false
    placeholder.value = 'Digite o número do CPF'
    disabled.value = false
    maxLenght.value = 11
    inputValue.value = ''
    showIcon.value = false
}
const numero = () => {
    spanContent.value = 'Número de celular'
    show.value = false
    placeholder.value = 'Digite o número do celular'
    disabled.value = false
    maxLenght.value = 11
    inputValue.value = ''
    showIcon.value = false
}
const clear = () => {
  inputValue.value = ''
  showIcon.value = false
}
</script>

<style scoped lang="scss">
main{
    background-color: #151515;
    height: 100vh;
    width: 100vw;
    padding-top: 1rem;
    align-items: center;
    display: flex;
    flex-direction: column;
    gap: 5rem;
    font-family: 'Inter';
    color: #FFF;
  }
.consulta-container{
  display: flex;
  flex-direction: column;
  align-items: center;
  position: relative;
  .inputs-container{
    display: flex;
    align-items: center;
    gap: 1rem;
    margin-top: 1rem;
    input{
      width: 398px;
      height: 52px;
      border-radius: 6px;
      background-color: #1e1e1e;
      border: none;
      padding: 15px 20px;
      color: #fff;
      font-size: 16px;
      font-family: 'Inter';
      outline: none;
    }
    button{
      padding: 12px 16px;
      height: 52px;
      border-radius: 6px;
      color: #FFF;
      background-color: #3427C8;
      border: none;
      font-family: 'Inter';
      font-weight: 500;
      cursor: pointer
    }
  }
  .selection-container{
    margin-top: 1rem;
    .options{
      background-color: #1e1e1e;
      width: 400px;
      height: 50px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      border-radius: 6px;
      padding: 10px 15px;
      color: #7b7b7b
    }
  }
}
.select-area {
  height: 3.5em;
  width: 29em;
  color: #7b7b7b;
  background-color: #1e1e1e;
  border-radius: 6px;
  position: relative;
  cursor: pointer;
  padding: 1em 2em;
  justify-content: space-between;
  display: flex;
  align-items: center;
}
.selection-area {
  display: flex;
  flex-direction: column;
  gap: 1em;
  transition: all ease-out 0.1s;
  margin-top: 1rem;
  position: relative;
}

.opcoes {
  height: 9em;
  width: 29em;
  background-color: #1e1e1e;
  color: #CCC;
  padding: 1em 2em;
  display: flex;
  flex-direction: column;
  border-radius: 6px;
  gap: 0.1em;
  position: absolute;
  top: 4rem
}

.opcoes span {
  padding: 0.5em 0.5em;
  width: 100%;
  border-radius: 6px;
  transition: 0.2s ease-in all;
  color: #7b7b7b
}
.selection-area span{
  transition: all linear 0.1s;
}
.opcoes span:hover {
  background-color: #151515;
  cursor: pointer;
}

@media screen and (max-width: 748px){
  main{
    justify-content: center
  }
  #navbar{
    position: absolute;
    top: 58rem
  }
  .consulta-container{
    bottom: 10rem
  }
}
</style>