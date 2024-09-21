<template>
  <q-page padding>
    <input
      v-model="message.title"
      v-auto-focus
      @keyup.esc="clearMessage"
      @keyup.enter="handleKeyUp"
      :class="{ InputClass: message.title.length > 20 }"
    />
    <br />
    <p v-if="message.title"></p>
    <h5 v-else>Please enter a message</h5>
    <button @click="clearMessage">Clear</button>
    <hr />
    <div v-if="message.title">
      <h6>Message UpperCase</h6>
      <p>{{ messageUpperCase }}</p>
    </div>
    <div v-if="message.title">
      <h6>Message UpperCase</h6>
      <p>{{ messageLowerCase }}</p>
    </div>
    <div class="imageIcon">
      <!-- <img
        src="https://pixsector.com/cache/517d8be6/av5c8336583e291842624.png"
        alt="imageicon"
        v-icon-style="imageStyle"
      /> -->
      <q-btn @click="backBtnClick" class="btnStyle"> GoBack </q-btn>
    </div>
  </q-page>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "IndexPage",
  data() {
    return {
      message: { title: "", desc: "" },
      clickBtn: false,
      //Style of the image
      imageStyle: {
        width: "100px",
        height: "100px",
        border: "2px solid black",
        borderRadius: "25px",
      },
    };
  },
  computed: {
    //To Avoid calling the function where any change happen in the component
    messageUpperCase() {
      return this.message.title.toUpperCase();
    },
    messageLowerCase() {
      return this.message.title.toLowerCase();
    },
  },

  methods: {
    clearMessage() {
      this.message.title = "";
    },
    handleKeyUp(e) {
      if (e.keyCode == 13) {
        this.alertMessage();
      }
    },
    alertMessage() {
      alert(this.message.title);
    },
    backBtnClick() {
      this.alertMessage();
    },
  },
  //Custom directives
  directives: {
    autoFocus: {
      mounted(el) {
        el.focus();
      },
    },
    iconStyle: {
      mounted(el, binding) {
        // Apply the styles from the binding
        Object.assign(el.style, binding.value);
      },
    },
  },
  beforeUnmount() {
    console.log("before destroy");
  },
  unmounted() {
    console.log("destroyed");
  },
});
</script>

<style>
.borderMessage {
  border: 1px solid black;
  display: flex;
  margin-top: 20px;
  padding: 5px;
}
.imageIcon {
  display: flex;
  gap: 10px;
  align-items: center;
}
.imageIcon button {
  width: 200px;
  height: 10px;
}
.InputClass {
  color: red;
}
.btnStyle {
  border-radius: 40px;
}
</style>
