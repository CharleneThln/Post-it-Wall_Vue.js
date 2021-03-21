<template>
  <div>
    <button><a href="/">BACK HOME</a></button>
    <h1>Titre A</h1>
    <p>texte aaaaa</p>
    <h1 v-if="is_visible">{{ message }}</h1>
    <h2>Seulement le premier mot : {{ onlyFirstWord }}</h2>
    <input type="texte" v-model="fullText">
    <h3>le premier mot de l'intput est : {{ hello }}</h3>
    <span @click="execute">Compteur : {{ count }}</span>
    <p>Image affichée avec hauteur en v-bind :</p><img src="../assets/logo.png" v-bind:height="height" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: "hello world",
      is_visible: true,
      count: 2,
      height: 200,
      hello: "Hello",
      word: "Word"
    };
  },
  computed: {
    onlyFirstWord() {
      return this.message.split(" ")[0].toUpperCase();
    },
    fullText: {
      //GETTER
      get: function() {
        return this.hello + " " + this.word;
      },

      //SETTER
      set: function(newValue) {
        const newHelloWord = newValue.split(" ");
        this.hello = newHelloWord[0];
        this.word = newHelloWord[newValue.length - 1];
      }
    }
  },
  methods: {
    execute() {
      this.count++;
    }
  }
};
</script>

<style scoped></style>
