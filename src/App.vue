<template>
  <div id="app" class="row justify-content-center" style="margin-top: 10%;">
    <Card emocao="Triste" :img="`${publicPath}img/triste.jpg`" :audio="`${publicPath}audio/triste.mp3`" v-if="recebido.id == 'triste'">
    </Card>
    <Card emocao="Alegre" :img="`${publicPath}img/sorrisoteste.png`" :audio="`${publicPath}audio/sorriso.mp3`" v-if="recebido.id == 'alegre'">
    </Card>
    <Card emocao="Trimemória" :img="`${publicPath}img/logo.png`" v-if="recebido.id == 'Vazio'">
    </Card>
  </div>
</template>

<script>
import axios from 'axios'
import Card from './components/Card.vue'

export default {
  components:{Card},
  data(){
    return{
      recebido: {id: 'Vazio' , index: -1},
      publicPath: process.env.BASE_URL
    }
  },
  created(){
    setInterval(() =>{
      var enviar = this.recebido.index + 1;
      axios.get('http://localhost:3035/achado/' + enviar).then(response => {
        console.log(response.data)
        this.recebido = response.data
      }).catch(function (error) {
        // handle error
        console.log(error);
      })
    }, 20000)
  }
}
</script>

<style>
</style>
