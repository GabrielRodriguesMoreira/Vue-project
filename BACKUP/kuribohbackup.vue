<script type="text/javascript" >

import Upgrade from './Upgrade.vue';
import BoosterStore from './BoosterStore.vue';



export default{

        components: {
            Upgrade,
            BoosterStore
        },
        data: function () {
        return {
        coins: 100000,
        }
        },
    methods:{
        incrementCounter(clickvalue){
            this.coins+=clickvalue;
            let elem = document.createElement("h1");
            elem.setAttribute('class','pointnumber');
            elem.innerHTML = '+'+ clickvalue;
            document.getElementById('leftside_container').appendChild(elem);
            setTimeout(()=>{elem.remove()},700)
        },
        convert(objvalue){
             this.incrementCounter(objvalue.value);
        },
        GoldRemove(quantity){
            this.coins-=quantity.Quantity;
        }
    }
}

</script>
<template>
<div class="main_container">
    <section class="leftside_container" id='leftside_container' >
            <button v-on:click="incrementCounter(1)" ><img src="https://i.pinimg.com/originals/a3/28/77/a328772218affb0a03c8d70fff1fa104.png" alt="kuribohclick" ></button>
            <div class="coinsdiv">
                <p>𓀕 𓀖 𓀗 𓀘 𓀙 𓀚 𓀛 𓀜 𓀝 𓀞 𓀟 𓀠 𓀡 𓀢 𓀣 𓀤 𓀥 𓀦 𓀧 𓀨 𓀩 𓀪 𓀫 𓀬 𓁇 𓁈 𓁉 𓁊 𓁋 𓀕 𓀖 𓀗 𓀘 𓀙 𓀚 𓀛 𓀜 𓀝 𓀞 𓀟 𓀠 𓀡 𓀢 𓀣 𓀤 𓀥 𓀦 𓀧 𓀨 𓀩 𓀪 𓀫 𓀬 𓁇 𓁈 𓁉 𓁊 𓁋</p>
                <h3>{{Math.round(coins)}} GOLD</h3>
                <p>𓀕 𓀖 𓀗 𓀘 𓀙 𓀚 𓀛 𓀜 𓀝 𓀞 𓀟 𓀠 𓀡 𓀢 𓀣 𓀤 𓀥 𓀦 𓀧 𓀨 𓀩 𓀪 𓀫 𓀬 𓁇 𓁈 𓁉 𓁊 𓁋 𓀕 𓀖 𓀗 𓀘 𓀙 𓀚 𓀛 𓀜 𓀝 𓀞 𓀟 𓀠 𓀡 𓀢 𓀣 𓀤 𓀥 𓀦 𓀧 𓀨 𓀩 𓀪 𓀫 𓀬 𓁇 𓁈 𓁉 𓁊 𓁋</p>
            </div>
    </section>

    <div class="rightside_container">
        <section class="upgrades-container" >
            <Upgrade 
                    name="Power UP 1"
                    :coins=coins
                    :Speed=0.1
                    :Price=50
                    :Value=3
                    v-on:passiveEarn="convert" v-on:RemoveGold="GoldRemove"
            />
            <Upgrade 
                    name="Power UP 2"
                    :coins=coins
                    :Speed=0.05
                    :Price=500
                    :Value=5
                    v-on:passiveEarn="convert" v-on:RemoveGold="GoldRemove"
            />
            <Upgrade 
                    name="Power UP 3"
                    :coins=coins
                    :Speed=1.
                    :Price=1000
                    :Value=1
                    v-on:passiveEarn="convert" v-on:RemoveGold="GoldRemove"
            />
            <Upgrade 
                    name="Power UP 3"
                    :coins=coins
                    :Speed=1.
                    :Price=1000
                    :Value=1
                    v-on:passiveEarn="convert" v-on:RemoveGold="GoldRemove"
            />
            <Upgrade 
                    name="Power UP 3"
                    :coins=coins
                    :Speed=1.
                    :Price=1000
                    :Value=1
                    v-on:passiveEarn="convert" v-on:RemoveGold="GoldRemove"
            />
            <Upgrade 
                    name="Power UP 3"
                    :coins=coins
                    :Speed=1.
                    :Price=1000
                    :Value=1
                    v-on:passiveEarn="convert" v-on:RemoveGold="GoldRemove"
            />
        </section>
        <section class='booster-container'>
            <BoosterStore :coins='[coins]' v-on:cobrar='GoldRemove' />
        </section>
    </div>
</div>
</template>


<style >
@font-face {
    font-family: 'myfont';
    src: url('/thefont.ttf');
}
.main_container{
min-width: 100vw;
min-height: 100vh;
width: 100%;
height: 100%;
display: flex;
justify-content: space-between;
}
.leftside_container{
    width: 50%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}
.leftside_container button{
 background-color: transparent;
 border: none;
 width: 80%;
 cursor: pointer;
 -webkit-tap-highlight-color: transparent;
}
.leftside_container button img{
    width: 100%;
    object-fit: scale-down;
    filter: drop-shadow(5px -4px 0px #08FF00);
}
.leftside_container button img:active{
    transform: scale(98%);
}
.coinsdiv{
    overflow: hidden;
    display: flex;
    flex-direction: column;
    justify-content: center;
    color: white;
    white-space: nowrap;
    width: 60%;
    max-height: 100px;
   background: linear-gradient(90deg, rgba(0,0,0,0) 0%, rgba(0,0,0,0.75) 17%, rgba(0,0,0,1) 50%, rgba(0,0,0,0.75) 75%, rgba(0,0,0,0) 100%);
    color: yellow;
    text-shadow: 1px 1px 1px #000, 
                 1px 1px 5px rgb(0, 217, 255), -1px -1px 5px rgb(0, 217, 255)
}
.coinsdiv p{
    animation: slidetext 5s infinite linear;
    }
.coinsdiv p:nth-child(1){
    animation: slidetext 5s infinite linear reverse;
}
.coinsdiv h3{
    margin: 5px;
    text-align: center;
    font-size: 30px;
}
@keyframes slidetext {
  from {
    left: 0;
    transform: translateX(0);
  }
  to {
     left: 100%; 
    transform: translateX(-100%);
  }
}
.pointnumber{
    font-size: 35px;
    position: absolute;
    top: 100px;
    animation: up .7s forwards;
color: yellow;
    text-shadow: 1px 1px 1px #000, 
                 1px 1px 5px rgb(0, 217, 255), -1px -1px 5px rgb(0, 217, 255)
}
@keyframes up {
    0%{

    }
    100%{
        transform: translateY(-20px);
    }
}

.rightside_container{
    max-height: 100vh;
    width: 35%;
    padding-top: 10px;
}




.upgrades-container{
    max-height: 300px;
    background-color: rgba(0, 33, 82, 0.3);
    border-radius: 0.4rem;
    overflow: auto;
}

@media only screen and (max-width: 600px) {
  .leftside_container {
    width: 100%;
  }
}

</style>
