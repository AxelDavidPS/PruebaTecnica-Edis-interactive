<template>
  <div id="BtnMonthYear" class="btn-group dropdown" role="group">
    <button
      class="btn btn-dark dropdown-toggle"
      type="button"
      data-bs-toggle="dropdown"
      aria-expanded="false"
    >
      {{ text }}
    </button>
    <DropCalendar
      :year="year"
      @aum="aumentarFather"
      @dis="disminuirFather"
      @todo="todoYearFather"
      @monYe="monthYearFather"
    ></DropCalendar>
  </div>
</template>

<script>
import DropCalendar from "@/components/DropCalendar.vue";

export default {
  name: "BtnMonthYear",
  components: {
    DropCalendar,
  },
  data() {
    return {
    };
  },
  props:{
    year: Number,
    text: String
  },

  methods: {
    aumentarFather(){
      this.$emit("aum")
    },

    disminuirFather(){
      this.$emit("dis")
    },

    todoYearFather(year){
      this.$emit("todo",year)
    },

    monthYearFather(year,month){
      this.$emit("monthYear",year, month)
    }
  },
};
</script>

<style scoped></style>
