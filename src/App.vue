<template>
  <h1>{{ title }}</h1>
  <input type="text" ref="name" />
  <button @click="handleClick">click me</button>

  <p>welcome....</p>
  <teleport to="#modals" v-if="showModal">
    <Modal :header="header" :text="text" theme="sale" @close="toggleModal">
      <template v-slot:links>
        <a href="#">Sign in</a>
        <a href="#">See more</a>
      </template>
      <h1>Ninja giveaway!</h1>
      <p>Grab your ninja swag for half price!</p>
    </Modal>
  </teleport>

  <teleport to="#modals" v-if="showModalTwo">
    <Modal :header="header" :text="text" theme="sale" @close="toggleModalTwo">
      <h1>Sign up to the newsletter</h1>
      <p>For updates and promo codes!</p>
    </Modal>
  </teleport>
  <!-- <button @click.left="toggleModal">open modal</button> -->
  <!-- <button @click.right="toggleModal">open modal</button> -->
  <!-- <button @click.shift="toggleModal">open modal</button> -->
  <!-- <button @click.alt="toggleModal">open modal</button> -->
  <button @click.alt="toggleModal">open modal (alt)</button>
  <button @click="toggleModalTwo">open modal</button>
</template>

<script>
import Modal from "./components/Modal.vue";
export default {
  name: "App",
  components: { Modal },
  data() {
    return {
      title: "My First Vue App :)",
      header: "Sign up for the giveaway!!",
      text: "Grab your ninja swag for half price!",
      showModal: false,
      showModalTwo: false,
    };
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name);
      this.$refs.name.classList.add("active");
      this.$refs.name.focus();
    },
    toggleModal() {
      this.showModal = !this.showModal;
    },
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo;
    },
  },
};
</script>

<style>
#app,
#modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
