<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-toolbar-title class="text-center">
          Disclaimer: Everything here is a labor of love and <strong>parody</strong>. We do not claim to own Heathstone, nor the art present. All assets and concepts are used in accordance with Fair Use.
        </q-toolbar-title>
      </q-toolbar>
    </q-header>
    <q-carousel
        arrows
        class="q-mt-xl"
        animated
        autoplay="7000"
        v-model="slide"
        height="400px"
     >
        <q-carousel-slide name="first">
          <q-img crossorigin="use-credentials" class="absolute-top" fit="contain" height="400px" src="https://cdn.discordapp.com/attachments/747284270095007776/860409321920528424/Logo-Cropped.png" />
          <div class="absolute-bottom custom-caption">
            <div class="text-h2 text-white">"We put the pirate in Corpirate."</div>
            <div class="text-subtitle1 text-white">-J.D. Blackfoot</div>
          </div>
        </q-carousel-slide>
        <q-carousel-slide name="second">
          <q-img crossorigin="use-credentials" class="absolute-top" fit="contain" height="400px" src="https://cdn.discordapp.com/attachments/747284270095007776/860409321920528424/Logo-Cropped.png" />
          <div class="absolute-bottom custom-caption">
            <div class="text-h2">"This is a placeholder"</div>
            <div class="text-subtitle1">-Aedam Edinson</div>
          </div>
        </q-carousel-slide>
        <q-carousel-slide name="third">
         <q-img crossorigin="use-credentials" class="absolute-top" fit="contain" height="400px" src="https://cdn.discordapp.com/attachments/747284270095007776/860409321920528424/Logo-Cropped.png" />
          <div class="absolute-bottom custom-caption">
            <div class="text-h2">"What's a placeholder"</div>
            <div class="text-subtitle1">-Thóra Lindborg</div>
          </div>
        </q-carousel-slide>
      </q-carousel>
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
