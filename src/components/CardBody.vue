<template>
    <div class="card-body">
            <div class="gh-img-name-username">
                <img src="../assets/logo.png" alt="gh-avatar">
                <div class="name-date-container">
                    <div class="name-username">
                        <p class="gh-name">Mzer Emmanuel Terdoo</p>
                        <p class="gh-username">terdoo-mzer</p>
                     </div>
                    <p>Joined <span class="joined-date"> 25 Jan 2011</span></p>
                </div>
                
            </div>

            <div class="stats-links-container">
                 <div class="profile-bio-stats">
                        <h3>Bio:</h3>
                        <p class="bio">
                            Lorem ipsum dolor sit amet consectetur adipisicing elit.
                            Ullam sint neque odio fugiat, nesciunt quas similique obcaecati 
                            cupiditate a saepe ducimus eveniet animi laboriosam deleniti at cum 
                            hic excepturi f
                        </p>
                        <div class="stats-box">
                            <!-- Repos -->
                            <div class="repos">
                                <p class="gh-repos">Repos</p>
                                <p class=" profile-numbers">8</p>
                            </div>

                            <!-- Followers -->
                            <div class="followers">
                                <p class="gh-followers">Followers</p>
                                <p class="profile-numbers">3938</p>
                            </div>

                            <!-- Following -->
                            <div class="following">
                                <p class="gh-following">Following</p>
                                <p class="profile-numbers">9</p>
                            </div>
                        </div>
                     </div>

                    <!-- Profile Links -->
                    <div class="gh-links">
                        <ul>
                            <div>
                                <i class="fas fa-map-marker-alt"></i>
                                <li><a href="#">Link a</a></li>
                            </div> 
                            <div>
                                <i class="fab fa-twitter"></i>
                                <li><a href="#">Link b</a></li>
                            </div> 
                            <div>
                                <i class="fas fa-link"></i>
                                <li><a href="#">Link c </a></li>
                            </div> 
                            <div>
                                <i class="fas fa-building"></i>
                                <li><a href="#">Link d</a></li>
                            </div> 
                        </ul>
                    </div>
            </div>
    </div>
</template>

<script>

export default {
    name: 'CardBody',
    data() {
        return {
            name: ''
        }
    }
}
</script>
<style scoped>
   
    .card-body {
        background: gray;
        border-radius: 10px;
        margin-top: 10px;
        padding: 10px 10px;
    }

    .gh-img-name-username {
        display: flex;
       /* justify-content: space-around; */
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
        width: 100px;
        height: 100px;
        padding: 10px;
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
        background: #fff;
        border-radius: 10px;
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

    .gh-links ul li {
        list-style-type: none;
        display: inline;
        padding: 10px;
    }

    .gh-links ul li a {
        text-decoration: none;
    }

    @media only screen and  (max-width: 1000px) {
        .name-date-container {
            flex-direction: column !important;
            background: red;
        }

        .name-date-container {
            flex-direction: column;
         }

        .stats-links-container {
            width: 100%;
            margin-left: 0; 
        }

        .gh-links ul {
            grid-template-columns: 1fr;
            padding: 0;
        }
    }



</style>
