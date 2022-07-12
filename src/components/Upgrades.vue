<script>
export default({
    methods: {
        incressPassive(){
            console.log('click');
            this.$emit('incressPassiveSignal');
        },
        incressClick(){
            this.$emit('incressClickSignal',{
                value: 1,
               
            });
             console.log('Click');
        }
    },
})
</script>

<template>
<div class="main_upgrades_container">
    <div class="Upgrades">
        <div class='Upgrade'>
            <h3>Aumentar valor do click:</h3>
            <p>100G</p>
            <button v-on:click="incressClick">Comprar</button>
            
        </div>
        <div class='Upgrade'>
            <h3>Automatizar ganhos</h3>
            <p>100G</p>
            <button v-on:click="incressPassive">Comprar</button>
        </div>
    </div>
    <div class="Booster"></div>
</div>
</template>


<style>

.main_upgrades_container{
    width: 30%;
    background-color: rgb(100, 26, 26);
}
.Upgrade{
    display: flex;
}
</style>