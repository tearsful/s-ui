<template>
  <v-app style="overflow: auto;">
    <drawer :isMobile="isMobile" :displayDrawer="displayDrawer" @toggleDrawer="toggleDrawer" />
    <default-bar :isMobile="isMobile" @toggleDrawer="toggleDrawer" />
    <default-view />
  </v-app>
</template>

<script lang="ts" setup>
import { computed, ref } from 'vue'
import DefaultBar from './AppBar.vue'
import Drawer from './Drawer.vue'
import DefaultView from './View.vue'
import { useDisplay } from 'vuetify'

const { smAndDown } = useDisplay()
const displayDrawer = ref(false)

const toggleDrawer = () => {
  displayDrawer.value = !displayDrawer.value
}

const isMobile = computed( ():boolean =>{
  displayDrawer.value = !smAndDown.value
  return smAndDown.value
})
</script>
