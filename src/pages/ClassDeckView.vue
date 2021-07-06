<template>
  <q-dialog v-model="showDetail" >
    <q-img
      class="no-shadow card"
      crossorigin="use-credentials"
      fit="scale-down"
      style="margin-left: 10px; margin-top: -125px; z-index: 0;"
      loading="lazy"
      alt="card image"
      :src="activeCard.imageUrl"
    />
    <q-card style="min-height: 325px; width: 425px; background-color: burlywood;">
      <q-card-section class="col-12 bg-grey-9" style="border-radius: 0px; min-height: 40px; box-shadow: 0px 1px 5px black;" />
      <div class="text-left mid-detail-text text-weight-400 q-mt-md q-pl-md">
        <b>Name:</b> {{activeCard.title}}
      </div>
      <div class="text-left mid-detail-text text-weight-400 q-pl-md">
        <b>Type:</b> {{activeCard.type}}
      </div>
      <div class="text-left mid-detail-text text-weight-400 q-pl-md">
        <b>Rarity:</b> {{activeCard.rarity}}
      </div>
      <div class="text-left mid-detail-text text-weight-400 q-pl-md">
        <span v-if="activeCard.power && activeCard.health"><b>Power:</b> {{activeCard.power}} <b>Health:</b> {{activeCard.health}}</span> <b>Mana Cost:</b> {{activeCard.cost}}
      </div>
      <div class="text-left mid-detail-text text-weight-400 q-pl-md">
        <b>Effect: </b>
        "<span v-if="activeCard.triggers.length > 0"
            v-for="(effect, index) in activeCard.triggers"
            :key="index"
          >
            {{effect+ (index < activeCard.triggers.length -1 ? ' & ' : ': ')}}
        </span>
        {{activeCard.detailText}}"
      </div>
      <div v-if="activeCard.flavorText && activeCard.flavorText.length > 0" class="text-center mid-detail-text text-weight-400 q-pt-lg">
        <i>"{{activeCard.flavorText}}"</i>
      </div>
    </q-card>
  </q-dialog>
  <q-card>
    <div class="text-italic text-bold text-center pop-text q-pa-md">"{{subtitle}}"</div>
    <q-card-section class="card-background-lighter text-center">
      {{deckBlurb}}
    </q-card-section>
    <q-card-section class="cardheader text-center" v-bind:style="{ 'background-color': activeColor, 'color': 'white', 'z-index': 2, 'box-shadow': '1px 2px 5px black' }">
      {{properDeckname}} Employee Directory
    </q-card-section>
    <q-card-section class="row justify-around flex-wrap card-background deck-padding" style="flex-wrap: wrap;">
        <q-img
          class="no-shadow col-xs-4 col-sm-2 col-md-1 col-lg bighover q-ma-xl"
          fit="scale-down"
          crossorigin="use-credentials"
          style="height: 200px;"
          loading="lazy"
          alt="card image"
          :src="item.imageUrl"
          v-for="(item, index) in data[properDeckname]"
          :key="index"
          @click="activeCard = item; showDetail = true;"
        />
    </q-card-section>
  </q-card>
</template>

<script>
import { ref } from 'vue'
import DeckData from '../../DeckData.json'

export default {
  name: 'ClassDeckView',
  setup () {
    return {
      showDetail: ref(false),
      data: DeckData,
      activeCard: {}
    }
  },
  computed: {
    deckname () {
      return this.$router.currentRoute.value.query.name
    },
    properDeckname () {
      return this.deckname[0].toUpperCase() + this.deckname.substring(1)
    },
    activeColor () {
      switch (this.deckname) {
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
      switch (this.deckname) {
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
  created () {
    console.log(DeckData[this.properDeckname])
  },
  props: {
    deckBlurb: {
      type: String,
      default: 'A Blurb goes here'
    }
  }
}
</script>
<style scoped>
.cardheader {
  font-size: 36px;
}

.pop-text {
  font-size: 20px
}

.mid-detail-text {
  font-size: 18px;
}

.deck-padding {
  min-height: 54.5vh;
}
</style>
