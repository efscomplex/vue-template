<template lang='pug'>
header.header
      .logo
            slot(name="logo")
                  router-link(to="/")
                        Logo(v-if="!!logo" :src="logo" title="<h2>WordPress.com</h2>")
      .nav
            slot(name="nav")
                  Nav(@toggleBar="verticalBar=$event")
                        Navbar(:routes="navRoutes" :vertical="verticalBar")
      .actions
            slot(name="actions")
</template> 

<script>
import {ref} from '@vue/composition-api'

export default {
   props:{
      title: String,
      logo: String,
      routes: Array,
   },
   components:{
      Logo: () => import('@/components/base/Logo'),
      Navbar: () => import('@/components/core/Navbar'),
   },
   setup(props, {root}){
      const verticalBar = ref(false)
      const navRoutes = ref(
         root.$store.state.pages.slice(1)
      )

      return {navRoutes, verticalBar}
   }
}
</script>
<style lang="stylus" scoped>
header
   padding:.4rem 0
   width 100%

   display:grid
   grid-template-areas 'logo nav actions'
   align-items center

.actions
     margin 1rem
     grid-area actions
.logo
     grid-area logo
.nav
     grid-area nav
</style>