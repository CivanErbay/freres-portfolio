<template>
  <div id="landing" class="landing-wrapper">
    <h1 class="headline-link">hannafreres</h1>
  </div>
</template>

<script>
export default {
  
}
</script>

<style lang="scss">
  .landing-wrapper {
    
      width: 100vw;
      height: 100vh;
      background: url('../assets/img1.jpeg') no-repeat 0 0;
      background-position: center;
      background-size: contain;
      position: relative;
    

    .headline-link {
        position: absolute;
        font-weight: 300;
        font-size: 4rem;
        color: white;
        top: 150px;
        left: 100px;
    }
  }
</style>