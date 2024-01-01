<script setup>
import axios from 'axios'
import { onBeforeMount, ref } from 'vue';

const lk = ref()
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
  <img :src="lk" alt="" style="width: 100vw; height: 100vh;" />
  <div class="answer">{{ answer }}</div>
</template>

<style scoped>
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
  font-size: 5rem;
  color: white;
  text-shadow: 0 0 10px black;
  animation-name: bounce;
  animation-duration: 1.5s;
}
</style>