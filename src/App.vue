<template>
  <router-view/>
</template>

<style lang="scss">

@import url('https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&display=swap');
// form inputs 24px font size

$strongCyan: hsl(172, 67%, 45%);
$darkCyan: hsl(183, 100%, 15%);
$greyishCyan: hsl(186, 14%, 43%);
$greyishCyan1: hsl(184, 14%, 56%);
$lightCyan: hsl(185, 41%, 84%);
$lightCyanNon: hsl(189, 41%, 97%);
$white: hsl(0, 0%, 100%);

#app {
  font-family: 'Space Mono', monospace;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

body {
  background-color: $lightCyan;
  overflow: hidden;
}

</style>
