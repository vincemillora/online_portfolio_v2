<template>
  <div>
    <v-btn 
      text
      small
      :dark="is_dark"
      class="font-weight-bold footer-button"
      @click="scrollToSection('about')"
    >
      <div class="hidden-button">About</div>
    </v-btn>
    ・
    <v-btn 
      text
      small
      :dark="is_dark"
      class="font-weight-bold footer-button"
      @click="scrollToSection('portfolio')"
    >
      <div class="hidden-button">Work</div>
    </v-btn>
    ・
    <v-btn 
      text
      small
      :dark="is_dark"
      class="font-weight-bold footer-button"
      @click="scrollToSection('contact')"
    >
      <div class="hidden-button">Contact</div>
    </v-btn>
  </div>
</template>

<script>
  export default {
    props: ["is_dark"],
    methods: {
      scrollToSection(section) {
        this.$scrollTo(`#${section}`)
      }
    }
  }
</script>

<style scoped>
  .hidden-button {
    text-underline-offset:  var(--offset, 0.1em);
    transition: --offset 400ms, text-decoration-color 400ms;
  }
  .footer-button:hover .hidden-button {
    --offset: 0.2em;
    text-decoration: underline 0.15em;
    transform: rotate(-5deg) skew(-5deg);
  }
</style>