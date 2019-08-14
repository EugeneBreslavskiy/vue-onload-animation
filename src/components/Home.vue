<template>
  <section class="section">
    <h1 class="title">
      <div class="title-string-wrapper">
        <span class="title-string" ref="topString">Tween Lakes</span>
      </div>
      <div class="title-string-wrapper">
        <span class="title-string" ref="bottomString">United States</span>
      </div>
    </h1>
    <div class="image-wrapper">
      <img class="image" src="../assets/main.jpg" ref="image">
      <span class="image-curtain" ref="curtain"></span>
    </div>
  </section>
</template>

<script>

  import TweenMax from 'gsap'
  import CustomEase from "../libs/gsap/CustomEase.js"
  
  export default {
    name: "Home",
    mounted() {

      TweenMax.to(this.$refs.curtain, 1,
        {
          width: '0%',
          left: '100%',
          ease: CustomEase.create("custom", "M0,0 C0.77,0 0.175,1 1,1"),
          delay: 1.5
        }
      )
      
      TweenMax.from(this.$refs.topString, 1.25,
        {
          y: '100%',
          ease: CustomEase.create("custom", "M0,0 C0.77,0 0.175,1 1,1"),
          delay: 2
        }
      )

      TweenMax.from(this.$refs.bottomString, 1.25,
        {
            y: '-100%',
            ease: CustomEase.create("custom", "M0,0 C0.77,0 0.175,1 1,1"),
            delay: 2
        }
      )
      
    }
  }
  
</script>
