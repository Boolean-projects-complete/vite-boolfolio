<script>
import axios from 'axios';

export default {
    data() {
        return {
            arrProject: [],
        };
    },
    created(){
        //richiesta dati al server
        axios.get('http://localhost:8000/api/projects', {
            params: {
                page: this.Npage
            },
        })
        .then(response => (this.arrProject = response.data.data))
    }
};
</script>

<template>

<h5>questi sono i nostri post</h5>
<ul>
    <li v-for="project in arrProject" :key="project.id">{{ project.title }}</li>
</ul>

<nav aria-label="Page navigation example">
  <ul class="pagination">
    <li class="page-item">
      <a class="page-link" href="#" aria-label="Previous">
        <span aria-hidden="true">&laquo;</span>
      </a>
    </li>
    <li class="page-item"><a class="page-link" href="#">1</a></li>
    <li class="page-item"><a class="page-link" href="#">2</a></li>
    <li class="page-item"><a class="page-link" href="#">3</a></li>
    <li class="page-item">
      <a class="page-link" href="#" aria-label="Next">
        <span aria-hidden="true">&raquo;</span>
      </a>
    </li>
  </ul>
</nav>
</template>


<style>

</style>