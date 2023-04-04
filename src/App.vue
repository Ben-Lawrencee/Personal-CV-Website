<template>
  <main>
    <Banner/>
    <About/>
    <Experience/>
    <Education/>
  </main>
  <Sidebar/>
</template>

<script>
import Sidebar from '@/components/Sidebar.vue'
import Banner from '@/sections/Banner.vue'
import About from '@/sections/About.vue'
import Education from './sections/Education.vue';
import Experience from './sections/Experience.vue';

export default {
  name: 'App',
  components: { Sidebar, Banner, About, Experience, Education }
}
</script>

<style lang="scss">
@import '@/GlobalVariables.scss';
@import '@/GlobalAttributes.scss';

* {
  box-sizing: border-box;
  letter-spacing: .04em;
}

html {
  font-size: max(1vmax, 12pt);
}

html, body {
  display: inline-block;
  
  margin: 0;
  padding: 0;
  width: 100vw;
  width: 100dvw;
}

body {
  font-family: Roboto, Arial;
  -webkit-font-smoothing: antialiased;

  background: linear-gradient(to bottom, $dark, #1d002c);
  background-position-x: -200%;
  color: $text;

}

main {
  width: 50vw;
  width: 50dvw;
  min-width: 400px;
  $side-margin: 20vw;
  margin-inline: $side-margin;

  padding-top: 20px;
}

section {
  min-height: 600px;
  margin-block: 16vh;
  margin-block: 16dvh;
}

::-webkit-scrollbar {
  display: none;
}

@media (max-width: 1000px) {
  main {
    margin-left: 8%;
  }
}

</style>
