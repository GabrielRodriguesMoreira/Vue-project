<script>
export default{
    data(){
        return{
        clickvalue: 1,
        }
    },
    methods: {
        emitclick(){
            this.$emit('kuribohclick',this.clickvalue)
        }
    }
}
</script>

<template>
<div class="main_kuriboh_container">
    <img src="/kuriboh.png" alt="kuriboh img" v-on:click="emitclick">
    <div class="kuriboh_upgrade">
        <div class="kuriboh_level">
            <p>LV    1</p>
        </div>
        <p>Kuriboh <br /> +1  Gold por Click</p>
    </div>
</div>
</template>

<style scoped>

.main_kuriboh_container{
    display: flex;
    position: relative;
    align-items: center;
    flex-direction: column;
}
.main_kuriboh_container img{
    width: 80%;
    margin-bottom: 20px;
    cursor: pointer;
}
.main_kuriboh_container img:active{
    transform: scale(98%);
}
.kuriboh_upgrade{
    display: flex;
    align-items: center;
    width: 60%;
    max-height: 70px;
    background: rgba(0, 128, 157, 0.7);
    border: 3px solid #98E483;
    box-shadow: 1px 1px 5px rgb(0, 217, 255), -1px -1px 5px rgb(0, 217, 255);
    border-radius: 5rem;
}
.kuriboh_upgrade p{
    margin-left: 20px;
    font-size: 18px;
    text-align: center;
    color: rgb(151, 255, 177);
     text-shadow: 1px 1px 1px #000, 
                 1px 1px 5px rgb(0, 217, 255), -1px -1px 5px rgb(0, 217, 255)
}

.kuriboh_level{
    border-radius: 50%;
    width: 120px;
    height: 120px;
    background: rgba(0, 128, 157, 0.7);
    border: 3px solid #98E483;
    box-shadow: 1px 1px 5px rgb(0, 217, 255), -1px -1px 5px rgb(0, 217, 255);
    margin-left: -10px;
    display: flex;
    justify-content: center;
    align-items: center;
    -webkit-backdrop-filter: blur(10px);
    backdrop-filter: blur(10px);
}
.kuriboh_level p{
    margin: 0;
    font-size: 30px;
}

</style>