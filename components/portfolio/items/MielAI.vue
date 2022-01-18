<template>
  <div class="parent">
    <div class="content text-center">
      <div class="white--text content-text content-text-title">miel AI</div>
      <div class="white--text content-text content-text-subtitle">fashion market</div>
      <div class="hidden-button slant cursive-text mt-5">see more</div>
    </div>
    <div class="child white-bg">
      <v-img 
        height="100%"
        width="100%"
        src="/images/work/mielAI.jpg"
        eager
      />
    </div>
  </div >
</template>

<script>
  export default {
    props: ['is_show_details']  
  }
</script>

<style scoped>
  .parent {
    position: relative;
    width: 100%; 
    height: 100vh;
    overflow: hidden;
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