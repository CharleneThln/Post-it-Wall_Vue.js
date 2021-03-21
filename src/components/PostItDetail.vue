<template>
  <div class="container">
    <div class="row">
      <div class="col">
        <h1>Détail du post-it #{{ id }}</h1>
        <div>
          <p>
            <button><router-link to="/">←</router-link></button>
            Back to my postits
          </p>
        </div>
        <div class="post-it">
          <h2>{{ notes[id].title }}</h2>
          <p>{{ notes[id].content }}</p>
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
      notes: [{
          id: 0,
          title: "Titre du Post-It 1",
          content:
            "Contenu du premier post-it : Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."
        }]
    };
  },
  beforeMount() {
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
  background: khaki;
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

button {
  font-size: 12px;
  padding-left: 15px;
  padding-right: 15px;
  margin: 5px;
  background: lightgrey;
  border: solid;
  border-width: 1px;
  border-radius: 10%;
}
button a {
  color: black;
  text-decoration: none;
}

a:hover {
  color: black;
  text-decoration: none;
}

button:hover {
  background: white;
}

#delete:hover {
  color: white;
  background: grey;
}
</style>
