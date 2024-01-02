<script setup>
import axios from 'axios'
import { onBeforeMount, ref } from 'vue';

const lk = ref('')
const answer = ref()
onBeforeMount(() => {
  axios.get('https://yesno.wtf/api').then(res => {
    console.log(res.data)
    lk.value = res.data.image
    answer.value = res.data.answer
  })
})
</script>

<template>
  <div class="container">
    <img :src="lk" alt="" />
  </div>
  <div class="answer">{{ answer }}</div>
  <footer>
    <div>Powered By <em>brook.today</em></div>
    <div>Thanks to <em>yesno.wtf</em></div>
  </footer>
</template>

<style scoped>
* {
  box-sizing: border-box;
}

footer {
  display: flex;
  position: fixed;
  bottom: 0;
  width: 100%;
  font-size: 2rem;
  color: white;
  background-color: rgba(0, 0, 0, .5);
  padding: 0.5rem 2rem;
  justify-content: space-between;
}

.container {
  width: 100%;
  height: 100vh;
  /* padding-bottom: 100%; */
  position: relative;
  overflow: hidden;
  background-image: url(/loading.gif);
}

img {
  position: absolute;
  width: 100%;
  height: 100%;
  object-fit: cover;
}

@keyframes bounce {
  0% {
    /* transform: translateY(0); */
    scale: 1;
  }

  50% {
    /* transform: translateY(-20px); */
    scale: 1.5;
  }

  100% {
    /* transform: translateY(0); */
    scale: 1;
  }

}

.answer {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size: 6rem;
  color: white;
  text-shadow: 0 0 10px black;
  /* animation-name: bounce;
  animation-duration: 1.5s; */
  animation: bounce 1.5s 3;
}
</style>