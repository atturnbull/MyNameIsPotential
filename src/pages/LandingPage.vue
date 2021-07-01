<template>
  <q-page>
    <q-dialog v-model="showDetail" >
      <q-card style="height: 300px; width: 350px;">
        <div class="bg-blandground">
          <div class="row justify-around items-center q-ma-md">
            <q-btn class=" bg-primary text-white" style="height: 25px;" label="<" @click="previousDetail" />
              <q-card v-if="activeExplanation == 0" class="flex flex-center row text-wrap buzzword-nogrow q-pa-md">
                <strong>INVESTMENT</strong> OPPORTUNITIES!
              </q-card>
              <q-card v-if="activeExplanation == 1" class="flex flex-center row text-wrap buzzword-nogrow ">
                <span><strong>CONTINUOUS</strong> INTEREST!</span>
              </q-card>
              <q-card v-if="activeExplanation == 2" class="flex flex-center row text-wrap buzzword-nogrow">
                <strong>PROFESSIONAL</strong> GROWTH SYNERGY!
              </q-card>
              <q-card v-if="activeExplanation == 3" class="flex flex-center row text-wrap buzzword-nogrow q-pa-md">
                <strong>ITEMIZED</strong> REWARD STRUCTURE!
              </q-card>
              <q-card v-if="activeExplanation == 4" class="flex flex-center row text-wrap buzzword-nogrow q-pa-md">
                <strong>INTEGRATION</strong> AND ACQUISITION!
              </q-card>
            <q-btn class="bg-primary text-white" style="height: 25px;" label=">" @click="nextDetail" />
          </div>
          <div class="column text-center text-gray">
            <q-card-section class="big-explain-name text-italic">
              - {{explanations[activeExplanation].name.toUpperCase()}} -
            </q-card-section>
            <q-card-section>
              {{explanations[activeExplanation].description}}
            </q-card-section>
          </div>
        </div>
      </q-card>
      <q-img
        class="no-shadow card"
        fit="scale-down"
        style="margin-left: 25px; margin-top: -100px; z-index: 0;"
        loading="lazy"
        alt="card image"
        :src="explanations[activeExplanation].exampleCard"
      />
    </q-dialog>
    <q-card class="col-1">
          <q-carousel
            arrows
            animated
            autoplay="7000"
            v-model="slide"
            height="400px"
          >
            <q-carousel-slide name="first" style="background-size: {{$q.screen.width}};" img-src="https://www.pardot.com/wp-content/uploads/2020/09/do-not-use-1.jpg">
              <div class="absolute-bottom custom-caption">
                <div class="text-h2 text-white">"We put the pirate in Corpirate."</div>
                <div class="text-subtitle1 text-white">-J.D. Blackfoot</div>
              </div>
            </q-carousel-slide>
            <q-carousel-slide name="second" img-src="https://cdn.quasar.dev/img/parallax1.jpg">
              <div class="absolute-bottom custom-caption">
                <div class="text-h2">"This is a placeholder"</div>
                <div class="text-subtitle1">-Aedam Edinson</div>
              </div>
            </q-carousel-slide>
            <q-carousel-slide name="third" img-src="https://cdn.quasar.dev/img/parallax2.jpg">
              <div class="absolute-bottom custom-caption">
                <div class="text-h2">"What's a placeholder"</div>
                <div class="text-subtitle1">-Thóra Lindborg</div>
              </div>
            </q-carousel-slide>
          </q-carousel>
          <q-card-section class="flex flex-between column col-12 text-center">
            <div class="text-italic text-bold pop-text">All new buzzwords!</div>
            <q-card-section class="flex flex-center row">
              <q-card class="flex flex-center row text-wrap buzzword" clickable @click="activeExplanation = 0; showDetail = true;">
                <strong>INVESTMENT</strong> OPPORTUNITIES!
              </q-card>
              <q-card class="flex flex-center row text-wrap buzzword" @click="activeExplanation = 1; showDetail = true;">
                <span><strong>CONTINUOUS</strong> INTEREST!</span>
              </q-card>
              <q-card class="flex flex-center row text-wrap buzzword" @click="activeExplanation = 2; showDetail = true;">
                <strong>PROFESSIONAL</strong> GROWTH SYNERGY!
              </q-card>
              <q-card class="flex flex-center row text-wrap buzzword" @click="activeExplanation = 3; showDetail = true;">
                <strong>ITEMIZED</strong> REWARD STRUCTURE!
              </q-card>
              <q-card class="flex flex-center row text-wrap buzzword" @click="activeExplanation = 4; showDetail = true;">
                <strong>INTEGRATION</strong> AND ACQUISITION!
              </q-card>
            </q-card-section>
          </q-card-section>
          <div class="text-italic text-center q-mb-lg text-bold pop-text">Same old office, fresh new faces!</div>
          <div v-for="(deck, index) in decks" :key="index">
            <LiteGallery :deck="deck" :name="index"/>
          </div>
    </q-card>
  </q-page>
</template>

<script>
import { ref } from 'vue'
import DeckData from '../../DeckData.json'
import LiteGallery from 'components/LiteGallery.vue'

export default {
  name: 'LandingPage',
  setup () {
    return {
      decks: DeckData,
      slide: ref('first'),
      activeExplanation: ref(0),
      showDetail: ref(false),
      explanations: [
        {
          name: 'Invest',
          description: 'Effect! When triggered, it stores an investment! Best compared to Invoke. Fully flavorful text to follow!',
          exampleCard: 'https://i.imgur.com/5CogUba.png'
        },
        {
          name: 'Interest',
          description: 'Talks about the cards that have continuous effects, that happen at the end of your turn.',
          exampleCard: 'https://i.imgur.com/5CogUba.png'
        },
        {
          name: 'Profession',
          description: 'Consumes all Investments when played, and does something per one consumed.',
          exampleCard: 'https://i.imgur.com/5CogUba.png'
        },
        {
          name: 'Item',
          description: 'Classification for Spells! Any Parts, Scrolls, Tomes, Wands, Relics, Fruit, or Potions are classified as Items! Basic explanation; if it\'s a Thing and not doing something WITH the thing, it\'s an Item.',
          exampleCard: 'https://i.imgur.com/5CogUba.png'
        },
        {
          name: 'Merger',
          description: 'Talks about the cards that mix Pirates and a type, and then the cards that mix Item and a type.',
          exampleCard: 'https://i.imgur.com/5CogUba.png'
        }
      ]
    }
  },
  created () {
    console.log(DeckData)
  },
  props: {
    deckname: {
      type: String
    }
  },
  methods: {
    previousDetail () {
      this.activeExplanation > 0 ? this.activeExplanation-- : this.activeExplanation = 4
      console.log(this.explanations[this.activeExplanation])
    },
    nextDetail () {
      this.activeExplanation < 4 ? this.activeExplanation++ : this.activeExplanation = 0
      console.log(this.activeExplanation)
    }
  },
  components: {
    LiteGallery
  }
}
</script>
<style lang="sass" scoped>
.custom-caption
  text-align: center
  padding: 12px
  color: white
  background-color: rgba(0, 0, 0, .3)

.big-explain-name
  font-size: 32px

.pop-text
  font-size: 20px

.buzzword
  width: 175px
  height: 113px
  padding: 25px
  margin: 10px
  transition-duration: 0.5s
  z-index: 1
  background-color: $secondary
  color: white

.buzzword-nogrow
  width: 175px
  height: 70px
  transition-duration: 0.5s
  z-index: 1
  background-color: $secondary
  color: white

.buzzword:hover
  transform: scale(1.5)
  transition-duration: 0.5s
  z-index: 2

.buzzinfo
  transition-duration: 0.5s
  display: none
  font-size: 10px

</style>
