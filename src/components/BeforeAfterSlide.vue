<template>
    <div>
        <div class="wrapper">
            <div class="before">
                <img class="content-image" src="../images/After.jpg" draggable="false"/>   </div>
                <div class="after">
                    <img class="content-image" src="../images/Before.jpg" draggable="false"/>
                </div>
                <div class="scroller w-[55px] h-full max-[1200px]:w-[40px] max-[640px]:w-[33px] absolute cursor-grabbing top-0 bottom-0" >
                    <img src="../images/Handle.svg" alt="" class="h-full w-full">
                </div>
            </div>
        </div>
</template>


<script setup>
import { onMounted} from 'vue';
onMounted(()=>{
let active = false;
document.querySelector('.scroller').addEventListener('mousedown',function(){
  active = true;
  document.querySelector('.scroller').classList.add('scrolling');
});
document.body.addEventListener('mouseup',function(){
  active = false;
  document.querySelector('.scroller').classList.remove('scrolling');
});
document.body.addEventListener('mouseleave',function(){
  active = false;
  document.querySelector('.scroller').classList.remove('scrolling');
});
document.body.addEventListener('mousemove',function(e){
  if (!active) return;
  let x = e.pageX;
  x -= document.querySelector('.wrapper').getBoundingClientRect().left;
  scrollIt(x);
});
function scrollIt(x){
    let transform = Math.max(0,(Math.min(x,document.querySelector('.wrapper').offsetWidth)));
    if (window.innerWidth>1200) {
    document.querySelector('.after').style.width = transform+"px";
        document.querySelector('.scroller').style.left = transform-28+"px";
    }else if(window.innerWidth>640){
    document.querySelector('.after').style.width = transform+"px";
        document.querySelector('.scroller').style.left = transform-22+"px";
    }else{
    document.querySelector('.after').style.width = transform+"px";
        document.querySelector('.scroller').style.left = transform-18+"px";
    }
}

scrollIt(150);
document.querySelector('.scroller').addEventListener('touchstart',function(){
  active = true;
  document.querySelector('.scroller').classList.add('scrolling');
});
document.body.addEventListener('touchend',function(){
  active = false;
  document.querySelector('.scroller').classList.remove('scrolling');
});
document.body.addEventListener('touchcancel',function(){
  active = false;
  document.querySelector('.scroller').classList.remove('scrolling');
});
})
</script>


<style scoped>
.before,.after {
  width:100%;
  height:100%;
  background-repeat:no-repeat;
  position: absolute;
  top:0;
  left:0;
  pointer-events:none;
  overflow: hidden ;
}
.content-image{
  height:100%;
  max-width:1000000%;
}

.scrolling{
  pointer-events:none;
}
</style>