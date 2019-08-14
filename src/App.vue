<template>
  <div id="app">
    <header class="header" ref="header">
      <a href="https://unsplash.com/@colemader" class="header-link header-link-logo">Cole Mader</a>
    </header>
    <div class="curtain"></div>
    <div class="side" ref="side"></div>
    <router-view/>
  </div>
</template>

<script>
  
  import TweenMax from 'gsap'
  import CustomEase from "./libs/gsap/CustomEase.js"
  
  export default {
    name: 'App',
    mounted() {
      
      TweenMax.from(this.$refs.header, 1,
        {
          opacity: 0,
          delay: 1.5
        }
      )
      
      TweenMax.to(this.$refs.side, 1,
        {
          width: '100%',
          right: 0,
          ease: CustomEase.create("custom", "M0,0 C0.77,0 0.175,1 1,1"),
          delay: 1.5
        }
      )
    
    }
  }

</script>

<style lang="sass">
  
  @import url('https://fonts.googleapis.com/css?family=Playfair+Display:400,700&display=swap')

  body
    margin: 0
    font-family: 'Playfair Display', sans-serif
    font-size: 14px
    font-weight: 400
    font-style: normal
    font-stretch: normal
    line-height: 1.2
    
  .section
    display: flex
    align-items: center
    justify-content: center
    min-height: 100vh
    box-sizing: border-box
    overflow: hidden
  
  .header
    display: flex
    align-items: center
    justify-content: space-between
    padding: 25px
    box-sizing: border-box
    position: absolute
    top: 0
    right: 0
    left: 0
    z-index: 5

  .header-link
    font-weight: 700
    color: #1a1a1a
    text-decoration: none
    
  .image-wrapper
    overflow: hidden
    position: relative
  
  .image
    display: block
    width: 65vw
    opacity: 0.75
    
  .image-curtain
    display: block
    width: 100%
    position: absolute
    top: 0
    right: 0
    bottom: 0
    left: 0
    background-color: #fff
    
  .title
    margin: 0
    font-size: 70px
    font-weight: 700
    text-transform: uppercase
    text-align: center
    letter-spacing: 2.5px
    color: #1a1a1a
    position: absolute
    z-index: 5
    
  .title-string-wrapper
    margin: 10px 0
    overflow: hidden
    
  .title-string
    display: block
    
  .side
    width: 0%
    background-color: #f5f5f5
    position: absolute
    top: 0
    bottom: 0
    left: 50%
    z-index: -1

  .curtain
    width: 0%
    background-color: #f0f1f3
    position: absolute
    top: 0
    right: 0
    bottom: 0
    left: 0
    z-index: 10
    animation: slideCurtain 1.5s cubic-bezier(.77, 0, .175, 1)
  
  @keyframes slideCurtain
    0%
      left: 0
      width: 0%
    50%
      left: 0
      width: 100%
    100%
      left: 100%
      width: 0
  
</style>
