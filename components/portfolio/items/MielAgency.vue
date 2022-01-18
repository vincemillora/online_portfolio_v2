<template>
  <div 
    class="white-bg"
    v-bind:class="{
      'parent-border': is_show_details && !isPhone,
    }"
  >
    <div 
      class="parent"
      v-bind:class="{'clickable': !is_show_details}"
      @click="showDetails()"
    >
      <div class="child">
        <v-img 
          :height="is_show_details ? '75vh' : '100vh'"
          width="100%"
          src="/images/work/mielAgency.jpg"
          eager
          class="transition-effect"
        >
          <div class="content text-center">
            <div class="white--text content-text content-text-title">miel agency</div>
            <div class="white--text content-text content-text-subtitle">influencer marketing</div>
            <div v-if="!is_show_details" class="hidden-button slant cursive-text mt-5">see more</div>
          </div>
        </v-img>
      </div>
    </div>
    <div v-if="is_show_details" class="transition-effect white-bg">
      <div v-bind:class="{
          'pa-16':!isPhone,
          'pa-8': isPhone
        }"
      >
        <span>
        An Instagrammer network platform where customers can search and select influencers that can advertise their product. <strong>miel agency</strong> offer various advertising options such as sampling, feed/story posting, performance-based advertising, and ambassador advertising. 
        <br /><br />
        After influencers advertised the product, <strong>miel agency</strong> will gather performance data such as likes, comments, views, reach, and insights about the feed/story posts. Customers then can see these data reports real-time through the campaign management screen. 
        </span>
      </div>
      <div class="pa-16 text-center">
        <v-btn
          fab
          dark
          color="#3e3d57"
          @click="nextSection()"
        >
          <v-icon color="#c0375f">mdi-arrow-right-thick</v-icon>
        </v-btn>
      </div>
    </div>
  </div >
</template>

<script>
  export default {
    props: ['is_show_details'],
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
      nextSection() {
        this.$emit('next', 'mielAI')
      },
      showDetails() {
        if(!this.is_show_details) {
          this.$emit('expand')
        }
      }
    }
  }
</script>

<style scoped>
  .parent {
    position: relative;
    width: 100%; 
    overflow: hidden;
  }
  .parent-border {
    border-left: 1px solid rgb(226, 226, 226);
  }

  .child {
    width: 100%;
    height: 100%;
    background-position: center;
    background-size: cover;
    transition: all 20s;
  }

  .parent:hover .child,
  .parent:focus .child {
    transform: scale(1.2);
  }

  .parent:hover .child:before,
  .parent:focus .child:before {
    display: block;
  }

  .content {
    z-index: 100;
    position: absolute;
    top: 50%;
    left: 50%;
    -ms-transform: translate(-50%, -50%);
    transform: translate(-50%, -50%);
  }
  
  .clickable {
    cursor: pointer;
  }

  @property --offset {
    syntax: '<length>';
    inherits: false;
    initial-value: 0;
  }

  .hidden-button {
    text-decoration: underline 0.15em;
    text-underline-offset:  var(--offset, 0.2em);
    transition: --offset 400ms, text-decoration-color 400ms;
    color: white;
    font-size: 1.5rem;
  }

  .parent:hover .hidden-button {
    --offset: 0.4em;
    text-decoration-color: #c0375f;
  }

  @supports not (background: paint(something)) {
    a {
      transition: text-underline-offset 400ms, text-decoration-color 400ms;
    }
    
    a:hover,
    a:focus {
      text-underline-offset: 0.4em;
    }
  }
</style>