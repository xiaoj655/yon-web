<script setup>
import axios from 'axios'
import { onBeforeMount } from 'vue';

const lk = ref()
onBeforeMount(() => {
  axios.get('https://yesno.wtf/api').then(res => {
    console.log(res.data)
  })
})

</script>

<template></template>