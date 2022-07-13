<script>
export default({
    props: {
        name: String,      //nome do power up
        coins: Number,     //gold atual para checar se a compra é válida
        Speed: Number,    // velocidade da barrinha. Quando maior mais rápida 
        Price: Number,    //valor do power up
        Value: Number,    // Quanto de gold gera a cada ciclo
    },
    data() {
        return {
            Preco: this.Price,
            id: String(Date.now())
        }
    },
    methods: {
        progressbar(){
            console.log(this.id)
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
                            value:this.Value,
                            });
                        progressBar.style.setProperty('--width', 0);
                        }
                    }, 1)
                }
        },
    },
})
</script>

<template>
    <div class="upgrade-container">
        <div class="name-progressbar">
            <h2>{{name}}</h2>
            <div class="progress-bar" :id="[id]" style="--width: 0"></div>
        </div>
        <div class="price-button">
            <button v-on:click="progressbar">COMPRAR</button>
            <h2>{{Preco}}G</h2>
        </div>
    </div>
</template>


<style>
.upgrade-container{
    position: relative;
    width: 95%;
    color: white;
    background-color: rgba(0, 0, 0, 0.7);
    border: 2px solid rgb(252, 252, 145);
    padding: 10px 20px;
    border-radius: 5rem;
    box-shadow: 1px 1px 5px rgb(0, 217, 255), -1px -1px 5px rgb(0, 217, 255);
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin: 30px 0;
}



.name-progressbar{
    width: 70%;
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
	top: .1em;
	bottom: .1em;
	width: calc(var(--width, 0) * 1%);
	min-width: 0;
	max-width: 100%;
	background-color: aqua;
	border-radius: 1em;
	padding: 0;
}
.price-button {
    width: 35%;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 15px;
}
.price-button button{
    border:none;
    border-radius: 25%;
    padding: 6px;
    color: white;
     background: radial-gradient(ellipse farthest-corner at right bottom, #FEDB37 0%, #FDB931 8%, #9f7928 30%, #8A6E2F 40%, transparent 80%),
                radial-gradient(ellipse farthest-corner at left top, #FFFFFF 0%, #FFFFAC 8%, #D1B464 25%, #5d4a1f 62.5%, #5d4a1f 100%);
    cursor: pointer;
}

.price-button h2{
    position: absolute;
    right: 50px;
    bottom: -20px;
    font-size: 18px;
    background-color: rgba(0, 0, 0, 0.7);
    border: 2px solid rgb(252, 252, 145);
    border-radius: 5rem;
    padding: 5px 10px;
    box-shadow: 1px 1px 5px rgb(0, 217, 255), -1px -1px 5px rgb(0, 217, 255);
    -webkit-backdrop-filter: blur(100%) !important;
    backdrop-filter: opacity(110%) !important;
}
</style>