<template>
  <div class="container">
    <div class="row">
      <div class="col">
        <h1>Détail du post-it #blue</h1>
        <div>
          <p>
            <button><router-link to="/">←</router-link></button>
            Back to my postits
          </p>
        </div>
        <div class="post-it">
          <h2>Post-it #blue</h2>
          <p>Ceci est un post-it bleu !</p>
          <p>
            But I must explain to you how all this mistaken idea of denouncing
            pleasure and praising pain was born and I will give you a complete
            account of the system, and expound the actual teachings of the great
            explorer of the truth, the master-builder of human happiness.
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "PostItDetail",
  props: {
    id: { type: Number }
  },
  data() {
    return {
      notes: [
        {
          id: 0,
          title: "Titre du Post-It 1",
          content: "Contenu du premier post-it"
        },
        {
          id: 1,
          title: "Titre du Post-It 2",
          content: "Contenu du deuxième post-it"
        },
        {
          id: 2,
          title: "Titre du Post-It 3",
          content: "Contenu du troisième post-it"
        }
      ]
    };
  },
  mounted() {
    console.log("mounted");
    if (localStorage.getItem("notes")) {
      this.notes = JSON.parse(localStorage.getItem("notes"));
    }
  }
};
</script>

<style scoped>
.post-it {
  align-content: center;
  box-shadow: -5px 10px 6px 2px rgba(0, 0, 0, 0.39);
  -webkit-box-shadow: 0px 10px 6px 2px rgba(0, 0, 0, 0.39);
  -moz-box-shadow: -5px 10px 6px 2px rgba(0, 0, 0, 0.39);
  background-color: rgba(0, 0, 0, 0.25);
  border-bottom-left-radius: 300px 20px;
  background: lightblue;
  width: 600px;
  height: 300px;
  justify-content: center;
  align-items: center;
  font-family: "Arial", cursive;
  padding: 3%;
  margin: 0 auto;
  width: 60%;
}

h2 {
  font-size: 25px;
  padding-bottom: 15px;
  padding-left: 15px;
  text-align: left;
}
p {
  font-size: 15px;
}
</style>
