<script>
import newcard from './newcard.vue'

export default{
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
    <div class='cardstore'>
        <img v-on:click="getdata" src="https://www.yugioh-card.com/en/wp-content/uploads/2022/02/TAMA_550.png" alt="">
        <p>1000G</p>
    </div>
    <component :is="newcard" :src='[url]'  v-on:deletar="deletar"></component>
</template>



<style >
.cardstore{
    cursor: pointer;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    max-height: 300px;
    position: relative;
}

.cardstore img{
    padding: 0;
    margin: 0;
    height: 250px;
   
}
.cardstore img:hover{
 filter: drop-shadow(0px -0px 5px #08FF00);
}
.cardstore p{
    position: relative;
    color: yellow;
    background-color: rgba(0, 0, 0, 0.7);
    border: 2px solid rgb(252, 252, 145);
    padding: 10px 20px;
    border-radius: 5rem;
    box-shadow: 1px 1px 5px rgb(0, 217, 255), -1px -1px 5px rgb(0, 217, 255);
    text-align: center;
}
</style>