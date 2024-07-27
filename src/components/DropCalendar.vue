<template>
  <div
    id="DropCalendar"
    class="dropdown-menu dropdown-menu-dark px-3 pb-1"
    data-bs-theme="dark"
  >
    <div
      class="d-flex flex-row row-cols-3 justify-content-between align-items-center"
    >
      <button class="w-auto dropdown-item" @click="disminuir">
        <Icon :icon="arrowLeft" />
      </button>
      <span class="text-center">{{ year }}</span>
      <button class="w-auto dropdown-item" @click="aumentar">
        <Icon :icon="arrowRight" />
      </button>
    </div>

    <div class="row row-cols-3">
      <button class="btn" @click="monthYear">Ene</button>
      <button class="btn" @click="monthYear">Feb</button>
      <button class="btn" @click="monthYear">Mar</button>
      <button class="btn" @click="monthYear">Abr</button>
      <button class="btn" @click="monthYear">May</button>
      <button class="btn" @click="monthYear">Jun</button>
      <button class="btn" @click="monthYear">Jul</button>
      <button class="btn" @click="monthYear">Ago</button>
      <button class="btn" @click="monthYear">Sep</button>
      <button class="btn" @click="monthYear">Oct</button>
      <button class="btn" @click="monthYear">Nov</button>
      <button class="btn" @click="monthYear">Dic</button>
    </div>

    <div class="row">
      <button class="mt-1 text-center btn btn-secondary" @click="todoYear">
        Todo {{ year }}
      </button>
    </div>
  </div>
</template>

<script>
import { Icon } from "@iconify/vue2";

export default {
  name: "DropCalendar",
  components: {
    Icon,
  },
  props:{
    year: Number
  },
  data() {
    return {
      arrowLeft: "ic:outline-arrow-left",
      arrowRight: "ic:outline-arrow-right",
    };
  },
  methods:{
    aumentar(e){
      e.stopPropagation();
      this.$emit("aum")
    },

    disminuir(e){
      e.stopPropagation();
      this.$emit("dis")
    },

    todoYear(){
      this.$emit("todo",this.year)
    },

    monthYear(e){
      const month = e.target.textContent 
      this.$emit("monYe",this.year, month)
    }

  }
};
</script>

<style scoped></style>
