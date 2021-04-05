<template>
<div>
    <h1>hi</h1>
<Poll />

<span> {{rows}} </span>
</div>
</template>

<script>
import Poll from "./Poll.vue";


export default {
  name: "PolList",
  components: {
     Poll,
  },
}

</script>

<style>

</style>
