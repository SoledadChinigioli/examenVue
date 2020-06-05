<template>
  <div class="home">

     <table>
     <tr >
       <td>
          <b-form-input size="sm" v-model="search" class="mr-sm-2" placeholder="Buscar"></b-form-input>
      </td>
       <td>
         <b-button size="sm" class="my-2 my-sm-0" type="submit">Buscar</b-button>
       </td>
     </tr>
    </table>

    <strong><h1 style = "font-family:Comic Sans" align='center'>HÉROES</h1></strong>

    <h4 align='center'>Los Héroes de tu infancia ahora los tenemos nosotros.</h4>
    
     <div class='home'>
      
    <b-container fluid>
      <b-card-group deck>
        <div
          v-for="heroe in filteredheroe"
          :key="heroe.id"
          style='margin-top:15px'
        >
          <heroe-item :heroeParam="heroe"></heroe-item>
          
        </div>
      </b-card-group>
      <br />
      <b-button href='/' variant='dark' align='right'>IR A HOME</b-button>
    </b-container>
  </div>
    </div>

    
</template>

<script>
import Heroes from '@/components/Heroes.vue'

export default {
  name: 'Home',
  components: {
    'heroe-item': Heroes
  },
  mounted () {
    if(this.$route.params.id){
    
      this.getHeroeXCasa()
    }else{
    this.getHeroe()}

  }, 
  data () {
    return {
      heroeData: [],
      search: ''
    }
  },
  methods: {
    async getHeroe () {
      const res = await fetch('/heroe.json')
      const resJson = await res.json()
      this.heroeData = resJson.Heroes
    },
    async getHeroeXCasa (){
     
        const casa = this.$route.params.id
        const res = await fetch('/heroe.json')
        const resJson = await res.json()
        this.heroeData = await resJson.Heroes.filter(
          heroe => heroe.casa.toLowerCase().match(casa.toLowerCase()
          ))
          
    }
  },
  computed: {
    filteredheroe: function(){
      return this.heroeData.filter((heroe)=>{
        return heroe.nombre.toLowerCase().match(this.search.toLowerCase())
      });
    }

  }
}
</script>
