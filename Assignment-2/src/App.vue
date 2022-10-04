<script setup>
import { ref, onMounted } from "vue";
import axios from "axios";

const user = ref({});
onMounted(async () => {
  const response = await axios.get("https://api.github.com/users/devisasari");
  user.value = response.data;
});
</script>

<template>
  <div id="app">
    <div class="container">
      <div class="row">
        <div class="col-md-12">
          <div class="card">
            <div class="card-body">
              <div class="row">
                <div class="col-md-3">
                  <img :src="user.avatar_url" class="img-fluid" />
                </div>
                <div class="col-md-9">
                  <h1>Name: {{ user.name }} </h1>
                  <p>Bio: {{ user.bio }}</p>
                  <p>Location: {{ user.location }}</p>
                  <p>Company: {{ user.company }}</p>
                  <p>Public Repos: {{ user.public_repos }}</p>
                  <p>Public Gists: {{ user.public_gists }}</p>
                  <p>Followers: {{ user.followers }}</p>
                  <p>Following: {{ user.following }}</p>
                  <p>Latest Update: {{ user.updated_at }}</p>
                  <p>
                    <a :href="user.html_url" target="_blank" class="btn btn-primary">View Profile</a>
                  </p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#github-profile {
  margin-top: 100px;
}

#github-profile img {
  width: 150px;
  border-radius: 50%;
  border: 2px solid #000;
}
</style>
