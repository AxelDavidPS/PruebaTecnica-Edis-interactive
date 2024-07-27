<template>
  <div class="home p-4 btn-group" role="group" aria-label="Button group with nested dropdown">
    <InOutButton :status="status_state" @action="onChange" />
    <BtnMonthYear 
      :year="year" 
      :text="text"
      @dis="disminuirYear"
      @aum="aumentarYear"
      @todo="onFullYear"
      @monthYear="onDateMonthChanged"
    />
  </div>
</template>

<script>
import InOutButton from "@/components/InOutButton.vue";
import BtnMonthYear from "@/components/BtnMonthYear.vue";

export default {
  name: "HomeView",
  components: {
    InOutButton,
    BtnMonthYear
  },
  data() {
    return {
      status_state: "input",
      year: 2023,
      text:"Todo 2023",
      month: ""
    };
  },
  methods: {
    onChange(status){
      status == "input" ? this.status_state = "output" : this.status_state = "input" 
      console.log(`Status chenged to: ${this.status_state}`);
    },
    disminuirYear() {
      this.year -= 1
      console.log(`Disminucion del año a: ${this.year}`);
    },
    aumentarYear() {
      this.year += 1
      console.log(`Aumento del año a: ${this.year}`);
    },
    onFullYear(year){
      this.text = `Todo ${year}` 
      console.log(`Selección de todo el año: ${this.year}`);
    },
    onDateMonthChanged(year, month){
      this.text = `${month} ${year}` 
      this.month = `${month}`
      console.log(`Selección del mes y año: ${this.month} ${this.year}`);
    }
  },
};
</script>
