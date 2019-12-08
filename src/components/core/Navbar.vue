<template lang='pug'>
ul.navbar(:class="!!vertical? 'vertical': 'horizontal'")
      template(v-for="route in routes")
            router-link(
                  :to="route.path" 
                  active-class="active") {{route.label}}
</template>

<script>
export default {
   props:{
      routes:{
         default:()=>[]
      },
      vertical:{
         type: [Boolean],
         default: false
      }
   },
}
</script>
<style lang="stylus" scoped>
.popup
      position absolute
      background-color: var(var(--popup-bg-c),--bg-c)
      color var(var(--popup-c), --c)
      &:before 
            font-size .8em
            //content '▴'//'❌'
            position absolute
            top .2rem
            right .6rem
            cursor pointer
            opacity .8
.vertical
      flex-direction:column
      @extend .popup !optional
      a
            padding: .6rem 0
.horizontal
   a
      padding:0 1rem

ul.navbar
   display:inline-flex
   border-radius 5px
   padding:1rem 2rem 1rem 1.4rem
   a
      text-decoration none
      text-transform capitalize
      display:block
      color:inherit
      letter-spacing:0.5px
      &:hover
         opacity:.7
</style>