<script setup>
const props = defineProps({
  TL: {
    type: String,
    default: 'Bash',
  },
})
</script>

<template>
  <div class="TL">
    <div class="TL_word">{{ props.TL }}</div>
  </div>
</template>

<style lang="scss">
.TL {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 40px;
  height: 30px;
  position: relative;
  // left: 0px;
  &_word {
    width: 20px;
    height: 20px;
    text-align: center;
    color: rgb(170, 170, 170);
    font-size: 16px;
  }
}
// .TL {
//   color: rgb(170, 170, 170);;
//   font-size: 18px;
// }
</style>
