<template>
  <div>
    <div class="input-container">
        <i class="fas fa-search"></i>
        <input type="text" v-model='searchprofile' v-bind:placeholder="placeholder">
        <button @click.prevent="getGithubProfile">Search</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'FormSearch',
 data() {
   return {
     placeholder: 'Search Github username',
     searchprofile: ""
   }
 },
 methods:{
   getGithubProfile() {
     this.$emit('getGithubUser', this.searchprofile)
   }
 }
}
</script>

<style scoped>
  .input-container {
    display:flex;
    flex-direction:row;
    border:1px solid grey;
    border-radius: 10px;
    padding:5px;
}

input {
  /* Tell the input to use all the available space */
  flex-grow:2;
  /* And hide the input's outline, so the form looks like the outline */
  border:none;
}

input:focus {
  /* removing the input focus blue box. Put this on the form if you like. */
  outline: none;
}

i.fas {
  font-size: 20px;
  color: #0061FF;
  padding: 10px;
}

button {
  border: none;
  padding: 15px 25px;
  cursor: pointer;
  background: #0061FF;
  color:white;
  font-weight: bold;
  border-radius: 5px;
}

button:focus {
  outline: none;
}
</style>