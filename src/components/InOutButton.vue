<template>
  <div id="button" class="btn btn-dark" @click="action">
    <Icon :icon="isInput.Icon" :class="isInput.color" class="mb-1" />
    <span>{{ isInput.text }}</span>
  </div>
</template>

<script>
import { Icon } from "@iconify/vue2";

export default {
  name: "InOutButton",
  components: { Icon },

  props: {
    status: String,
  },


  data() {
    return {
      confOut: {
        text: "Salida",
        Icon: "fluent:arrow-step-out-20-filled",
        color: "text-info",
      },
      confIn: {
        text: "Entrada",
        Icon: "fluent:arrow-step-in-20-filled",
        color: "text-primary",
      },
    };
  },

  methods: {
    action() {
      this.$emit("action", this.status);
    },
  },
  computed: {
    isInput() {
      return this.status == "input" ? this.confIn : this.confOut;
    },
  },

};
</script>

<style scoped></style>
