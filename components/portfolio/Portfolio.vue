<template>
  <v-row 
    no-gutters
    justify="center"
  >
    <v-col 
      :cols="isPhone ? 12 : 6"
      v-bind:class="{'title-sticky': !isPhone}">
      <v-row 
        no-gutters
        justify="center"
        align="center"
        class="background-right title-sticky"
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
      </v-row>
    </v-col>
    <v-col :cols="isPhone ? 12 : 6">
      <miel-agency />
    </v-col>
  </v-row>

</template>

<script>
  import MielAgency from '~/components/portfolio/items/MielAgency.vue'

  export default {
    components: {
      MielAgency,
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
  }
</script>

<style css-scoped>
  .background-right {
    height: 100vh;
  }
  .title-text {
    font-size: 5rem;
    color: #2C2E2F;
  }
</style>
