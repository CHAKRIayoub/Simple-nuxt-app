<template>
    <div class="container" >
        <h2>liste des Produits : </h2>
        <div v-for="product in products" >
            <div class="panel panel-default">
                <div class="panel-heading"></div>
                <div class="panel-body">
                    <h5> {{ product.name }} {{ product.slug }} </h5>
                    <span>type : {{ product.type }} </span><br>
                    <span>Prix : {{ product.sale_price }} </span><br>
                </div>
                <div class="panel-footer"></div>
            </div>
        </div>
    </div>
</template>

<script>
    import axios from 'axios';

    export default {
   
        asyncData ({ params }) {
    
            return axios.get('http://127.0.0.1:8000/api/products/get_all')
                        .then((response) => {
                            return { products : response.data }    
                        })
            ; 

        }

    }
</script>


<style lang="css" >
  @import url(/bootstrap.min.css);
</style>
