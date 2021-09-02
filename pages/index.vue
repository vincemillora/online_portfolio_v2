<template>
  <div>
    <header-component />
    <about />
    <portfolio />
    <v-btn
      v-scroll="onScroll"
      v-show="fab"
      large
      fab
      dark
      fixed
      bottom
      right
      class="mb-8"
      color="#c0375f"
      @click="toTop"
    >
      <v-icon large>mdi-chevron-up</v-icon>
    </v-btn>
  </div>
</template>

<script>
  import headerComponent from '~/components/header/Header.vue'
  import about from '~/components/about/About.vue'
  import portfolio from '~/components/portfolio/Portfolio.vue'

  export default {
    components: {
      headerComponent,
      about,
      portfolio
    },
    data() {
      return {
        fab: false,
      }
    },
    methods: {
      onScroll (e) {
        if (typeof window === 'undefined') return
        const top = window.pageYOffset ||   e.target.scrollTop || 0
        this.fab = top > 20
      },
      toTop () {
        this.$vuetify.goTo(0)
      },
    }
  }
</script>

