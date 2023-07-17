<script>
import axios from 'axios';
import ProjectCard from './Projects/ProjectCard.vue';

export default {
  components: {
    ProjectCard,
  },

  data() {
    return {
      arrProjects: [],
      currentPage: 1,
      nPages: 0,
      activePage: 1,
    };
  },
  methods: {
    changePage(page) {
      this.currentPage = page;
      this.getProjects();
    },

    nextPage() {
      this.currentPage++;
      this.getProjects();
    },

    previousPage() {
      this.currentPage--;
      this.getProjects();
    },

    getProjects() {
      axios
        .get('http://localhost:8000/api/projects', {
          params: {
            page: this.currentPage,
          },
        })
        .then(response => {
          this.arrProjects = response.data.data;
          this.nPages = response.data.last_page;
        });
    }
  },
  created() {
    axios
      .get('http://localhost:8000/api/projects', {
        params: {
          page: this.currentPage,
        }
      })
      .then(response => {
        this.arrProjects = response.data.data;
        this.nPages = response.data.last_page;
      });
  },
};
</script>

<template>
  <main>
    <div class="container my-5">
      <div class="row row-cols-3 row-cols-sm-2 row-cols-md-3">
        <ProjectCard v-for="project in arrProjects" :key="project.id" :project="project" />
      </div>

    </div>
  </main>
  <div class="container d-flex justify-content-end">
    <nav>
      <ul class="pagination">
        <li class="page-item">
          <a class="page-link" href="#" @click="previousPage()">Previous</a>
        </li>

        <li v-for="page in nPages" :key="page" class="page-item" :class="{ active: page == currentPage }">
          <a class="page-link" href="#" @click="changePage(page)">
            {{ page }}
          </a>
        </li>

        <li class="page-item">
          <a class="page-link" href="#" @click="nextPage()">Next</a>
        </li>
      </ul>
    </nav>
  </div>
</template>


<style></style>