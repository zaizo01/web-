<template>
  <div class="container">
    <h1 class="title">Gallery of Rick & Morty</h1>
    <div class="columns is-multiline is-mobile">
      <div
        class="column is-one-quarter"
        v-for="personaje in personajes.results"
        :key="personaje.id">
        <div class="card">
          <div class="card-image">
            <figure class="image is-4by3">
              <img v-bind:src="personaje.image" alt="Placeholder image" />
            </figure>
          </div>
          <div class="card-content">
            <p class="title is-4">{{personaje.name}}</p>
            <div class="content has-text-weight-medium is-size-6">
              <p>Status: {{personaje.status}}</p>
              <p>Species: {{personaje.species}}</p>
              <p>gender: {{personaje.gender}}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      personajes: []
    };
  },
  created() {
    axios.get("https://rickandmortyapi.com/api/character").then(Response => {
      this.personajes = Response.data;
      console.log(Response);
    });
  }
};
</script>

<style scoped>
.columns {
  margin-top: 90px;
}
.title {
  text-align: center;
  margin-top: 25px;
}
</style>>


