<template lang='pug'>
label.search
   slot
      i 🔎
   input(:value="value" @input="onInput" placeholder="search..." autofocus)
</template>
<script>
import {ref} from '@vue/composition-api'

export default {
   setup(){
      const value = ref('')

      function onInput(){
         console.log('new value');
      }
      return {
         value, onInput
      }
   }
}
</script>
<style lang="stylus" scoped>
.search
   cursor:pointer
   display: flex
   align-items: center
   padding: .4rem
   background-color:white
   border-radius:3px
input
   display: inline-block
   width: auto
   padding: 0 .6rem
   vertical-align: middle
   background-color:transparent
   border:none
   &:focus
      outline:none
</style>