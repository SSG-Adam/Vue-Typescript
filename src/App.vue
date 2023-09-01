<template>
  <div class="app">
    <header>
      <div class="title"><h1>Jobs Listing</h1></div>
      <div class="order">
        <button @click="handleClick('title')">Order by Title</button>
        <button @click="handleClick('salary')">Order by Salary</button>
        <button @click="handleClick('location')">Order by Location</button>
      </div>
    </header>
    <JobsList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import JobsList from "./components/JobsList.vue";
import Job from "./types/Job";
import OrderTerm from "./types/OrderTerm";

export default defineComponent({
  name: "App",
  components: {
    JobsList,
  },
  setup() {
    const jobs = ref<Job[]>([
      { title: "Software Engineer", location: "U.S.A (Remote)", salary: 30000, id: "1" },
      { title: "Sr. Vue Developer", location: "Paris, France", salary: 40000, id: "2" },
      { title: "Backend Developer (MongoDB)", location: "Rotterdam, Netherlands", salary: 35000, id: "3" },
      { title: "Sr. DevOps", location: "Hellsinki, Finland", salary: 21000, id: "4" },
      { title: "ML/AI Engineer", location: "India (Remote)", salary: 32000, id: "5" },
    ]);

    const order = ref<OrderTerm>("title");

    const handleClick = (term: OrderTerm) => {
      order.value = term;
    };

    return { jobs, handleClick, order };
  },
});
</script>

<style>
header {
  text-align: center;
}
header .order {
  margin-top: 20px;
}
button {
  margin: 0 10px;
  color: #1195c9;
  border: 3px solid #1195c9;
  background: #d5f0ff;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}
</style>
