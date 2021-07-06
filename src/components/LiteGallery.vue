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
        <p>{{activeBlurb}}</p>
      </div>
      <q-card-section v-if="deck.length > 0" class="text-center pop-text">
        Top Performers:
      </q-card-section>
      <q-card-section class="row justify-around">
        <q-img
          class="no-shadow col-1 bighover"
          crossorigin="anonymous"
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
    activeBlurb() {
      switch (this.name.toLowerCase()) {
        case 'warrior':
          return 'The busybody core of our multistage marketing masterclass, these heavy hitting hustlers handle all the baseline issues in sales and advertising. They know how to close a deal like nothing else, and don’t even get me started on their upsale! Sure, they’ve been getting more and more merchanized as time’s gone on, but that doesn’t mean their job’s replaceable! In fact, it’s the exact opposite. It takes a full platoon of fully dedicated engineers and artificers to create something HALF as good as one of our warriors. '
        case 'warlock':
          return 'We will admit; some of the work here can be soul-draining. Thankfully, that’s the warlock’s MO! Our cloak clad customer service team can handle ANYTHING that the retail front of Ravenholdt Inc. can throw at them. Need something returned? Absolutely. Want to know where we keep the poison? They’ve got you. And have you SEEN the rewards cards, they’re able to push? For anyone else, this job would have been hell. And for them, it still is! They’re just, for whatever reason, all about that!'
        case 'rogue':
          return 'The heart and soul of any good assassination orginization, our rogues are on the cutting edge of white collar crime! Everyone knows that a company falls apart from the inside, so we’re getting rid of the middleman, and starting our research on how best to make yourself rich, without even trying. Way we figure it, if everyone’s stealing, then no-one is! Plus, it guarantees a lack of competition! What are the other companies gonna do, get rid of us? Have they seen the people we attract? No way we’ll forgive them. '
        case 'shaman':
          return 'It’s difficult, trying to think of the next breakthrough. That’s why we have our top Shaman’s, plundering and pondering the plentiful positions that the planet can provide! Yes, our research and development team uses only the best that the elemental lords have to offer, with astounding results! By reinventing what’s already been established, we can guarantee that the customers won’t feel out of place with our products, while our competition will be shocked, and left in the dust! In more ways than one, of course.'
        case 'priest':
          return 'Workplace harassment is only to be expected, in a rowdy, cross factional environment such as our offices. As such, who do people turn to, when they’ve got one to many arrows in their sternum? That’s right, the lovely priests in Healing Resources, of course! HR focuses on settling disputes, and disarming greater situations from occurring, while still providing a safe environment for people to settle personal disputes. After all, it’s just like we always say! “You can kill each other plenty; just not on the clock!”'
        case 'paladin':
          return 'What’s the most important thing about selling a product? That’s right, PLACEMENT. If you’re a friendly enough face, you could sell an ice box to a tuskarr. And who better to represent us, than the only class with “Pal" in their name? Our fleet of paladins are all trained to subliminally train the masses, that our prices are fair and that our hours are reasonable. With abundant free samples, our Paladin Relations team, or PR team, are here to make enemies into friends, and friends into enemies.'
        case 'mage':
          return 'Accounting is a herculean task, especially for such a complexing complex as ours. Thankfully, our arcane associates are able to account for nearly everything! Peering into the future, gathering information from everywhere they can, they’ve got the whole thing down to a science! And beyond just budgets, they’ve got an astounding outreach, in regards to markets! With extreme accuracy, they can pinpoint exactly who and where on Azeroth needs our products, and can teleport them a sample, and a business card.'
        case 'hunter':
          return 'Behind every great event are those doing their best to make sure everything goes smoothly. And for us, it’s our dear Hunters. With trained, constantly tracking eyes, they can spot bugs and system inconsistencies from a mile away, and take the necessary actions to keep those cogs turning. Armed with an overabundance of trained messenger animals, they can keep the information flowing, and flowing fast. And they also have guns! Just in case. It’s a thankless job, but someone’s gotta do IT.'
        case 'druid':
          return 'When it comes to stalks and bonds, none understand them quite like our Druidic team. Within moments of its opening, our transformative traders can track and train thousands of truly terrific trees and plants, on the global market, with each one representing the growth of a company. Alongside trimming the bonsai that are our competitions, they also guarantee our metaphorical proliferation, by constantly opening and maintaining new branches across the globe. And believe you me, baby, business is BLOOMING.'
        case 'demon hunter':
          return 'With all the chaos and havoc breaking out, SOMEONE’S got to keep us on the straight and narrow! And who better than our very own Union Representatives? The Demon Hunters of Labor Union 667 maintain absolute order, by ensuring that our pandemonium falls under strict guidelines. Is everyone fighting to their death wearing hardhats and UV vests? Are those in the punishment cube getting at least five 30 minute breaks a day? And are the wages of sin equal to the amount of sin going in? If not, STRIKE!'
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
