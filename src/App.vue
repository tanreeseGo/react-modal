<template>
  <h1>{{ title }}</h1>
  <p>Welcome...</p>

  <teleport to=".modals" v-if="showModal">
    <Modal :header='header' :text='text' theme= 'dark' @close="toggleModal">
      <template v-slot:links>
        <a href="#">sign up now</a>
        <a href="#">more info</a>
      </template>
      <h1>hello ninjas!</h1>
      <p>you've come to the right page!</p>
    </Modal>
  </teleport>

  <teleport to="modals " v-if="showModalTwo">
    <Modal :header='header' :text='text' theme= 'sale' @close="toggleModalTwo">
      <h1>sign up to newsletter!</h1>
      <p>get the latest insights from vital journalism!</p>
    </Modal>
  </teleport >

  <button @click="toggleModal">toggle modal</button>
  <button @click="toggleModalTwo">toggle modal two</button>
  
  <input type="text" ref="namer">
  
  <button @click.alt="handleClick">click me (alt)</button>
</template>

<script>
import Modal from './components/Modal.vue'

export default {
  name: 'App',
  components: { Modal },
  data () {
    return {
      title: 'My First Vue App',
      header: 'Sign up for a giveaway',
      text: 'Grab your ninjas nowwwwww',
      showModal: false,
      showModalTwo: false
    }
  },
  methods: {
    handleClick() {
      console.log(this.$refs.namer)
      this.$refs.namer.classList.add('active')
      this.$refs.namer.focus()
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

<style>
#app, .modal {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  border-bottom: 1px solid black;
  display: inline-block;
  padding: 10px;
}
</style>
