<template>
  <Header />
   <ApidataPage /> 
</template>

<script>

import Header from '@/components/Header'
import ApidataPage from '@/components/ApidataPage'




export default {
  name: 'App',
  components: {
    Header,
    ApidataPage
  },
  data() {
    return {}
  }
}
</script>

<style>
 @import url('https://fonts.googleapis.com/css2?family=Fira+Sans&display=swap');

#app {
  font-family: 'Fira Sans', sans-serif;
  width: 53%;
  min-width: 430px;
  color: #fff;
  margin: auto;
  padding: 50px 0
}
</style>
