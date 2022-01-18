<template>
  <v-row 
    no-gutters
    justify="center"
  >
    <v-col 
      class="white-bg transition-effect"
      :cols="isPhone ? 12 : start_transition ? 3 : 6"
      v-bind:class="{'title-sticky': !isPhone}"
      style="z-index: 100"
    >
      <v-row 
        no-gutters
        justify="center"
        align="center"
        class="background-right title-sticky"
        style="positon: relative"
      >
        <div 
          class="cursive-text font-weight-bold title-text slant"
          v-bind:class="{
            'title-size-pc': !isPhone,
            'title-size-mp': isPhone,
          }"
        >
          Work
        </div>
        <div style="position: absolute; bottom: 25px">
          <section-footer :is_dark="false" />
        </div>
        <v-btn
          v-if="start_transition && !isPhone"
          fab
          dark
          color="#3e3d57"
          style="position: absolute; top: 10%; right: -28px;"
          @click="closeDetails"
        >
          <v-icon color="#c0375f">mdi-close</v-icon>
        </v-btn>
      </v-row>
    </v-col>
    <v-col
      class="transition-effect"
      :cols="isPhone ? 12 : start_transition ? 9 : 6"
      style="z-index: 1;"
    >
      <div 
        v-if="section === null || !start_transition || section === 'mielAgency'"
        id="mielAgency"
      >
        <miel-agency 
          :is_show_details="start_transition"
          @expand="showDetails('mielAgency')"
          @next="nextSection" 
        />
      </div>
      <div
        v-if="section === null || !start_transition || section === 'mielAI'"
        id="mielAI"
        v-bind:class="{'clickable': !start_transition}"
        @click="showDetails('mielAI')"
      >
        <mielAi :is_show_details="start_transition" />
      </div>
    </v-col>
  </v-row>

</template>

<script>
  import SectionFooter from '~/components/misc/SectionFooter.vue'
  import MielAgency from '~/components/portfolio/items/MielAgency.vue'
  import mielAi from '~/components/portfolio/items/MielAI.vue'

  export default {
    components: {
      MielAgency,
      mielAi,
      SectionFooter
    },
    data() {
      return {
        is_show_details: false,
        start_transition: false,
        section: null
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
      showDetails(section) {
        this.is_show_details = true
        this.$scrollTo(`#${section}`)
        this.section = section

        let self = this
        setTimeout(function(){ 
          self.start_transition = true
        }, 750);
      },
      closeDetails() {
        this.is_show_details = false
        this.$scrollTo(`#${this.section}`)

        let self = this
        setTimeout(function(){ 
          self.start_transition = false
          self.section = null
        }, 750);
      },
      nextSection(section) {
        this.closeDetails()

        let self = this
        setTimeout(function(){ 
          self.showDetails(section)
        }, 1000);
      }
    }
  }
</script>

<style scoped>
  .background-right {
    height: 100vh;
  }
  .title-text {
    font-size: 5rem;
    color: #2C2E2F;
  }
  .clickable {
    cursor: pointer;
  }
</style>
