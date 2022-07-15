<script>
export default{
    props: {
        name: String,      //nome do power up
        coins: Number,     //gold atual para checar se a compra é válida
        Speed: Number,    // velocidade da barrinha. Quando maior mais rápida 
        Price: Number,    //valor do power up
        value: Number,    // Quanto de gold gera a cada ciclo
    },
    data() {
        return {
            Preco: this.Price,
            id: String(Date.now())
        }
    },
     methods: {
        progressbar(){
            if(this.coins>=this.Preco){
                this.Preco = this.Preco + Math.round((25*this.Preco)/100);
                //remover gold
                this.$emit('RemoveGold',{
                        Quantity:this.Price,
                        });

                //ativar barra
                let progressBar = document.getElementById(this.id)
                let interval = setInterval(() => {
                let computedStyle = getComputedStyle(progressBar)
                let width = parseFloat(computedStyle.getPropertyValue('--width')) || 0
                if(width<99){
                progressBar.style.setProperty('--width', width + this.Speed)
                } else {
                        //adicionar gold passivo
                        this.$emit('passiveEarn',{
                            value:this.value,
                            });
                        progressBar.style.setProperty('--width', 0);
                        }
                    }, 1)
                }
        },
    },
}

</script>


<template>
    <div class="upgrade_container" v-on:click="progressbar">
        <div class="upgrade_price"> <p>{{Preco}} G</p></div>
        <div class="name-progressbar">
            <p>{{name}}</p>
            <div class="progress-bar" :id="[id]" style="--width: 0"></div>
        </div>
    </div>
</template>


<style scoped>
.upgrade_container{
    margin-top: 50px;
    display: flex;
    align-items: center;
    width: 90%;
    max-height: 60px;
    background: rgba(0, 128, 157, 0.7);
    border: 3px solid #98E483;
    box-shadow: 1px 1px 5px rgb(0, 217, 255), -1px -1px 5px rgb(0, 217, 255);
    border-radius: 5rem;
    cursor: pointer;
    user-select: none;
}
.upgrade_container:nth-child(1){
    margin-top: 20px;
}
.upgrade_price{
    border-radius: 50%;
    width: 95px;
    height: 95px;
    background: rgba(0, 128, 157, 0.7);
    border: 3px solid #98E483;
    box-shadow: 1px 1px 5px rgb(0, 217, 255), -1px -1px 5px rgb(0, 217, 255);
    margin-left: -10px;
    display: flex;
    justify-content: center;
    align-items: center;
    -webkit-backdrop-filter: blur(10px);
    backdrop-filter: blur(10px);
    color: rgb(252, 255, 79);
    font-size: 20px;
     text-shadow: 1px 1px 1px #000, 
                 1px 1px 5px rgb(0, 217, 255), -1px -1px 5px rgb(0, 217, 255)
}
.name-progressbar{
    width: 65%;
    font-size: 20px;
    color: rgb(151, 255, 177);
     text-shadow: 1px 1px 1px #000, 
                 1px 1px 5px rgb(0, 217, 255), -1px -1px 5px rgb(0, 217, 255)
}
.progress-bar {
	position: relative;
	width: 100%;
	height: 1em;
	background-color: rgb(255, 255, 238);
	border-radius: 1.5em;
}

.progress-bar::before {
	content: attr(data-label);
	display: flex;
	align-items: center;
	position: absolute;
	left: .1em;
	top: .15em;
	bottom: .1em;
	width: calc(var(--width, 0) * 1%);
	min-width: 0;
	max-width: 100%;
	background-color: aqua;
	border-radius: 1em;
	padding: 0;
}
</style>