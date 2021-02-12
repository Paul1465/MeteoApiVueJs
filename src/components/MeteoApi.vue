<template>
  <div class="container">
    <h1 class="my-4">App météo avec Vue.js</h1>
      <div class="form-groupe mb-5">
        <label for="position" class="float-left mt-5">Entrez le nom d'une ville</label>
        <input  id="position"
                type="text"
                class="form-control"
                v-model="requete"
                @keypress.enter="goMeteo"
                >
      </div>
      <div class="w-75 m-auto" v-if="temps">
        <h3 class="text-center">Position: {{temps.name}} </h3>
        <div class="card text-center p-5">
          <p class="texte-affichage">Temperature : {{temps.main.temp.toFixed()}}</p>
          <p class="texte-affichage">Temps : {{temps.weather[0].description}}</p>
        </div>
      </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'MeteoApi',
  data(){
    return {
      requete: '',
      temps: undefined,
      api_code: '0730050c0dd6d59bb9d7bb8373aae15f',
      url_recherche: 'https://api.openweathermap.org/data/2.5/weather?'

    }
  },
  methods: {
    goMeteo(){
        axios
        .get(`${this.url_recherche}q=${this.requete}&units=metric&APPID=${this.api_code}&lang=fr`)
        .then(reponse => {
          this.temps = reponse.data;
        })
        this.requete = ''
    }
  }
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.texte-affichage{
  font-size: 25px;
  font-weight: 300;
  line-height: 1.2;
}
</style>
