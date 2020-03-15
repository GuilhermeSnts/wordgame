<template>
  <div class="chip">
    {{ word }}
  </div>
</template>

<script>
export default {
  props: {
    word: String
  }
};
</script>

<style lang="sass" scoped>
$oldSilver: #858478
$oldLace: #FAF5E1
$riffleGreen: #514F3E

.chip
    padding: 4px 16px
    margin: 3px
    background: $oldSilver
    border-radius: 8px
    color: $oldLace
    font-size: 1em
    font-weight: semi-bold
</style>
