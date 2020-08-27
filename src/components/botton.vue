<template>
  <div>
    <div class="row">
      <div class="col-sm">
        <p style="font-size: 150%">{{aplayer.name}}</p>
        <p>
          <img v-bind:style="{width: aplayer.hp + 'px'}" :src="hp1" alt height="20px" />
        </p>
        <p style="font-size: 150%">{{thp}}{{aplayer.hp}}</p>
        <p>
          <img style="width:70%" :src="aplayer.image" />
        </p>
      </div>
      <div class="col-md-sm">
        <div class="row">
          <div class="col-md">
            <button class="btn btn-primary" @click="start()">Start</button>
          </div>
          <div class="col-md">
            <button v-bind:disabled="end" class="btn btn-danger" @click="attack()">Normal Attack</button>
          </div>
          <div class="col-md-4">
            <button v-bind:disabled="end" class="btn btn-dark" @click="special()">Ultimate Attack</button>
          </div>
          <div class="col-md">
            <button class="btn btn-light" @click="reset()">NewGame</button>
          </div>
          <br />
          <br />
          <br />
          <br />
          <br />
          <br />

          <img
            class="rounded mx-auto d-block"
            src="http://static1.comicvine.com/uploads/original/13/135592/5270582-4644160274-vs.pn.png"
            width="30%"
          />
        </div>
        <div class="row">
          <div class="col-sm"></div>
          <div class="col-sm">
            <div id="score">
              <div v-if="amonster.hp <= 0">You Win</div>
              <div v-else-if="aplayer.hp <= 0">You Lose</div>
            </div>
          </div>
          <div class="col-sm"></div>
        </div>
      </div>
      <div class="col-sm">
        <p style="font-size: 150%">{{amonster.name}}</p>
        <p>
          <img v-bind:style="{width: amonster.hp + 'px'}" :src="hp2" alt height="15px" />
        </p>
        <p style="font-size: 150%">{{thp}}{{amonster.hp}}</p>
        <p>
          <img style="width:70%" :src="amonster.image" />
        </p>
      </div>
    </div>
    <hr />
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      thp: "HP:",
      end: false,
      hp2:
        "https://i.ppy.sh/bca61e3c2183a86ddb4c1d75914fab845e2b128f/687474703a2f2f692e696d6775722e636f6d2f6953766c5662432e706e67",
      hp1:
        "https://i.ppy.sh/bca61e3c2183a86ddb4c1d75914fab845e2b128f/687474703a2f2f692e696d6775722e636f6d2f6953766c5662432e706e67",
      aplayer: { name: "", hp: 1, image: "", hp1: "" },
      player: [
        {
          name: "Senju Hashirama",
          hp: 200,
          image: require("../assets/1.png"),
        },
        {
          name: "Namikaze Minato",
          hp: 150,
          image: require("../assets/2.png"),
        },
        {
          name: "Uzumaki Naruto",
          hp: 170,
          image: require("../assets/3.png"),
        },
        {
          name: "Uchiha Sasuke",
          hp: 170,
          image: require("../assets/4.png"),
        },
      ],
      amonster: { name: "", hp: 1, image: "", hp1: "" },
      monster: [
        {
          name: "Uchiha Madara",
          hp: 195,
          image: require("../assets/5.png"),
        },
        {
          name: "Uchiha Obito",
          hp: 180,
          image: require("../assets/6.png"),
        },
        {
          name: "Kisame",
          hp: 140,
          image: require("../assets/7.png"),
        },
        {
          name: "Setzu",
          hp: 135,
          image: require("../assets/8.png"),
        },
      ],
      pmax: "50%",
      mmax: "50% ",
    };
  },
  methods: {
    randomno: function (min, max) {
      return Math.max(Math.floor(Math.random() * max) + 1, min);
    },
    start: function () {
      this.aplayer = this.player[this.randomno(1, 4) - 1];
      this.amonster = this.monster[this.randomno(1, 4) - 1];
    },
    attack: function () {
      this.pmax = Math.floor(Math.random() * 10 + 4);
      this.amonster.hp = this.amonster.hp - this.pmax;
      this.mmax = Math.floor(Math.random() * 10 + 4);
      this.aplayer.hp = this.aplayer.hp - this.mmax;
      if (this.aplayer.hp <= 0) {
        this.aplayer.hp = 0;
        this.end = true;
      } else if (this.amonster.hp <= 0) {
        this.amonster.hp = 0;
        this.end = true;
      }
    },
    special: function () {
      this.pmax = Math.floor(Math.random() * 15 + 6);
      this.amonster.hp = this.amonster.hp - this.pmax;
      this.mmax = Math.floor(Math.random() * 15 + 6);
      this.aplayer.hp = this.aplayer.hp - this.mmax;
      if (this.aplayer.hp <= 0) {
        this.aplayer.hp = 0;
        this.end = true;
      } else if (this.amonster.hp <= 0) {
        this.amonster.hp = 0;
        this.end = true;
      }
    },
    reset: function () {
      window.location.reload();
    },
  },
};
</script>
<style>
#score {
  font-size: 300%;
  color: aliceblue;
}
</style>