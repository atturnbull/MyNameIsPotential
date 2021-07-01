<template>
  <div>My component</div>
  <card-detail />
</template>

<script>
import CardDetail from '../components/CardDetail.vue'

export default {
  name: 'ClassDeckView',
  setup () {
    return {}
  },
  props: {
    deckname: {
      type: String
    }
  },
  components: {
    'card-detail': CardDetail
  }
}
</script>
