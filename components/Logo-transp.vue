<template>
<Nuxt-link to="/">
    <img
    class="LaEsquinaLogo"
    alt="LA ESQUINA RADIO"
    src="/logo-trasp.svg"
  >
</Nuxt-link>
</template>

<style>
.LaEsquinaLogo {
  height: 150px;
  width: 150px;
  transform: rotateY(560deg);
  animation: turn 3.5s ease-out forwards 1s;
}

@keyframes turn {
  100% {
    transform: rotateY(0deg);
  }
}
</style>
