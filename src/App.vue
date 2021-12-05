<template>
  <Header />
  <FormSearch @getGithubUser="registerUser($event)" />
  <CardBody />
</template>

<script>
import FormSearch from '@/components/FormSearch'
import Header from '@/components/Header'
import CardBody from '@/components/CardBody'



export default {
  name: 'App',
  components: {
    Header,
    FormSearch,
    CardBody
  },
  data() {
     return {
     githubUser: {},
     searchedProfile: ''
   }
  },
  methods: {
    async githubApi() {
      const response = await fetch('https://api.github.com/users/octocat')
      const data = await response.json()
      return data
    },
    registerUser(searchedProfile) {
      this.searchedProfile = searchedProfile
      // console.log(searchedProfile)
    }
  },
  async created() {
    const data = await this.githubApi()
    console.log(data)
    this.githubUser = data
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  width: 50%;
  min-width: 400px;
  color: #000;
  margin: auto;
  padding: 50px 0
}
</style>
