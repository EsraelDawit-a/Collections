<template>
  <div>
      <div class="flex justify-center mb-3 load text-2xl pt-5"></div>

       <div 
         class="w-[33%] cards ld h-[500px] bg-indigo-200 skeleton" >
         <img src alt="">
       </div> 
     </div>
</template>

<script>
export default {
 name:"SkeletonLoader"
}
</script>

<style scoped>
    .ld{
  border-top: 0px !important;
}


.skeleton {
  height: 270px;
  background: linear-gradient(
    90deg,
    hsl(210, 15%, 88%),
    hsl(210, 15%, 95%),
    hsl(210, 15%, 88%)
  );
  background-size: 200%;
  animation: loader 1s infinite reverse;
}
.load {
  height: 40px;
  background: linear-gradient(
    90deg,
    hsl(210, 15%, 88%),
    hsl(210, 15%, 95%),
    hsl(210, 15%, 88%)
  );
  background-size: 200%;
  animation: loader 1s infinite reverse;
}
.skeleton.load {
  width: 50%;
  height: 1em;
  color:rgb(192, 179, 179);
}
small.skeleton {
  height: 1rem;
  width: 4rem;
}
p.skeleton {
  height: 3em;
}

.cards {
 
  border-right: 0px;
  border-bottom: 0px;
  font-family: "Courier New", Courier, monospace;
}

/* skeleton animation */
@keyframes loader {
  from {
    background-position: -100% 0;
  }
  to {
    background-position: 100% 0;
  }
}

</style>