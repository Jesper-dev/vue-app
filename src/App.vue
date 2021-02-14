// Detta är en html template, man kan säga att det är html för att göra det lätt
// Varje component måste ha en template tag
<template>
  <!-- <div id="wrapper"> -->
    <h1>{{title}}</h1>

    <input type="text" ref="name"/>
    <button @click="handleClick">Click Me</button>
    <teleport to=".modals" v-if="showModal">
      <!-- Inne i Modal så är det något som kallas ett slot, vi fixar template som props ungefär -->
      <Modal  @close='toggleModal'>
        <h1 class="modalTitle">This is a slot</h1>
        <p class="modalText">Yippie</p>
        <template v-slot:links>
          <a href="#">Sign Up!</a>
          <a href="#">More Info</a>
        </template>
      </Modal>
    </teleport>

    <teleport to=".modals" v-if="showModalTwo">
      <!-- Inne i Modal så är det något som kallas ett slot, vi fixar template som props ungefär -->
      <Modal  @close='toggleModalTwo'>
        <h1 class="modalTitle">This is the second Modal</h1>
        <p class="modalText">Whohooo</p>
        
      </Modal>
    </teleport>
    <p>Welcome...</p>
    <button @click="toggleModal">Show Modal</button>
    <button @click="toggleModalTwo">Show Modal Two</button>
<!-- </div> -->
</template>

<script>
import Modal from './components/Modal'

//Det här är 'root object/component', den har data, methods osv.
export default {
  name: 'App',
  components: {
    Modal
  },
  data() {
    return {
      title: 'My First Vue App',
      showModal: false,
      showModalTwo: false,
    }
  },
  //Methods sköter metoder/functioner i våra components
  methods: {
    handleClick() {
      //För att komma åt input
      console.log(this.$refs.name)
      this.$refs.name.classList.add('active')
      this.$refs.name.focus()
    },
    toggleModal() {
      this.showModal = !this.showModal
    },
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo
    }
  } 
}
</script>

/* Här är style, precis som css */
<style>
#app, .modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  box-sizing: border-box;
}

#app > h1{
  border-bottom: 2px solid #ddd;
  padding-bottom: 10px;
}

#desc{
  font-size: 1.5rem;
}

.modalTitle {
  color: white;
}

.modalText {
  color: white;
}
</style>
