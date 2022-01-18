<template>
  <v-row 
    no-gutters
    justify="center"
  >
    <v-col 
      :cols="isPhone ? 12 : 6"
      v-bind:class="{'title-sticky': !isPhone}"
    >
      <v-row 
        no-gutters
        justify="center"
        align="center"
        class="background-left component-height"
        style="positon: relative"
      >
        <div 
          class="white--text cursive-text font-weight-bold title-text slant"
          v-bind:class="{
            'title-size-pc': !isPhone,
            'title-size-mp': isPhone,
          }"
        >
          Contact
        </div>
        <div 
          style="position: absolute; bottom: 25px"
          class="white--text"
        >
          <section-footer :is_dark="true" />
        </div>
      </v-row>
    </v-col>
    <v-col 
      :cols="isPhone ? 12 : 6" 
      class="component-height white-bg"
      style="display: flex; flex-direction: column;"
      v-bind:class="{
        'pa-16':!isPhone,
        'pa-8': isPhone
      }"
    >
      <div class="font-weight-medium">
        Feel free to contact me - I'm open for any topic.
      </div>
      <div class="caption">
        You can contact me through my social accounts or through my email: <a @click="sendMail()"> vcmillora.03@gmail.com </a>
      </div>
      <v-divider class="my-5 mr-16" />
      <div>
        <v-btn 
          icon
          large
          href="https://twitter.com/VinceMillora"
          target="_blank"
          class="social-button"
        >
          <v-icon 
            color="#3e3d57" 
            class="hidden-button"
          >
            mdi-twitter
          </v-icon>
        </v-btn>
        <v-btn 
          icon
          large
          href="https://www.instagram.com/vcmillora/"
          target="_blank"
          class="social-button"
        >
          <v-icon 
            color="#3e3d57" 
            class="hidden-button"
          >
            mdi-instagram
          </v-icon>
        </v-btn>
        <v-btn 
          icon
          large
          href="https://www.linkedin.com/in/vince-millora-3606a0143/"
          target="_blank"
          class="social-button"
        >
          <v-icon 
            color="#3e3d57" 
            class="hidden-button"
          >
            mdi-linkedin
          </v-icon>
        </v-btn>
        <v-btn 
          icon
          large
          href="https://github.com/vincemillora"
          target="_blank"
          class="social-button"
        >
          <v-icon 
            color="#3e3d57" 
            class="hidden-button"
          >
            mdi-github
          </v-icon>
        </v-btn>
      </div>
      <div class="mt-auto">
        <contact />
      </div>
    </v-col>
  </v-row>
</template>

<script>
  import SectionFooter from '~/components/misc/SectionFooter.vue'
  import contact from '~/static/images/contact.svg'

  export default {
    components: {
      contact,
      SectionFooter
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
      openLink(link) {
        window.open(link);
      },
      sendMail(){
        window.open('mailto: vcmillora.03@gmail.com');
      },
    }
  }
</script>

<style scoped>
  .background-left {
    background-color: #3e3d57;
  }
  .component-height {
    height: 100vh;
  }
  .title-text {
    font-size: 5  rem;
  }
  .hidden-button {
    text-underline-offset:  var(--offset, 0.1em);
    transition: --offset 400ms, text-decoration-color 400ms;
  }
  .social-button:hover .hidden-button {
    --offset: 0.2em;
    text-decoration: underline 0.15em;
    text-decoration-color: #3e3d57;
    transform: rotate(-5deg) skew(-5deg);
  }
</style>