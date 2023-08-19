<template>
  <main>
    
    <div class="form-container">
      <h1>B7 TECHNOLOGY</h1>
      <div class="input-container">

        <div class="input-usuario">
          <input type="text" id="inputSenha" placeholder="Digite seu usuário">
          <User style="width: 40px; color: #c6c6c6; position: absolute; top: 16px; left: 24px; cursor: pointer" />
        </div>

        <div class="input-senha">
          <input :type="inputSenha" id="inputSenha" placeholder="Digite sua senha">
          <FingerPrint style="width: 40px; color: #c6c6c6; position: absolute; top: 16px; left: 24px; cursor: pointer" />
          <Eye @click="TogglePass" v-show="!Toggle" class="showPass" style="width: 34px; color: #c6c6c6; position: absolute; top: 18px; right: 24px; cursor: pointer" />
          <EyeSlash @click="TogglePass" v-show="Toggle"  class="hidePass" style="width: 34px; color: #c6c6c6; position: absolute; top: 18px; right: 24px; cursor: pointer" />
        </div>

      </div>
      <span>Ainda não tem uma conta? <a href="#">converse com um admin</a></span>
      <div class="button-container">
        <router-link to="/central">
          <button type="submit">
            Entrar
          </button>
        </router-link>
      </div>
    </div>

  </main>
</template>

<script setup>
import FingerPrint from '../components/icons/FingerPrint.vue'
import User from '../components/icons/User.vue'
import Eye from '../components/icons/Eye.vue'
import EyeSlash from '../components/icons/EyeSlash.vue'

import {ref, computed} from 'vue'

const Toggle = ref(true)

const inputSenha = computed(()=> ( Toggle.value == true ? 'password' : 'text'))
const TogglePass = (() => Toggle.value = ! Toggle.value)

</script>

<style scoped lang="scss">

main{
  height: 100vh;
  width: 100vw;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  font-family: 'Inter';
  background-image: linear-gradient( to bottom, #151515, rgba(0, 0, 0, 0.9))
}

.form-container{
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 26px;
  span{
    font-size: 16px;
    font-weight: 300;
    color: rgba(255, 255, 255, 0.2)
  }
  a{
    opacity: 1;
    color: #fff;
    text-decoration: none;
  }
  h1{
    font-family: 'montserrat';
    font-size: 45px;
    color: #FFF;
  }
}
.input-container{
  display: flex;
  flex-direction: column;
  gap: 26px;
  .input-senha{
    position: relative;
    input{
      width: 474px;
      height: 74px;
      border-radius: 6px;
      border: none;
      outline: none;
      padding: 18px 96px;
      color: #7b7b7b;
      font-family: 'Montserrat';
      font-size: 20px;
    }
    input::placeholder{
      color: #7b7b7b;
      font-size: 20px;
      letter-spacing: 1px
    }
  }
  .input-usuario{
    position: relative;
    input{
      width: 474px;
      height: 74px;
      border-radius: 6px;
      border: none;
      outline: none;
      padding: 18px 96px;
      color: #7b7b7b;
      font-family: 'Montserrat';
      font-size: 20px;
    }
    input::placeholder{
      color: #7b7b7b;
      font-size: 20px;
      letter-spacing: 1px
    }
  }
}
.button-container button{
  background-color: #3427C8;
  border: none;
  cursor: pointer;
  color: #FFF;
  width: 474px;
  height: 74px;
  border-radius: 6px;
  font-size: 20px;
  font-family: 'Montserrat';
  font-weight: 500;
  transition: all ease-in 0.1s;
}
.button-container button:hover{
  background-color: #2619b5
}
</style>