<template>
  
    <Carrusel/>

    <div class="c1 container p-3 mt-3 ">

    <div class="c2 container" id="im"  style="display: block">
       <div class="row">
       <div class="col-12 col-sm-6 col-md-4 col-lg-4 col-xl-3"  v-for="empresa in empresas" :key="empresa.id"> 
      
           <div href="producto.vue" class="btn card m-1">  
            <img :src="'http://localhost:1337'+empresa.img.url" alt="" id="image" class="card-img-top" >
              <div class="card-body">  
               <p> {{ empresa.nombre }} </p>
               <p> Nombre: {{ empresa.nempresa }} </p>
               </div>
            </div>
       </div>
       </div>
    </div>

  </div>

</template>



<script>

import axios from 'axios'; 
import Carrusel from '@/components/Carrusel.vue'


export default {
        name: "home",
     props:{
        nav: "",
    },
    data(){
        return{
            empresas: [],
        }
    },
    components:{
        Carrusel,
    },


    mounted() {

        axios.get("http://localhost:1337/empresas")
        .then((res) => {
            this.empresas = res.data;
        });
         
    },
    

}
</script>