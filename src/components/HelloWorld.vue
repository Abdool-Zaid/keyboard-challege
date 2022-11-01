<script setup>
import { onMounted } from "vue";
let i
let keys=new Set([]);
let keyboard=[]
function generateRandomColor() {
  let letters = "0123456789ABCDEF";
  let color = "#";
  for (let i = 0; i < 6; i++) {
    color += letters[Math.floor(Math.random() * 16)];
  }
  return color;
}
onMounted(() => {
window.addEventListener("keypress", (event)=> {
keys.add(event.key)
keyboard=[...keys]
board.innerHTML=``
keyboard.forEach((key)=>{
  board.innerHTML+=`
  <p class="key" id="key${key}">${key}</p>
  `
})
  document.querySelectorAll('.key').forEach((key)=>{
    key.style=`
    margin: 1%;
    `
  }) 
  document.querySelector(`#key${event.key}`).classList.add('active')
  console.log(document.querySelector(`#key${event.key}`).classList)
  document.querySelector('.active').style=`
  background-color:${ generateRandomColor()} ;
  
  
  `
})

});
</script>

<template>
  <div id="board"></div>
</template>

<style scoped>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#board{
  display: flex;
  flex-wrap: wrap;
}
.active{
  animation: animatename 1s linear infinite;
}
@keyframes animatename{
  0%{
  opacity: 0;
  }
  50%{
    opacity: 1;
  }
  100%{
  opacity: 0;
  }
}
</style>
