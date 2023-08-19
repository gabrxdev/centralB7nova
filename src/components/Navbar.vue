<template>
 <nav :id="id">
  <router-link to="/central"> <Dashboard style="width: 26px;" /> </router-link>
  <router-link to="/consulta"> <Search style="width: 26px;" /> </router-link>
  <router-link to="/"> <DropDown style="width: 26px;" /> </router-link>
  <router-link to="/"> <Group style="width: 26px;" /> </router-link>
  <router-link to="/"> <Settings style="width: 26px;" /> </router-link> 
 </nav>
</template>

<script setup>
import Dashboard from '../components/icons/Dahshboard.vue'
import Search from '../components/icons/Search.vue'
import DropDown from '../components/icons/DropDown.vue'
import Group from '../components/icons/Group.vue'
import Settings from '../components/icons/Settings.vue'
defineProps({
    id: String
})
</script>

<style scoped lang="scss">
nav{
    display: flex;
    gap: 62px;
    background-color: #1e1e1e;
    width: 572px;
    height: 74px;
    align-items: center;
    justify-content: center;
    border-radius: 25px;
    a{
        color: #7b7b7b
    }
    a.router-link-active{
        color: #7568fc
    }
}
</style>
