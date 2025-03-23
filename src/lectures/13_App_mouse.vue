<template>
  <div>
    <div id="modifiers">
      <div @click="clickDiv">
        DIV 영역
        <p @click.self="clickP">
          P영역
          <!-- <span @click.stop="clickSpan">SPAN 영역</span> -->
          <!-- .stop Bubbling 막기 -->

          <span @click="clickSpan">SPAN 영역</span>
          <a href="https://naver.com" @click.prevent.stop="clickA">a 영역</a>
          <!-- .prevent 기존 기능 막기기 -->
        </p>
      </div>
    </div>
    <button @click.once="clickDiv">once</button>
    <!--  이벤트가 한 번만 일어남 -->
  </div>
</template>

<script>
export default {
  setup() {
    const clickDiv = () => {
      console.log('clickDiv')
      // location.href = 'https://naver.com'
    }
    const clickP = () => {
      console.log('clickP')
    }
    const clickSpan = () => {
      console.log('clickSpan')
      // alert('좋아요')
      // e.stopPropagation()
      // click.stop
    }
    const clickA = () => {
      alert('어떤 기능!')
    }
    return { clickDiv, clickP, clickSpan, clickA }
  },
}
</script>

<style scoped>
#modifiers div,
#modifiers p,
#modifiers span {
  padding: 40px;
}
#modifiers div {
  background-color: #ccc;
}
#modifiers p {
  background-color: #999;
}
#modifiers span {
  background-color: #666;
  display: block;
}
</style>
