<script>
import newcard from './newcard.vue'

export default {
props: {
        coins: Number,
    },
    components:{
            newcard
    },
    data(){
        return{
            ibagem: String,
            newcard: null,
            data: Object,
            url: String,
        }
    },
    mounted(){
         fetch('https://db.ygoprodeck.com/api/v7/randomcard.php')
        .then((res) => res.json())
        .then(data => this.data = data)
    },
    methods: {
        getdata(){
            if(this.coins>=1000){
                this.$emit('cobrar',{
                    Quantity: 1000
                });
            fetch('https://db.ygoprodeck.com/api/v7/randomcard.php')
            .then((res) => res.json())
            .then(data => this.data = data)
                this.url = String(this.data.card_images[0].image_url)
                this.newcard = 'newcard'
                        
            }

        },
        deletar(){
            this.newcard = null;
        }

    }
}
</script>


<template>
    <div class="main_store_container">

        <div class="StorePrice">
            <h1>1000 G</h1>
            <button v-on:click="getdata"> COMPRAR</button>
        </div>
        <div class="storeimg">
            <img src="https://firescroll.net/wp-content/uploads/2022/02/YGO-Battles-of-Chaos.png" alt="">
        </div>
        
    </div>
    <component :is="newcard" :src='[url]'  v-on:deletar="deletar"></component>
</template>


<style scoped>
.main_store_container{
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px;
    width: 100%;
    height: 100%;
    background: #00809D;
    border: 3px solid #98E483;
    box-shadow: 1px 1px 5px rgb(0, 217, 255), -1px -1px 5px rgb(0, 217, 255);
    border-radius: 15px;
}
.storeimg img{
    max-height: 200px;
    -webkit-transform: scaleX(-1);
  transform: scaleX(-1);
}
.StorePrice{
    margin-left: 30px;
    height: 100%;
    width: 40%;
    text-align: center;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    align-items: center;
    font-size: 25px;
    color: rgb(226, 252, 78);
     text-shadow: 1px 1px 1px #000, 
                 1px 1px 5px rgb(0, 217, 255), -1px -1px 5px rgb(0, 217, 255)
    
}
.StorePrice button{
    border: none;
    background: hwb(107 15% 16%);
    border-radius: 15px;
    color: white;
    width: 100%;
    height: 40%;
    font-size: 30px;
    cursor: pointer;
}
</style>