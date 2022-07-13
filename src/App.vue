<script setup>
import Kuriboh from './components/Kuriboh.vue'
import Upgrade from './components/Upgrade.vue';
</script>
<template > 
  <Kuriboh/>
</template>


<style>
body{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  background-image: url('https://img.freepik.com/premium-vector/ancient-egypt-egyptian-hieroglyphs-seamless-pattern-antique-elements-symbols-papyrus-historical-traditional-background-pyramids-graphic-decor-textile-wrapping-paper-wallpaper-vector-texture_176411-2756.jpg');
    
}
body *{
  font-family: "myfont";
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body *::-webkit-scrollbar-track
{ 
  box-shadow: none;
	-webkit-box-shadow: inset 0 0 6px rgba(0,0,0,0.3);
	background-color: #F5F5F5;
}

body *::-webkit-scrollbar
{
	width: 6px;
	background-color: #F5F5F5;
}

body *::-webkit-scrollbar-thumb
{
	background-color: #000000;
}





</style>
