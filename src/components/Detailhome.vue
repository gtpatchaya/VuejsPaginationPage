<template>
  <b-container >
  <b-row align-v="center">
    <job-card v-for="job in displayjobs" :key="job.id" :name="job.name"></job-card> 
  </b-row>
   <b-pagination
      v-model="currentPage"
      :total-rows="rows"
      :per-page="perPage"
      first-text="First"
      prev-text="Prev"
      next-text="Next"
      last-text="Last"
      @input="paginate(currentPage)"
    ></b-pagination>
</b-container> 
</template>

<script>

import JobCard from '@/components/JobCard.vue';

export default {
  name: 'DetailHome',
  components : {"job-card" : JobCard},
  props: {
    msg: String
  },
  mounted(){
    this.fetchData();
  },
  data(){
    return {
      jobs : [],
      displayjobs : [],
      currentPage : 1,
      rows:1,
      perPage : 3
    }
  },
  methods : {
    async fetchData(){
      const res = await fetch("jobs.json");
      const val = await res.json();
      this.jobs = val;
      this.displayjobs = val.slice(0,3);
      this.rows = this.jobs.length;
      console.log(val); 
    },
    paginate(currentPage){
      const start  = (this.currentPage  -1) * this.perPage;
      this.displayjobs = this.jobs.slice(start , start+3);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
