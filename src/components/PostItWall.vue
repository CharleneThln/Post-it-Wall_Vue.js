<template>
  <div class="container">
    <div class="row">
      <div class="col-4">
        <ul>
          <li v-for="(note, index) in notes" v-bind:key="note.id">
            <div class="post-it">
              <h2 id="title">{{ note.title }}</h2>
              <p id="content">{{ note.content }}</p>
              <button id="delete" v-on:click="removeNote(index)">x</button>
              <router-link :to="'/postit/' + note.id">
                <button>
                  →
                </button></router-link
              >
            </div>
          </li>
        </ul>
      </div>
      <div class="col-4" style="margin-top:100px;">
        <div class="post-it" style="background:lightblue">
          <h2>Post-it #blue</h2>
          <p>
            Ce post-it est bleu !<br />
            But I must explain to you how all this mistaken idea of denouncing
            pleasure and praising pain was born and I will give you a complete
            account of the system, and expound the actual teachings of the great
            explorer of the truth, the master-builder of human happiness.
          </p>
          <button id="delete">x</button>
          <router-link to="/bluepostit"
            ><button>
              →
            </button></router-link
          >
        </div>
      </div>
      <div class="col-4">
        <div v-if="onmouseover"></div>
        <span @mouseover="hover = true" @mouseleave="hover = false">
          <div class="post-it" id="add">
            <form v-on:submit.prevent="addNewNote">
              <h2><label for="new-note">Add new post-it</label></h2>

              <span v-if="hover">
                <pre><input v-model="newNoteTitle" placeholder="titre" /></pre>
                <pre><input v-model="newNoteContent" placeholder="contenu" /></pre>
                <button>Add</button>
              </span>
            </form>
          </div>
        </span>
        <div class="post-it" style="background:pink;margin-top:50px;">
          <h2>Post-it #pink</h2>
          <p>
            Renvoie vers la page "test"
          </p>
          <button id="delete">x</button>
          <button><a href="/test">→ /test</a></button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import PostItDetail from "@/components/PostItDetail.vue";
import BluePostIt from "@/components/BluePostIt.vue";
export default {
  component: {
    PostItDetail,
    BluePostIt
  },
  data() {
    return {
      hover: false,
      newNoteTitle: "",
      newNoteContent: "",
      notes: [
        {
          id: 0,
          title: "Titre du Post-It 1",
          content:
            "Contenu du premier post-it : Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."
        }
      ]
    };
  },
  beforeMount() {
    if (localStorage.getItem("notes")) {
      this.notes = JSON.parse(localStorage.getItem("notes"));
    }
  },
  methods: {
    addNewNote: function() {
      this.notes.push({
        id: this.notes.length,
        title: this.newNoteTitle,
        content: this.newNoteContent
      });
      this.newNoteText = "";
      this.newNoteContent = "";
      this.saveNotes();
    },
    saveNotes: function() {
      localStorage.setItem("notes", JSON.stringify(this.notes));
    },
    removeNote(id) {
      console.log(id);
      this.notes.splice(id, 1);

      this.saveNotes();
    }
  }
};
</script>

<style scoped>
.post-it {
  position: relative;
  box-shadow: -5px 10px 6px 2px rgba(0, 0, 0, 0.39);
  -webkit-box-shadow: 0px 10px 6px 2px rgba(0, 0, 0, 0.39);
  -moz-box-shadow: -5px 10px 6px 2px rgba(0, 0, 0, 0.39);
  background-color: rgba(0, 0, 0, 0.25);
  border-bottom-left-radius: 300px 20px;
  background: khaki;
  border-bottom: solid;
  border-width: 1px;
  width: 230px;
  height: 200px;
  justify-content: center;
  align-items: center;
  font-family: "Arial", cursive;
  margin-top: 10%;
  padding-top: 8%;
}

h2 {
  font-size: 25px;
  padding-top: 2px;
  padding-left: 15px;
  text-align: left;
}

p {
  font-size: 15px;
  width: 200px;
  padding-top: 10px;
  padding-left: 15px;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

li {
  display: block;
}

#add {
  opacity: 60%;
  background: lightgrey;
  height: 100px;
}

#add:hover {
  opacity: 100%;
  height: 230px;
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
  border-color: black;
}
</style>
