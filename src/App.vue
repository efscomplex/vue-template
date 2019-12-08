<template lang="pug">
#app
      Header(:logo="require('@/assets/logo.png')" )
            template(#actions)
                  button.btn.primary Get Started
                  button.btn.primary(style="margin:0 1rem") Language: En
      main
      footer

</template>

<script>
import Header from '@/components/core/Header'
import Navbar from '@/components/core/Navbar'
export default {
    name: 'app',
    components:{
       Header,
       Navbar,
    }
}
</script>
<style lang="stylus" scoped>
@import 'styles/'

#app
    color white
    background-color #333
</style>
<style lang="stylus">      
header .actions
      @media screen and (max-width 768px) 
            display none
</style>
