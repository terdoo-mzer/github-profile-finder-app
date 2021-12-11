<template>
  <div>
    <div class="input-container">
        <i class="fas fa-search"></i>
        <input type="text" v-model='searchprofile' v-bind:placeholder="placeholder" autofocus>
        <button @click="checkEmptyField()">Search</button>
    </div>
     <div v-if="errorResponse">
                {{ errorResponse }}
    </div>
    <main v-else v-show="showUI">
           
           <div>
                 <div class="card-body">
                <div class="gh-img-name-username">
                    <img :src="githubUser.avatar_url" alt="gh-avatar">
                    <div class="name-date-container">
                        <div class="name-username">
                            <p class="gh-name">{{ githubUser.name }}</p>
                            <p style="color:#0061FF" class="gh-username">{{ githubUser.login }}</p>
                        </div>
                        <p v-bind:style="{ color: greyColor}">Joined <span class="joined-date"> {{ timeStamp  }} </span></p>
                    </div>
                    
                </div>

                <div class="stats-links-container">
                        <div class="profile-bio-stats">
                            <h3>Bio:</h3>
                            <div v-if="githubUser.bio" v-bind:style="{ color: greyColor}">
                                <p class="bio">
                                    {{ githubUser.bio }}
                                </p>
                            </div>
                            <div v-else>
                                <p class="bio">
                                    {{ error }}
                                </p>
                            </div>
                            
                            <div class="stats-box">
                                <!-- Repos -->
                                <div class="repos">
                                    <p class="gh-repos">Repos</p>
                                    <p class=" profile-numbers">{{ githubUser.public_repos }}</p>
                                </div>

                                <!-- Followers -->
                                <div class="followers">
                                    <p class="gh-followers">Followers</p>
                                    <p class="profile-numbers">{{ githubUser.followers }}</p>
                                </div>

                                <!-- Following -->
                                <div class="following">
                                    <p class="gh-following">Following</p>
                                    <p class="profile-numbers">{{ githubUser.following }}</p>
                                </div>
                            </div>
                            </div>

                        <!-- Profile Links -->
                        <div class="gh-links">
                            <ul> 
                                <div  v-bind:style="{ color: greyColor}">
                                    <div v-if="githubUser.location">
                                        <i class="fas fa-map-marker-alt"></i>
                                        <li>{{ githubUser.location }} </li>
                                    </div>
                                    <div v-else>
                                        <i class="fas fa-map-marker-alt"></i>
                                        <li>{{ error }} </li>
                                    </div>
                                </div> 
                                <div  v-bind:style="{ color: greyColor}">
                                    <div v-if="githubUser.twitter_username">
                                        <i class="fab fa-twitter"></i>
                                        <li>@{{ githubUser.twitter_username }}</li>
                                    </div>
                                    <div v-else>
                                        <i class="fab fa-twitter"></i>
                                        <li>{{ error }} </li>
                                    </div>
                                </div> 

                                <div  v-bind:style="{ color: greyColor}">
                                    <div v-if="githubUser.blog">
                                        <i class="fas fa-link"></i>
                                        <li><a :href="githubUser.blog">{{ githubUser.blog }}</a></li>
                                    </div>
                                    <div v-else>
                                    <i class="fas fa-link"></i>
                                        <li>{{ error }} </li>
                                    </div>
                                </div> 

                                <div  v-bind:style="{ color: greyColor}">
                                    <div v-if="githubUser.html_url">
                                        <i class="fas fa-building"></i>
                                            <li><a :href="githubUser.html_url"> {{ githubUser.html_url }}</a></li>
                                    </div>
                                    <div v-else>
                                    <i class="fas fa-building"></i>
                                            <li>{{ error }} </li>
                                    </div>
                                </div> 
                            </ul>
                        </div>
                </div>
             </div>
           </div>
        
    </main>
  </div>
</template>

<script>
import moment from 'moment'
export default {
  name: 'ApidataPage',
 data() {
   return {
    showUI: false,
    loading: true,
    greyColor: '#CBD5E1',
    errorResponse: '',
     githubUser: {},
     searchprofile: '',
     placeholder: 'Search Github username',
    loadingImage: require('../assets/transgif.gif'),
    error: 'Not available',
   }
 },
  methods: {
    async githubApi() {
        try {
             const response = await fetch(`https://api.github.com/users/${this.searchprofile}`)
            const data = await response.json()
              if (!response.ok) {
                throw new Error(response.status);
              }
                        // console.log(data)
            this.showUI = true
            this.loading = false
            return this.githubUser = data
        } catch(e) {
             console.log('Oops! User Not Found');
             this.errorResponse = 'Oops! User Not Found'
        }
     
    },
    // Check if user has typed into the input field
    checkEmptyField() {
        if(!this.searchprofile.length) {
                alert("Oops!!! You have to type into the input field :)")
        } else {
            // If user has typed into the input field then, make the request
            this.githubApi();
        }
    }
  },
  computed: {
      timeStamp() {
          return moment(this.githubUser.created_at).format("MMM Do YY");
      }
  }
}
</script>

<style scoped>
.input-container {
    display:flex;
    flex-direction:row;
    border: none;
    background: #1E293B;
    border-radius: 10px;
    padding:5px;
}

input {
  /* Tell the input to use all the available space */
  flex-grow:2;
  /* And hide the input's outline, so the form looks like the outline */
  border:none;
  background: #1E293B;
  color: #fff;
  font-size: 1.2em;
}

::placeholder {
    color: #fff;
}

input:focus {
  /* removing the input focus blue box. Put this on the form if you like. */
  outline: none;
}

i.fa-search {
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
  font-size: 1.1em;
  border-radius: 5px;
}

button:focus {
  outline: none;
}

/*  */

.card-body {
    background:  #1E293B;
    border-radius: 10px;
    margin-top: 10px;
    padding: 10px 10px;
}

.gh-img-name-username {
    display: flex;
    /* justify-content: space-around; */
}

.gh-name {
    font-size:1.2em
}

.name-date-container {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
}


/* .name-date-container p {
    margin: 0;
    background: blue;
} */


img {
    background: #fff;
    border-radius: 50%;
    border: none !important;
    width: 100px;
    height: 100px;
    margin-right: 10px;
}

.stats-links-container {
    width: 80%;
    margin-left: 20%; 
}

.profile-bio-stats .bio {
    text-align: left;
}

.stats-box {
    display: flex;
    justify-content:space-around;
    background: #0F172A;
    border-radius: 10px;
    color: #fff;
    font-weight: bold;
}

.profile-numbers {
    text-align: left;
}

.gh-links ul {
    display: grid;
    text-align: left;
    grid-template-columns: 1fr 1fr;
    padding: 0;
}

.gh-links ul div {
     margin-bottom: 5px;
}

.gh-links ul li {
    list-style-type: none;
    display: inline;
    padding: 10px;
}

.gh-links ul li a {
    text-decoration: none;
    color: #CBD5E1;
}

.loader-container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin: auto;
    min-height: 50vh;
}

@media only screen and  (max-width: 1000px) {
    .name-date-container {
        flex-direction: column !important;
    }

    .name-date-container {
        flex-direction: column;
      }

    .name-date-container p {
        margin-top: 0
      }

    .stats-links-container {
        width: 100%;
        margin-left: 0; 
    }

    .gh-links ul {
        grid-template-columns: 1fr;
        padding:0 ;
    }

     .gh-links ul div {
        padding-bottom: 5px;
    }
}
</style>