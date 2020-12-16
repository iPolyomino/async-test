<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <button v-on:click="send">update</button>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  methods: {
    send: async function () {
      this.$emit("update:msg", "start");

      // task
      await new Promise((resolve) => {
        setTimeout(() => {
          console.log("done");
          resolve();
        }, 3000);
      });

      this.$emit("update:msg", "done");
    },
  },
};
</script>
