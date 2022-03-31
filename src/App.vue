<script>
//vuein for snippet
import Home from './components/Home.vue'
import About from './components/About.vue'
import Count from './components/CountNumber.vue'
import ApiGet from './components/ApiGet.vue'
import ApiPost from './components/ApiPost2.vue'
import NotFound from './components/NotFound.vue'


const routes = {
  '/': Home,
  '/about': About,
  '/count': Count,
  '/apiGet': ApiGet,
  '/apiPost': ApiPost
}

export default {
  data() {
    return {
      currentPath: window.location.hash
    }
  },
  computed: {
    currentView() {
      return routes[this.currentPath.slice(1) || '/'] || NotFound
    }
  },
  mounted() {
    window.addEventListener('hashchange', () => {
		  this.currentPath = window.location.hash
		})
  }
}


</script>

<template>
  <!-- <div id="top-bar">
    <a href="#/">Home</a> |
    <a href="#/about">About</a> |
    <a href="#/count">Count</a> |
    <a href="#/non-existent-path">Broken Link</a> 
  </div> -->

  <ul class="nav justify-content-end">
  <li class="nav-item">
    <a class="nav-link active" aria-current="page" href="#/">Home</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" aria-current="page" href="#/about">About</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" aria-current="page" href="#/count">Count</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" aria-current="page" href="#/apiGet">Api Get</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" aria-current="page" href="#/apiPost">Api Post</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" aria-current="page" href="#/non-existent-path">Broken Page</a>
  </li>
</ul>

  <component :is="currentView" />
  
</template>

<style>
#top-bar {
  background-color: #134245;
  height: 30px;
}

</style>
