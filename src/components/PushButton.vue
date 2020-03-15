<template>
  <div class="button">
    <div class="letter">
      {{ letter }}
    </div>
  </div>
</template>

<script>
export default {
  props: {
    letter: String
  }
};
</script>

<style lang="sass">
$oldLace: #FAF5E1
$bone: #E4DFCD
$paleSilver: #CDC9B9
$oldSilver: #858478

.button
  width: 38px
  height: 38px
  display: flex
  flex-flow: column
  justify-content: center
  align-items: center

.letter
  padding: auto
  width: 28px
  height: 28px
  display: flex
  flex-flow: column
  justify-content: center
  align-items: center
  border: 1px solid $paleSilver
  border-bottom: 4px solid $paleSilver
  border-radius: 11px
  background: rgb(248, 248, 248)
  color: $oldSilver
  font-weight: bold
  cursor: pointer
  background: $oldLace
  user-select: none

.letter:hover
  transition: all 0.1s ease-in-out
  background: $bone
  border-bottom: 6px solid $paleSilver
  margin-bottom: 2px
</style>
