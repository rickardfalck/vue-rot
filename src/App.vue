<template>
  
  <side-menu :width="200" :top="0"/>
  <router-view/>
</template>

<script>
import SideMenu from '@/components/SideMenu.vue'


export default {
  name: 'Home',
  components: {
    SideMenu
  }
}

</script>


<style>

html,
body,
#app {
  height: 100%;
  width: 100%;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  
  text-align: center;
  color: #2c3e50;
}

.navigationicon {
  height: 24px;
  width: 24px;
  fill: #FFFFFF;
}

</style>
