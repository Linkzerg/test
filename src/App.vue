<template lang="html">
  <div class="container screen">
    <section id="cloud" class="nes-container with-title is-dark balloon">
      <div >
        <!-- <p class="targets">
          <span v-for="item in words"> {{ item }}</span>
        </p> -->
        <!-- <div class="targets">
          <div class="target" v-for="item in words">
            {{ item }}
          </div>
        </div> -->
        <wordcloud :data="defaultWords"
                    :showTooltip="sTtip"
                    nameKey="name"
                    font="Press Start 2P"
                    valueKey="value"
                    :wordPadding="wPadding"
                    :font-size="fSize"
                    :color="myColors">
                    </wordcloud>
      </div>
    </section>
    <section class="nes-container with-title is-dark balloon">
      <h2 class="title">Log</h2>
      <div class="messages">
        <div class="message -right">
          <div class="nes-balloon from-right">
            <p>Good morning. Thou hast had a good night's sleep, I hope.</p>
          </div>
          <i class="nes-bcrikko"></i>
        </div>
      </div>
    </section>
    <section class="nes-container with-title is-dark">
      <h2 class="title">Bottom left</h2>
      <div class="nes-field">
        <label for="name_field">Your name</label>
        <form  v-on:submit.prevent="fireType">
          <input type="text" id="fireInput" class="nes-input">
        </form>
      </div>
    </section>
    <section class="nes-container with-title is-dark">
      <h2 class="title">Progress</h2>
      <label> Level 1</label>
      <progress class="nes-progress is-warning" value="90" max="100"></progress>
    </section>
  </div>
</template>
<script>
/* Kelimelerin ağırlıkları toplamı 256'yı bulunca
kullanıcı bir hakkını kaybeder ve aynı seviyeden 0 kelime ile
tekrar başlar. Eğer hakkı kalmamışsa oyunu kaybeder.   */
import wordcloud from 'vue-wordcloud'

export default {
  data: function() {
    return {
      wPadding: 16,
      sTtip: false,
      fSize: [16,96],
      words: [

      ],
      myColors: ['#108DE0', '#76C442', '#F2C409', '#CE372B'],
     defaultWords: [{
         "name": "Cat",
         "value": 26
       },
       {
         "name": "fish",
         "value": 19
       },
       {
         "name": "things",
         "value": 18
       },
       {
         "name": "look",
         "value": 16
       },
       {
         "name": "two",
         "value": 15
       },
       {
         "name": "fun",
         "value": 9
       },
       {
         "name": "know",
         "value": 9
       },
       {
         "name": "good",
         "value": 9
       },
       {
         "name": "play",
         "value": 6
       }
     ]

    }
  },
  methods: {
    fireType: function (e) {
      // console.log('fireType');
      var shot = document.querySelector('#fireInput');
      var fire = shot.value;
      console.log(fire);
      // console.log(this.defaultWords);
      this.defaultWords = this.defaultWords.filter(function (element) {
        if (element.name == fire) {
          console.log('hit');
        }
        return element.name != fire;
      });
      shot.value = "";
    },
  },
  components: {
    wordcloud
  },
  created: function () {

  }
}
</script>

<style lang="css">
</style>
