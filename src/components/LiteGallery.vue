<template>
  <q-expansion-item
    header-class="q-pa-xl text-h4"
    v-bind:style="{ 'background-color': activeColor, 'color': 'white' }"
    :label="name"
    expand-icon-class="text-white"
  >
    
  </q-expansion-item>
</template>

<script>
export default {
  name: 'lite-gallery',
  setup () {
    return {
      activeColor: ''
    }
  },
  created () {
    console.log(this.deck)
    console.log(this.name)
    this.activeColor = this.getActiveColor(this.name)
  },
  methods: {
    getActiveColor (type) {
      switch (type.toLowerCase()) {
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
