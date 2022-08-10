<template>
  <q-page class="flex flex-center">
    <div class="figure" @click="translateBlock"/>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue';
import anime from 'animejs/lib/anime.es';

export default defineComponent({
  name: 'MainIndex',
  data() {
    return {
      status: false,
    }
  },

  methods: {
    translateBlock() {
      this.status = !this.status;

      anime({
        targets: '.figure',
        translateX: 200 * this.status,
        scaleX: [
          { value: 2, duration: 100, delay: 0, easing: 'easeOutExpo' },
          { value: 1, duration: 900 },
        ],
        rotate: function() { return anime.random(0, 50)/50 + 'turn'},
        easing: 'easeOutElastic(1, .8)',
        duration: 2000,
      })

      // anime({
      //   targets: '.block',
      //   translateX: function() { return anime.random(-100, 100) },
      //   translateY: function() { return anime.random(-100, 100) },
      //   scale: function() { return anime.random(1000, 2000)/1000 },
      //   backgroundColor: this.colorGenerate(),
      //   opacity: [
      //     {value: 1, duration: 0},
      //     {value: 0, delay: 100, easing:'easeOutExpo'},
      //   ],
      //   borderRadius: [
      //     function() { return anime.random(0, 50) + '%'} ,
      //     function() { return anime.random(0, 50) + '%'}
      //   ],
      //   rotate: function() { return anime.random(0, 10)/10 + 'turn'},
      //   duration: 3000,
      //   easing: 'easeOutElastic(0.2, 0.2)',
      // });
    },

    colorGenerate() {
      return  "#" + ((1 << 24) +
        (anime.random(70, 255) << 16) +
        (anime.random(70, 255) << 8) +
         anime.random(70, 255)).toString(16).slice(1)
    },
  },

  created() {
    document.querySelector(':root').style.setProperty(
      '--start-color', this.colorGenerate()
    )
  }
})
</script>
