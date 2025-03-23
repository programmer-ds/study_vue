<template>
  <div>
    <div :style="styleObject">
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Obcaecati expedita architecto omnis!
      Deserunt id alias, harum atque quod recusandae, labore animi dolorum aut nisi blanditiis
      laboriosam dolor adipisci, itaque quo.
    </div>
    <button v-on:click="fontSize--">---</button>
    <button v-on:click="fontSize++">+++</button>
  </div>
</template>

<script>
import { computed, reactive, ref } from 'vue'

export default {
  setup() {
    // const styleObject = reactive({
    //   color: 'red',
    //   fontSize: '13px',
    // })

    const fontSize = ref(13)

    const styleObject = computed(() => {
      return {
        color: 'red',
        fontSize: fontSize.value + 'px',
      }
    })

    return { styleObject, fontSize }
  },
}
</script>

<style lang="scss" scoped></style>
