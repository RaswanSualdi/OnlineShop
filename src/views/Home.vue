<template>
  <div class="home">
    <HeaderShayna/>
    <HeroShayna/>
    <WomenShayna/>
    <InstaShayna/>
    <LogoPartShayna/>
    <FooterShayna/>
 
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import HeaderShayna from '@/components/HeaderShayna.vue';
import HeroShayna from '@/components/HeroShayna.vue';
import WomenShayna from '@/components/WomenShayna.vue';
import InstaShayna from '@/components/InstaShayna.vue';
import LogoPartShayna from '@/components/LogoPartShayna.vue';
import FooterShayna from '@/components/FooterShayna.vue';


export default {
  name: 'Home',
  components: {
    HeaderShayna,
    HeroShayna,
    WomenShayna,
    InstaShayna,
    LogoPartShayna,
    FooterShayna,
   
  }
}
</script>
