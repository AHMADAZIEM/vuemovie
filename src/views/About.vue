<template>
  <div class="about">
    <input type="text" v-model="title" />
    <button type="button" @click="getMovies" class="btn btn-primary ml-2">Search</button>

    <h1>This is an about page</h1>
    <table class="table">
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">Title</th>
          <th scope="col">Last</th>
          <th scope="col">Handle</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in movies" :key="index">
          <th scope="row">{{index+1}}</th>
          <td>{{item.title}}</td>
          <td>Otto</td>
          <td>@mdo</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<script>
import axios from 'axios'
export default {
  data() {
    return {
      movies: [],
      title: ''
    }
  },
  methods: {
    getMovies (){
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=66e5b6a4070ff03bb075dd2b8a75773c&language=en-US&query=${this.title}&page=avenger&include_adult=false`)
        .then(res => {
          
          this.movies = res.data.results
          console.log('movie ',this.movies)
        })
    }
    
  },
}
</script>>