<template lang='pug'>
div.popup
      slot
</template>
     
<script>
export default {

}
</script>
<style lang="stylus" scoped>
.popup
      --c inherit
      --bg-c transparent
      position absolute
      background-color: var(--bg-c, var(--popup-bg-c))
      color var(--c, var(--popup-c))
      &:before 
            pos = 1rem
            content 'X'
            position absolute
            top pos
            right pos

</style>