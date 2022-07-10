<script type="text/javascript" >
export default{
        data: function () {
        return {
        coins: 0,
        passivecoins: 0.5,
        
        }
     },
     
    methods:{
        scroll(){
            console.log('bunda');
        },
        incrementCounter(){
            this.coins+=1;
        },
        passiveIncrement(){
             setInterval(() => {
        this.coins +=this.passivecoins;
      }, 1000);
        }
    },

}

</script>


<template>
    <div class='mainbox' >
        <section class='clicker_section'>
            <button class="increment_button" v-on:click="incrementCounter"><img src="/button_img.png" alt=""></button>
        </section>
        <section class='points'>
            <p>في القولكناعب ا لنرى >في القولكناعب ا لنرى>في القولكناعب ا لنرى>في القولكناعب ا لنرى>في القولكناعب ا لنرى>في القولكناعب ا لنرى>في القولكناعب ا لنرى</p>
            <h1 class='fonttest'>{{Math.round(coins)}} gold</h1>
            <p>في القولكناعب ا لنرى >في القولكناعب ا لنرى>في القولكناعب ا لنرى>في القولكناعب ا لنرى>في القولكناعب ا لنرى>في القولكناعب ا لنرى>في القولكناعب ا لنر</p>
        </section>
        <section class='passive_table'>
            <div class="upgradebox">
                <div class="upgrade">
                    <p> Standart pack (+1GPS)</p>
                    <button v-on:click="passiveIncrement">BUY</button>
                </div>
                <div class="upgrade">
                    <p> Standart pack (+1GPS)</p>
                    <button v-on:click="passiveIncrement">BUY</button>
                </div>

            </div>
        </section>
       
    </div>
</template>





<style scoped>
.clicker_section{
    margin-top: 20px;
    width: 100%;
    display: flex;
    justify-content: center;

}
.increment_button{
    border: none;
    background-color: transparent;
}
.increment_button img{
    max-height: 150px;
    animation: shiny 1s infinite;

}
@keyframes shiny {
    0%{
        filter: drop-shadow(0px 0px 10px #FFAB1F);
    }
    50%{
        filter: drop-shadow(0px 0px 30px #FFAB1F);
    }
    100%{
        filter: drop-shadow(0px 0px 10px #FFAB1F);
    }
}
@font-face {
    font-family: "myfont";
    src: url("/thefont.ttf");
}
.points{
    position: relative;
    max-width: 100vh;
    height: 130px;
    display: flex;
    overflow: hidden;
    flex-direction: column;
    align-items: center;
    justify-content: space-between;
    overflow:auto;
    background-color: rgba(0, 0, 0, 0.7);
    color: #ffd82a;
    font-size: 18px;

    white-space: nowrap;
    text-shadow: 0 0 20px rgb(11, 239, 255), 0 0 20px rgba(10, 175, 230, 0);

}
.points *{
    position: relative;
    animation: running 1s linear infinite;
    margin: 0;
}
.points p:nth-child(1){
    animation: running 1s linear infinite reverse;
}
.points h1:nth-child(2){
    font-size: 30px;
    position: absolute;
    top: 50%;
    transform: translate(0,-50%);
    animation: none;
}

@keyframes running{
    0%{
        left: 0px;
    }
    100%{
        left: -37%;
    }
}

.passive_table{
    margin-top: 20px;
    width: 100%;
}
.upgradebox{
    width: 60%;
background-color: rgba(0, 0, 0, 0.7);
}
.upgrade{
    position: relative;
    color: yellow;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 5px;

}
.upgrade button{
    font-family: "myfont";
    color: silver;
    background: radial-gradient(ellipse farthest-corner at right bottom, #FEDB37 0%, #FDB931 8%, #9f7928 30%, #8A6E2F 40%, transparent 80%),radial-gradient(ellipse farthest-corner at left top, #FFFFFF 0%, #FFFFAC 8%, #D1B464 25%, #5d4a1f 62.5%, #5d4a1f 100%);
    border: none;
    border-radius: 25%;
    height: 2rem;
}
</style>
