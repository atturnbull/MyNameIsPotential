<template>
  <q-expansion-item
    class="text-white"
    header-class="q-pa-xl text-h4"
    v-bind:style="{ 'background-color': activeColor, 'color': 'white' }"
    :label="name"
    :caption="subtitle"
    dark
    expand-icon-class="text-white"
  >
    <q-card class="text-black column text-white card-background">
      <div class="text-center q-pa-md">
        <p>;poqwndofnowqenefosdafnosadfoasdnfoiuwbqihebrijubqwiub
        rikewqbiourbikqwebriwqbrhwqevriuhyvweqikyfhbsdovjxzcop
        vuxczvjcxznkm;v eikr'bquwe[rhioew[qhr90832u483821y498g
        h321i4 231i9nr0-sdjhv08gxhaz97v9p4b1230948hr897dgsv890
        xczhvnqjkp23bn54u9p1j328v9pndsaob354v1p0jfdiosqa[p908g
        h321iyh4h5 321-9r7ghedfg89hsda803IJPSAF9SAFBEASD9]]]</p>
        <p>;poqwndofnowqenefosdafnosadfoasdnfoiuwbqihebrijubqwiub
        rikewqbiourbikqwebriwqbrhwqevriuhyvweqikyfhbsdovjxzcop
        vuxczvjcxznkm;v eikr'bquwe[rhioew[qhr90832u483821y498g
        h321i4 231i9nr0-sdjhv08gxhaz97v9p4b1230948hr897dgsv890
        xczhvnqjkp23bn54u9p1j328v9pndsaob354v1p0jfdiosqa[p908g
        h321iyh4h5 321-9r7ghedfg89hsda803IJPSAF9SAFBEASD9]]]</p>
        <p>;poqwndofnowqenefosdafnosadfoasdnfoiuwbqihebrijubqwiub
        rikewqbiourbikqwebriwqbrhwqevriuhyvweqikyfhbsdovjxzcop
        vuxczvjcxznkm;v eikr'bquwe[rhioew[qhr90832u483821y498g
        h321i4 231i9nr0-sdjhv08gxhaz97v9p4b1230948hr897dgsv890
        xczhvnqjkp23bn54u9p1j328v9pndsaob354v1p0jfdiosqa[p908g
        h321iyh4h5 321-9r7ghedfg89hsda803IJPSAF9SAFBEASD9]]]</p>
        <p>;poqwndofnowqenefosdafnosadfoasdnfoiuwbqihebrijubqwiub
        rikewqbiourbikqwebriwqbrhwqevriuhyvweqikyfhbsdovjxzcop
        vuxczvjcxznkm;v eikr'bquwe[rhioew[qhr90832u483821y498g
        h321i4 231i9nr0-sdjhv08gxhaz97v9p4b1230948hr897dgsv890
        xczhvnqjkp23bn54u9p1j328v9pndsaob354v1p0jfdiosqa[p908g
        h321iyh4h5 321-9r7ghedfg89hsda803IJPSAF9SAFBEASD9]]]</p>
      </div>
      <q-card-section v-if="deck.length > 0" class="text-center pop-text">
        Top Performers:
      </q-card-section>
      <q-card-section class="row justify-around">
        <q-img
          class="no-shadow col-1 bighover"
          fit="scale-down"
          style="height: 200px;"
          loading="lazy"
          alt="card image"
          :src="item.imageUrl"
          v-for="(item, index) in deck.slice(0, 5)"
          @click="$router.push('/decks?name='+name.toLowerCase())"
          :key="index"
        />
      </q-card-section>
      <q-card-section class="flex flex-center q-pt-md">
        <q-btn no-caps size="xl" type="a" color="secondary" label="Meet the team!" :to="'decks?name='+name.toLowerCase()"/>
      </q-card-section>
    </q-card>
  </q-expansion-item>
</template>

<script>
export default {
  name: 'lite-gallery',
  setup () {
    return {
    }
  },
  created () {
  },
  computed: {
    activeColor () {
      switch (this.name.toLowerCase()) {
        case 'warrior':
          return '#691e20'
        case 'warlock':
          return '#4f3857'
        case 'rogue':
          return '#2f303b'
        case 'shaman':
          return '#1b2580'
        case 'priest':
          return '#b0b4ba'
        case 'paladin':
          return '#b87926'
        case 'mage':
          return '#5f6f9d'
        case 'hunter':
          return '#416122'
        case 'druid':
          return '#6a3a27'
        case 'demon hunter':
          return '#1a3732'
        default:
          return '#ffffff'
      }
    },
    subtitle () {
      switch (this.name.toLowerCase()) {
        case 'warrior':
          return 'You\'re gonna have to come in on Saturday.'
        case 'warlock':
          return 'We are happy to take your call.'
        case 'rogue':
          return 'Slash and burn, take it all.'
        case 'shaman':
          return 'What happens if we make it blue?'
        case 'priest':
          return 'We\'re really like a big family, here.'
        case 'paladin':
          return 'Spin-doctor, line 1.'
        case 'mage':
          return 'Yes, your retirement plans are defrostable accounts.'
        case 'hunter':
          return 'Have you tried turning it off then on again?'
        case 'druid':
          return 'Outsider trading!'
        case 'demon hunter':
          return 'Better make sure you\'re in compliance.'
        default:
          return '#ffffff'
      }
    }
  },
  props: {
    deck: {
      type: Object
    },
    name: {
      type: String
    }
  }
}
</script>
<style scoped>
</style>
