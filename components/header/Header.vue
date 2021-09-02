<template>
  <v-row 
    no-gutters
    class="background"
    justify="center"
    align="center"
  >
    <v-col 
      :cols="isPhone ? 8 : 4" 
      class="slant"
    >
      <div
        class="mx-auto"
        v-bind:class="{
          'image-size-pc': !isPhone,
          'image-size-mp': isPhone,
        }"
      >
        <dreamer />
      </div>
      <div 
        class="name text-center cursive-text font-weight-bold"
        v-bind:class="{
          'name-size-pc': !isPhone,
          'name-size-mp': isPhone,
        }"
      >
        Vince Millora
      </div>

    </v-col>
  </v-row>
</template>

<script>
  import dreamer from '~/static/images/dreamer.svg'

  export default {
    components: {
      dreamer,
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
  .background {
    height: 100vh;
    background: #2e2f41;
    background: linear-gradient(315deg, rgba(46,47,65,255) 40%, rgba(62,61,87,255)100%);
  }
  .image-size-pc {
    width: 60%
  }
  .image-size-mp {
    width: 100%
  }
  .name {
    letter-spacing: -0.015625em;
    color: #c0375f;
  }
  .name-size-pc {
    margin-top: -50px;
    font-size: 4rem;
  }
  .name-size-mp {
    margin-top: -40px;
    font-size: 2.5rem;
  }
</style>

