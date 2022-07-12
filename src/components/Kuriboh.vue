<script type="text/javascript" >

import Upgrades from './Upgrades.vue';

export default{

        components: {
            Upgrades
        },
        data: function () {
        return {
        coins: 0,
        passivecoins: 0.01,
        clickvalue: 1,
        }
        },
    methods:{
        incrementCounter(){
            this.coins+=this.clickvalue;
            let elem = document.createElement("h1");
            elem.setAttribute('class','pointnumber')
            elem.innerHTML = '+'+this.clickvalue;
            document.getElementById('leftside_container').appendChild(elem);
            setTimeout(()=>{elem.remove()},700)
        },
        passiveIncrement(){
             setInterval(() => {
        this.coins +=this.passivecoins;
            }, 100);
        },
        incressClickValue(value){
            this.clickvalue+=value.value;
        }
    },
}

</script>
<template>
<div class="main_container">
    <section class="leftside_container" id='leftside_container' >
            <button v-on:click="incrementCounter" ><img src="https://i.pinimg.com/originals/a3/28/77/a328772218affb0a03c8d70fff1fa104.png" alt="kuribohclick" ></button>
            <div class="coinsdiv">
                <p>𓀕 𓀖 𓀗 𓀘 𓀙 𓀚 𓀛 𓀜 𓀝 𓀞 𓀟 𓀠 𓀡 𓀢 𓀣 𓀤 𓀥 𓀦 𓀧 𓀨 𓀩 𓀪 𓀫 𓀬 𓁇 𓁈 𓁉 𓁊 𓁋 𓀕 𓀖 𓀗 𓀘 𓀙 𓀚 𓀛 𓀜 𓀝 𓀞 𓀟 𓀠 𓀡 𓀢 𓀣 𓀤 𓀥 𓀦 𓀧 𓀨 𓀩 𓀪 𓀫 𓀬 𓁇 𓁈 𓁉 𓁊 𓁋</p>
                <h3>{{Math.round(coins)}} GOLD</h3>
                <p>𓀕 𓀖 𓀗 𓀘 𓀙 𓀚 𓀛 𓀜 𓀝 𓀞 𓀟 𓀠 𓀡 𓀢 𓀣 𓀤 𓀥 𓀦 𓀧 𓀨 𓀩 𓀪 𓀫 𓀬 𓁇 𓁈 𓁉 𓁊 𓁋 𓀕 𓀖 𓀗 𓀘 𓀙 𓀚 𓀛 𓀜 𓀝 𓀞 𓀟 𓀠 𓀡 𓀢 𓀣 𓀤 𓀥 𓀦 𓀧 𓀨 𓀩 𓀪 𓀫 𓀬 𓁇 𓁈 𓁉 𓁊 𓁋</p>
            </div>
    </section>
    <Upgrades v-on:incressPassiveSignal='passiveIncrement' v-on:incressClickSignal='incressClickValue'/>
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
@media only screen and (max-width: 600px) {
  .leftside_container {
    width: 100%;
  }
}
    
</style>
