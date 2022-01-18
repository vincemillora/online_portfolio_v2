<template>
  <div>
    <div style="position: relative; z-index: 10;">
      <header-component />
      <about id="about" />
      <portfolio id="portfolio" />
      <contact id="contact" />
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
    <footerComponent />
  </div>
</template>

<script>
  import headerComponent from '~/components/header/Header.vue'
  import footerComponent from '~/components/footer/Footer.vue'
  import about from '~/components/about/About.vue'
  import portfolio from '~/components/portfolio/Portfolio.vue'
  import contact from '~/components/contact/Contact.vue'

  export default {
    components: {
      headerComponent,
      footerComponent,
      about,
      portfolio,
      contact
    },
    data() {
      return {
        fab: false,
      }
    },
    computed: {
      isPhone() {
        if(this.$vuetify.breakpoint.name === "sm" || this.$vuetify.breakpoint.name === "xs") {
          return true
        } else {
          return false
        }
      },
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

<style scoped>
  .background {
    height: 100vh;
  }
</style>