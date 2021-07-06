<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-toolbar-title class="text-center">
          Disclaimer: Everything here is a labor of love and <strong>parody</strong>. We do not claim to own Heathstone, nor the art present. All assets and concepts are used in accordance with Fair Use.
        </q-toolbar-title>
      </q-toolbar>
    </q-header>
    <q-card>
        <q-img
          class="no-shadow col-1 q-mt-xl"
          fit="scale-down"
          style="height: 300px;"
          alt="card image"
          src="Logo-Cropped.png"
        />
    </q-card>
    <q-page-container style="margin-top: -50px;">
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from 'vue'

export default defineComponent({
  name: 'MainLayout',
  setup () {
    return {
      slide: ref('first')
    }
  }
})
</script>

<style lang="sass">
.custom-caption
  text-align: center
  padding: 12px
  color: white
  background-color: rgba(0, 0, 0, .3)

.big-explain-name
  font-size: 32px
</style>
