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
  border: 1px solid #B2AB8B
  border-bottom: 4px solid #B2AB8B
  border-radius: 11px
  background: rgb(248, 248, 248)
  color: #403E2B
  font-weight: bold
  cursor: pointer
  background: #F4EBBE
  user-select: none

.letter:hover
  transition: all 0.1s ease-in-out
  background: #FAF5E1
  border-bottom: 6px solid #B2AB8B
  margin-bottom: 2px
</style>
