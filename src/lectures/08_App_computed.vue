<template>
  <div>
    <h2>{{ teacher.name }}</h2>
    <h3>강의가 있습니까?</h3>
    <!-- {{ teacher.lectures.length > 0 ? '있음★' : '없음☆' }} -->
    <p>{{ hasLecture }}</p>
    <p>{{ existLecture() }}</p>
    <p>{{ hasLecture }}</p>
    <p>{{ existLecture() }}</p>
    <button v-on:click="counter++">Counter : {counter}</button>

    <h2>이름</h2>
    <p>{{ fullName }}</p>
  </div>
</template>

<script>
import { computed, reactive, ref } from 'vue'

export default {
  setup() {
    const teacher = reactive({
      name: '짐코딩',
      lectures: ['HTML/CSS', 'Javascript', 'Vue3'],
    })
    const hasLecture = computed(() => {
      console.log('computed')
      return teacher.lectures.length > 0 ? '있음★' : '없음☆'
    })
    // computed가 성능 측면에서 좋음 (안에 값이 캐싱 되기 때문문)

    const existLecture = () => {
      console.log('method')
      return teacher.lectures.length > 0 ? '있음★' : '없음☆'
    }

    const counter = ref(0)

    const firstName = ref('홍')
    const lastName = ref('길동')

    const fullName = computed({
      get() {
        return firstName.value + ' ' + lastName.value
      },
      set(value) {
        ;[firstName.value, lastName.value] = value.split(' ')
      },
    })
    console.log('Console 출력: ', fullName.value)
    fullName.value = '짐 코딩'

    return { teacher, hasLecture, existLecture, counter, fullName }
  },
}
</script>

<style lang="scss" scoped></style>
