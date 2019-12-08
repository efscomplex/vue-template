<template lang='pug'>
nav
      .action(@click="onClick" v-if="showNav" :class="{'hide': !showNav}")
            slot(name="icon" )
                  span.burger 
      transition(:name="effect")
            .navbar(v-if="showMenu || !showNav")
                  slot
</template>
<script>
import {computed, ref, watch} from '@vue/composition-api'

export default {
      props: {
            effect: {
                  default: 'fade'
            },
            break:{
                  default: 768
            }
      },
      setup(props, {emit}) {
            let mustShow = window.innerWidth < props.break
            const showNav = ref(mustShow)
            emit('toggleBar', mustShow)
            const showMenu = ref(!showNav)

            window.addEventListener('resize',
                  () => {
                        mustShow = window.innerWidth < props.break
                        if (mustShow !== showNav.value){
                              showNav.value = mustShow
                              emit('toggleBar', mustShow)
                        }
                  }
            )

            function onClick() {
                  showMenu.value = !showMenu.value

            }

            return {
                  showNav,
                  showMenu,
                  onClick,
            }
      },
}
</script>
<style lang="stylus" scoped>

nav
   display:inline-grid
   grid-template-areas 'action' 'navbar'
.hide
      --lapse .3s
      transition width var(--lapse) ease-in-out, opacity var(--lapse) ease-in-out
      @media screen and (min-width m)
            width 0
            opacity 0
            overflow hidden
.action
      --lapse .4s
      display inline-block
      grid-area action
      transition width var(--lapse) ease-in-out, opacity var(--lapse) ease-in-out
      cursor pointer
.navbar
   grid-area navbar
.hide
   width 0
   opacity 0
   display none
.burger
   w = 3px
   size = 5*w
   --color:white
   display: inline-block
   margin-right:1rem
   width: size
   height: size
   cursor:pointer
   background: linear-gradient(var(--color) w,transparent w),linear-gradient(transparent w*2,var(--color) w*2,var(--color) w*3,transparent w*3),linear-gradient(transparent w*4,var(--color) w*4,var(--color) w*5,transparent w*5)
 
</style>
    