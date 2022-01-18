<template>
  <v-row 
    no-gutters
    class="background "
    justify="center"
    align="center"
  >
    <v-col 
      :cols="isPhone ? 8 : 4" 
      style="position: fixed; top: 50%; left: 50%; margin-right: -50%; transform: translate(-50%, -50%) "
    >
      <undraw-footer />
    </v-col>
  </v-row>
</template>

<script>
  import UndrawFooter from '~/static/images/footer.svg'

  export default {
    components: {
      UndrawFooter
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

<style scoped>
  .background {
    height: 100vh;
  }
</style>