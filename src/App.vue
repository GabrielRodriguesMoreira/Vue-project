<script>
import Kuriboh from './components/Kuriboh.vue'
import Upgrade from './components/Upgrade.vue'
import BoosterStore from './components/BoosterStore.vue'

export default {
  components: {
    Kuriboh,
    Upgrade,
    BoosterStore
  },
  data(){
    return{
      coins: 0,
    }
  },
  methods: {
          goldclick(clickvalue){
              this.coins+=clickvalue
            let elem = document.createElement("h1");
            elem.setAttribute('class','pointnumber');
            elem.innerHTML = '+'+ clickvalue;
            document.getElementById('kuriboh').appendChild(elem);
            setTimeout(()=>{elem.remove()},700)
          },
          GoldRemove(quantity){
            this.coins-=quantity.Quantity;
        },
        PassiveGold(value){
          this.coins+=value.value;
          let elem = document.createElement("h1");
            elem.setAttribute('class','pointnumber');
            elem.innerHTML = '+'+ value.value;
            document.getElementById('kuriboh').appendChild(elem);
            setTimeout(()=>{elem.remove()},700)
        }
      }
}
</script>


<template  >
<div class="main_cointaner" id="master" >
  <section class="left_section" >
    <Kuriboh :coins=coins v-on:kuribohclick="goldclick" id='kuriboh'/>
    <div class='coins' v-on:click="calmo">
      <p>𓀕 𓀖 𓀗 𓀘 𓀙 𓀚 𓀛 𓀜 𓀝 𓀞 𓀟 𓀠 𓀡 𓀢 𓀣 𓀤 𓀥 𓀦 𓀧 𓀨 𓀩 𓀪 𓀫 𓀬 𓁇 𓁈 𓁉 𓀕 𓀖 𓀗 𓀘 𓀙 𓀕 𓀖 𓀗 𓀘 𓀙 𓀚 𓀛 𓀜 𓀝 𓀞 𓀟 𓀠 𓀡 𓀢 𓀣 𓀤 𓀥 𓀦 𓀧 𓀨 𓀩 𓀪 𓀫 𓀬 𓁇 𓁈 𓁉 𓀕 𓀖 𓀗 𓀘 𓀙</p>
      <h3>{{coins}} G</h3>
      <p>𓀕 𓀖 𓀗 𓀘 𓀙 𓀚 𓀛 𓀜 𓀝 𓀞 𓀟 𓀠 𓀡 𓀢 𓀣 𓀤 𓀥 𓀦 𓀧 𓀨 𓀩 𓀪 𓀫 𓀬 𓁇 𓁈 𓁉 𓀕 𓀖 𓀗 𓀘 𓀙 𓀕 𓀖 𓀗 𓀘 𓀙 𓀚 𓀛 𓀜 𓀝 𓀞 𓀟 𓀠 𓀡 𓀢 𓀣 𓀤 𓀥 𓀦 𓀧 𓀨 𓀩 𓀪 𓀫 𓀬 𓁇 𓁈 𓁉 𓀕 𓀖 𓀗 𓀘 𓀙</p>
    </div>
  </section>
  <section class="right_section" >
    <div class='Upgrades'>
      <Upgrade
        name="Power UP 1"
        :coins=coins
        :Speed=0.3
        :Price=50
        :value=3
        v-on:passiveEarn="PassiveGold" v-on:RemoveGold="GoldRemove"
      />
      <Upgrade
        name="Power UP 2"
        :coins=coins
        :Speed=0.8
        :Price=100
        :value=5
        v-on:passiveEarn="PassiveGold" v-on:RemoveGold="GoldRemove"
      />
      <Upgrade
        name="Power UP 3"
        :coins=coins
        :Speed=0.1
        :Price=300
        :value=20
        v-on:passiveEarn="PassiveGold" v-on:RemoveGold="GoldRemove"
      />
      <Upgrade
        name="Power UP 4"
        :coins=coins
        :Speed=0.5
        :Price=1000
        :value=100
        v-on:passiveEarn="PassiveGold" v-on:RemoveGold="GoldRemove"
      />
      <Upgrade
        name="Power UP 5"
        :coins=coins
        :Speed=0.9
        :Price=5000
        :value=500
        v-on:passiveEarn="PassiveGold" v-on:RemoveGold="GoldRemove"
      />
    </div>
    <div class='store'>
      <BoosterStore 
        :coins=coins
        v-on:cobrar="GoldRemove"
      />
    </div>
  </section>
</div>
</template>


<style>
body{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  background: linear-gradient(270deg, #355C7D 0%, #6C5B7B 47.99%, #C06C84 100%); 
}
body *{
font-family: 'Montserrat', sans-serif;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body *::-webkit-scrollbar-track{ 
  box-shadow: none;
	-webkit-box-shadow: inset 0 0 6px rgba(0,0,0,0.3);
	background-color: #F5F5F5;
}
body *::-webkit-scrollbar{
	width: 6px;
	background-color: #F5F5F5;
}
body *::-webkit-scrollbar-thumb{
	background-color: #000000;
}
.main_cointaner{
  display: flex;

}
.left_section, .right_section{
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-around;
  min-height: 100vh;
  height: 100%;
  width: 50%;
  position: relative;
}

/* Contador de Dinheiro */
.coins{

    overflow: hidden;
    display: flex;
    flex-direction: column;
    justify-content: center;
    color: white;
    white-space: nowrap;
    width: 60%;
    max-height: 130px;
   background: linear-gradient(90deg, rgba(0,0,0,0) 0%, rgba(0,0,0,0.75) 17%, rgba(0,0,0,1) 50%, rgba(0,0,0,0.75) 75%, rgba(0,0,0,0) 100%);
    color: yellow;
    text-shadow: 1px 1px 1px #000, 
                 1px 1px 5px rgb(0, 217, 255), -1px -1px 5px rgb(0, 217, 255)
}
.coins h3{
    margin: 10px;
    text-align: center;
    font-size: 35px;
}
.coins p{
      font-size: 14px;
          animation: slidetext 5s infinite linear;
    }
.coins p:nth-child(1){
    animation: slidetext 5s infinite linear reverse;
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

.Upgrades, .store{
  position:initial;
  display: flex;
  flex-direction: column;
  width: 90%;
  height: 60vh;
  overflow: auto;
  padding: 10px;
  background-color: rgba(0, 0, 0, 0.2);
  border-radius: 0.3rem;
}
.store{
height: 40vh;
align-items: center;
background-color: transparent;
}
.pointnumber{
    font-size: 35px;
    position: absolute;
    transform: translateY(-15%);
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



@media only screen and (max-width: 800px) {
.main_cointaner{
  flex-direction: column;
  align-items: center;
}
.left_section, .right_section{
  width: 100%;
}
}
</style>
