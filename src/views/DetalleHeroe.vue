<template>
  <div>
    <b-container fluid>
        <b-row>
          <b-col> <img
            style='max-height:400px'
            :src="'/img/' + heroeEncontrado.img"
        /><br /><br />
         </b-col>
         <b-row>
            <b-col><h4>Biografía: {{ heroeEncontrado.bio }}</h4></b-col>
          </b-row>
        
        
            <b-row>
            <b-col><h6>Aparición: {{ heroeEncontrado.aparicion}}</h6></b-col>
          </b-row>
            <b-row>
            <b-col><h1><strong>{{ heroeEncontrado.nombre }}</strong></h1></b-col>
          </b-row>
           <b-row>
            <b-col> <span style='color:red'> Poderes: </span>
            <br />
                <li  v-for="(poder, index) in heroeEncontrado.poderes"
                :key="index">{{poder}}</li>
            </b-col>
          </b-row>
           
          
          </b-row>
      
          <b-row style='text-align:left'>
            <b-col>
                <b-button href='/home' variant='outline-info'
                >VOLVER</b-button></b-col>
             <b-col>
            <b-button href='/' variant='outline-success'></b-button>
              </b-col>
          </b-row>
      
    </b-container>
  </div>
</template>

<script>
export default {
    name: 'DetalleHeroe',
    components: {},
    mounted () {
        this.getHeroeXId()
    },
    data () {
        return{
            heroeEncontrado: []
        }
    },
    methods: {
        async getHeroeXId () {
            const parametroId = this.$route.params.id
            const res = await fetch('/heroe.json')
            const resJson = await res.json()
            console.log(resJson)
            this.heroeEncontrado = await resJson.Heroes.find(
                heroe => heroe.id === parametroId
            )
            console.log(this.heroeEncontrado)
        }
    }
}
</script>>
