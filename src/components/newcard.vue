<script>
export default({
    props: {
        src: String
    },
    methods: {
        emitir(){
            this.$emit('deletar')
        }
    },
})

</script>

<template >
<div>
    <div class="box" v-on:click='emitir' id='id' >
        <div class="placeholder"></div>
        <img :src='[src]' alt="asdads">

    </div>
</div>
</template>


<style>
.box{
    top:0;
    left: 0;
    position: fixed;
    width: 100vw;
    height: 100vh;
    background-color: rgba(0, 0, 0, 0.5);
    display: flex;
    justify-content: center;
    align-items: center;
}
.box img,
.box .placeholder{
    position: fixed;
    height: 90%;

}
.box .placeholder{
    background-image: url('cardback.jpg');
    background-size: cover;
    aspect-ratio: 1/1.45;
}
</style>