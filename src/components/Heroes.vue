<template>
 <div>
  <b-card
    tag='article'
    style='max-width: 20rem; min-width: 20rem'
    class='mb-2'
  >
    <b-card-img
      :src="'/img/' + heroeParam.img"
        alt='Image'
        style='min-height:200px; max-height:200px'
    ></b-card-img>
    <b-card-title :title="heroeParam.nombre"></b-card-title>
          <b-card-text>
           <span style='color:red'> Poderes: </span>
           <li  v-for="(poder, index) in heroeParam.poderes"
                :key="index">{{poder}}</li>
    </b-card-text>
     <div style='text-align:center'>
        <b-button
          :href="'/detalleHeroe/' + heroeParam.id"
          variant='primary'
          style='width:100%'>
            <b>Detalle</b>
        </b-button>
      </div>
  </b-card>
  </div>
</template>

<script>
export default {
    props: ['heroeParam']
}
</script>
<style lang=''></style>