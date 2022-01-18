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
        class="background-left"
        style="positon: relative"
      >
        <div 
          class="white--text cursive-text font-weight-bold title-text slant"
          v-bind:class="{
            'title-size-pc': !isPhone,
            'title-size-mp': isPhone,
          }"
        >
          About
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
      class="white-bg"
      v-bind:class="{
        'pa-16':!isPhone,
        'pa-8': isPhone
      }"
    >
      <span> 
        Hi there, my name is Vince Carreon Millora, a guy from the Philippines. I am a software developer that enjoys coding
        and solving complex problems. I have experiences in using different technologies; I've been a back-end developer designing databases and APIs, a Blockchain developer 
        creating Smart Contracts, and a front-end engineer designing and creating web and mobile systems. In every position I've been, and every tasks I had, I've always aimed
        for a good result that would not only satisfy myself, but also the team and the client. I'm a teamplayer that is always ready to assist my teammates when they are in need. 
        That's why one of my goal as a developer is to become a Full-Stack, so that I will be able to produce good results and assist my team even if the task is back-end or front-end. <br/><br/>
        
        Currently, I am studying the Japanese language at <a @click="openLink('http://bit-okutama.jp/')">Bridge Institute of Technology</a> to efficiently deliver my thoughts and solutions even while staying in Japan. 
        In the morning, I study Japanese by developing an I.T. project and during the end of the school's semester, I present my project using Japanese. In the afternoon, 
        I am a Web Developer of <a @click="openLink('https://jellyfish-g.co.jp/en/')">株式会社JELLYFISH</a>. <br/><br/>
        
        As a junior developer, I'm always open for new opportunities that will enhance my current skills. I hope I could interest you in some way or another. 
        You can checkout my resume here just in case.
      </span> 
    </v-col>
  </v-row>

</template>

<script>
  import SectionFooter from '~/components/misc/SectionFooter.vue'

  export default {
    components: {
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
    }
  }
</script>

<style scoped>
  .background-left {
    height: 100vh;
    background-color: #c0375f;
  }
  .title-text {
    font-size: 5  rem;
  }
</style>
