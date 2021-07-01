<template>
  <q-page>
    <q-dialog v-model="showDetail" >
      <q-card style="height: 400px; width: 400px;">
        <div class="bg-blandground">
          <div class="row justify-around items-center q-ma-md">
            <q-btn class=" bg-primary text-white" style="height: 25px;" label="<" @click="previousDetail" />
              <q-card v-if="activeExplanation == 0" class="flex flex-center row text-wrap buzzword-nogrow" >
                <strong>ITEMIZED</strong> REWARD STRUCTURE!
              </q-card>
              <q-card v-else-if="activeExplanation == 1" class="flex flex-center row text-wrap buzzword-nogrow" >
                <strong>INTEGRATION</strong> AND ACQUISITION!
              </q-card>
              <q-card v-else-if="activeExplanation == 2" class="flex flex-center row text-wrap buzzword-nogrow" >
                <span><strong>CATEGORIZING</strong> PIPE-LINE!</span>
              </q-card>
              <q-card v-else-if="activeExplanation == 3" class="flex flex-center row text-wrap buzzword-nogrow" >
                <strong>INVESTMENT</strong> OPPORTUNITIES!
              </q-card>
              <q-card v-else-if="activeExplanation == 4" class="flex flex-center row text-wrap buzzword-nogrow" >
                <strong>PROFESSIONAL</strong> GROWTH SYNERGY!
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
              <q-card class="flex flex-center row text-wrap buzzword" @click="activeExplanation = 0; showDetail = true;">
                <strong>ITEMIZED</strong> REWARD STRUCTURE!
              </q-card>
              <q-card class="flex flex-center row text-wrap buzzword" @click="activeExplanation = 1; showDetail = true;">
                <strong>INTEGRATION</strong> AND ACQUISITION!
              </q-card>
              <q-card class="flex flex-center row text-wrap buzzword" @click="activeExplanation = 2; showDetail = true;">
                <span><strong>CATEGORIZING</strong> PIPE-LINE!</span>
              </q-card>
              <q-card class="flex flex-center row text-wrap buzzword" clickable @click="activeExplanation = 3; showDetail = true;">
                <strong>INVESTMENT</strong> OPPORTUNITIES!
              </q-card>
              <q-card class="flex flex-center row text-wrap buzzword" @click="activeExplanation = 4; showDetail = true;">
                <strong>PROFESSIONAL</strong> GROWTH SYNERGY!
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
          name: 'I T E M',
          description: 'With the recent additions of Spell Schools, we here at Ravenholdt Incorporated wanted to take a moment to remind everyone of their favorite classification that they didn’t even know they were using! Item spells are any specific food, drink, tool, pack, book, scroll, idol, explosive, or or even deck that fall within our specific criteria. It’s like we always say, “If it’s the item doing the magic and not you, then give the item the credit”',
          exampleCard: 'https://i.imgur.com/5CogUba.png'
        },
        {
          name: 'P I R A T E S',
          description: 'Our coworkers are like family to us, and what better way to make a bigger family than with a wedding? As such, the higher ups have all banned together, to combine the tribes, so to say! Going overseas, we’ve worked with our new Pirate siblings to reach all kinds of new heights, and accrue all kinds of new products. From our family to yours, we hope you can let us into your hearts, and if not, we’ll find our own way in.',
          exampleCard: 'https://i.imgur.com/5CogUba.png'
        },
        {
          name: 'M E R G E R',
          description: 'With the new influx of Items, comes an opportunity of sales. After all, products come in all shapes and sizes, and anything can be sold to anyone, if they need it. That’s why, many of our legendary employees have taken on the task of organizing specific spells and classifications therein, and finding a market for them. Itemization and orginization is a key component, in a successful multiproduct firm.',
          exampleCard: 'https://i.imgur.com/5CogUba.png'
        },
        {
          name: 'I N V E S T',
          description: 'Say goodbye, Galakrond, and move over, C’thun, because there’s a NEW slow and steady build-up lord in town, and his name’s CAPITALISM! Our employees work hard for you, to make sure you always get the most for your mana. That’s why, certain effects will automatically Invest for you, increasing your total Investments. How you use these liquid assets are entirely up to you to decide, with our variable payout system, referenced in the next blurb!',
          exampleCard: 'https://i.imgur.com/5CogUba.png'
        },
        {
          name: 'P R O F E S S I O N S',
          description: 'Whew! Synergizing sure is hard work. But look at all that capital you’ve earned! By playing a Profession card, you can turn however many Investments you have into a plethora of powerful effects. You can do this more than once, but you have to gather new Investments each time. You’ve already spent your cash on the first one, after all! But best of all, these Professions are available to anyone, regardless of class! That’s right, Neutral Spells!',
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
