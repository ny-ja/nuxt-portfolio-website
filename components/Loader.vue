<style scoped>
.loader {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  width: 100vw;
  position: fixed;
  top: 0;
  left: 0;
}

.l,
.o,
.a,
.d,
.i,
.n,
.g,
.d1,
.d2 {
  color: black;
  opacity: 0;
  animation: pass 2s ease-in-out infinite;
  letter-spacing: 0.5em;
  text-shadow: 2px 2px 3px #919191;
}

.l {
  animation-delay: 0.2s;
}

.o {
  animation-delay: 0.4s;
}

.a {
  animation-delay: 0.6s;
}

.d {
  animation-delay: 0.8s;
}

.i {
  animation-delay: 1s;
}

.n {
  animation-delay: 1.2s;
}

.g {
  animation-delay: 1.4s;
}

.d1 {
  animation: pass1 2s ease-in-out infinite;
  animation-delay: 1.6s;
}

.d2 {
  animation: pass1 2s ease-in-out infinite;
  animation-delay: 2s;
}

@keyframes pass {

  0%,
  100% {
    opacity: 1;
  }

  50% {
    opacity: 0;
  }
}

@keyframes pass1 {

  0%,
  100% {
    opacity: 1;
  }

  50% {
    opacity: 0;
  }
}
</style>


<template>
  <div class="loader">
    <span class="l">L</span>
    <span class="o">o</span>
    <span class="a">a</span>
    <span class="d">d</span>
    <span class="i">i</span>
    <span class="n">n</span>
    <span class="g">g</span>
    <span class="d1">.</span>
    <span class="d2">.</span>
  </div>
</template>
