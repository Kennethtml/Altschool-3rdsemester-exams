<script >
 import RepoList from "./components/ReposList"
export default{
 
  data(){
    return {
      user:null
    }
  }
  ,
  mounted(){
    fetch('https://api.github.com/users/kennethtml')
      .then(response => response.json())
      .then(data => {
        this.user = data;
        console.log(this.user);
      })
      .catch(error => {
        console.error(error);
      });
  }
}


</script>

<template>
 

  <main>
   <div v-if="!user">LOADING</div>
     <div v-else className="profile-container">
        <div className="profile">
          <div className="image">
            <img :src="user?.avatar_url" alt="" />
          </div>
          <div className="profile-details">
            <h1 className="username">{{user?.name}}</h1>
            <p className="fullname">{{user.login}}</p>
             <p className="fullname">{{user?.bio}}</p> 
            <p className="followers">
            
              Followers: <span>{{user?.followers}}</span>
            </p>
            <p className="followers">
             
              Following: <span>{{user.following}}</span>
            </p>
            <p className="public_repos">
              Public repos:{" "}
              <span>{{user.public_repos}}</span>
            </p>
           
          </div>
          </div>
     </div>

   
  </main>

</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
