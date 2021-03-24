<template>
  <header>
    <h1>{{ title }}</h1>
    <Button/>
  </header>
</template>

<script>
import Button from './Button';
export default {
  name: "Header",
  props: {
      title:String,
    // title: {
    //   type: String,
    //   default: "Hello Finland",
    // },
  },
  components:{
      Button,
  }
};
</script>
<style scoped src="../css/header.css"></style>
