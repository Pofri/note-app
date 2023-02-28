<template>
  <div class="overlay" v-if="display">
    <div class="modal">
      <textarea v-model="note" name="note" id="note" cols="30" rows="10"></textarea>
      <button @click="addNote">Add Note</button>
      <button @click="show">Close</button>
    </div>
  </div>
  <section class="note-taking-page">
    <div class="main-page">
      <div class="profile">
        <div><h1>Welcome</h1></div>
        <h2>Pofri</h2>
      </div>
      <div class="list-div">
        <div class="icon"><img src="../img/book.png" alt=""></div>
        <h2>Empty list!</h2>
        <p>Click the button to write something exciting!</p>
      </div>
      <div>
        <button class="plus" @click="show()">+</button>
      </div>
    </div>
    <div class="note-page" v-if="notes.length">
      <div class="content" v-for="note in notes">
        <div><p>{{note.note}}</p>
        </div>

        <div class="date">
          {{ note.date }}
        </div>

        
      </div>
      <div>
        <button class="plus" @click="show">+</button>
      </div>

      <!-- <div class="content">
        <div><p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Laborum aspernatur impedit eveniet velit ullam voluptatem quibusdam nostrum id tempore ab.</p>
        </div>

        <div class="date">
          12/12/12
        </div>
      </div>

      <div class="content">
        <div><p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Laborum aspernatur impedit eveniet velit ullam voluptatem quibusdam nostrum id tempore ab.</p>
        </div>

        <div class="date">
          12/12/12
        </div>
      </div>

      <div class="content">
        <div><p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Laborum aspernatur impedit eveniet velit ullam voluptatem quibusdam nostrum id tempore ab.</p>
        </div>

        <div class="date">
          12/12/12
        </div>
      </div>

      <div class="content">
        <div><p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Laborum aspernatur impedit eveniet velit ullam voluptatem quibusdam nostrum id tempore ab.</p>
        </div>

        <div class="date">
          12/12/12
        </div>
      </div> -->

      
    </div>
  </section>
</template>


<script setup>
import {ref} from 'vue'
const display = ref(false);

const note = ref('');
const notes = ref([]);
// let isNoteEmpty = ref(true)

function show(){
  display.value = !display.value
}

function addNote(){
  const newNote = {
    note: note.value,
    date: new Date(),
    id: Math.random()
  }
  notes.value.push(newNote);
  console.log(note.value);
  show();
  note.value = "";
}



</script>
<style>
*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
.note-taking-page{
  /* border: 2px solid black; */
  height: 100vh;
}
.main-page{
  /* border: 1px solid black; */
  height: 40em;
  width: 50em;
  color: white;
  padding: 20px;
  border-radius: 30px;
  font-weight: bolder;
  text-align: center;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: rgb(41, 41, 77);
}
.profile{
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  font-weight: bolder;
  margin-bottom: 70px;

}
.icon{
  margin-bottom: 30px;
}
.plus{
  position: absolute;
  top: 90px;
  right: 40px;
  padding: 20px;
  border-radius: 50%;
  border: none;
  font-size: 20px;
}

.overlay {

    position: fixed;
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.5);
    z-index: 5;
    display: flex;
    justify-content: center;
    align-items: center;

  }
.modal{
  display: flex;
  flex-direction: column;
  width: 40rem;
  gap: 5px;
  padding: 10px;
  box-shadow: 0 0 5px 5px rgba(92, 87, 87, 0.5);
}

.modal textarea{
  border: none;
  border-radius: 20px;
  padding: 20px;
  font-size: 15px;
}
.modal button{
  padding: 10px;
  border-radius: 30px;
  border: none;
}
.note-page{
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  row-gap: 20px;
  height: 40em;
  width: 70em;
  color: white;
  padding: 20px;
  border-radius: 30px;
  font-weight: bolder;
  text-align: center;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: rgb(41, 41, 77);
}

.content{
  border: 1px solid white;
  width: 20rem;
  height: 15rem;
  border-radius: 20px;
}
.date{
  margin-top: 100px;
}

</style>
