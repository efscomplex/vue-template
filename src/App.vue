<template lang="pug">
#app
      Header(:logo="require('@/assets/logo.png')" )
            template(#actions)
                  button.btn.primary Get Started
                  button.btn.primary(style="margin:0 1rem") Language: En
      main
            h1 main section
      footer
            h2 footer powered by @efscomplex

</template>

<script>
import Header from '@/components/core/Header'
import Navbar from '@/components/core/Navbar'
import '@/styles/styles.styl'

export default {
    name: 'app',
    components:{
       Header,
       Navbar,
    }
}
</script>
<style lang="stylus" scoped>
#app
      min-height 100vh
      --popup-bg-c #888
      --popup-c gray
      color white
      background-color #333
</style>
<style lang="stylus">      
.navbar.vertical
      color #333
      background-color white
header .actions
      @media screen and (max-width 768px) 
            display none
</style>
