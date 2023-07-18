<script>
import axios from 'axios';
import ProjectCard from './Projects/ProjectCard.vue';
import { store } from '../store';

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
      store,
    };
  },
  methods: {
    // changePage(page) {
    //   this.currentPage = page;
    //   this.getProjects();
    // },

    // nextPage() {
    //   this.currentPage++;
    //   this.getProjects();
    // },

    toNextPage() {
      this.currentPage != this.nPages ? this.currentPage++ : null;
    },

    // previousPage() {
    //   this.currentPage--;
    //   this.getProjects();
    // },

    toPrevPage() {
      this.currentPage != 1 ? this.currentPage-- : null;
    },


    getProjects() {
      // axios
      //   .get('http://localhost:8000/api/projects', {
      //     params: {
      //       page: this.currentPage,
      //     },
      //   })
      //   .then(response => {
      //     this.arrProjects = response.data.data;
      //     this.nPages = response.data.last_page;
      //   });

      axios
        .get(this.store.baseUrl + 'api/projects', {
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
    // axios
    //   .get('http://localhost:8000/api/projects', {
    //     params: {
    //       page: this.currentPage,
    //     }
    //   })
    //   .then(response => {
    //     this.arrProjects = response.data.data;
    //     this.nPages = response.data.last_page;
    //   });

    this.getProjects();
  },

  watch: {
    currentPage() {
      this.getProjects();
    }
  }
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
        <li class="page-item" :class="{ disabled: currentPage == 1 }">
          <!-- <a class="page-link" @click="previousPage()">Previous</a> -->
          <a class="page-link" @click="toPrevPage">Previous</a>
        </li>

        <li v-for="page in nPages" :key="page" class="page-item" :class="{ active: page == currentPage }">
          <!-- <a class="page-link" href="#" @click="changePage(page)">
            {{ page }}
          </a> -->
          <a class="page-link" href="#" @click="currentPage = page">
            {{ page }}
          </a>
        </li>

        <!-- <li class="page-item">
          <a class="page-link" href="#" @click="nextPage()">Next</a>
        </li> -->
        <li class="page-item" :class="{ disabled: currentPage == nPages }">
          <a class="page-link" href="#" @click="toNextPage()">Next</a>
        </li>
      </ul>
    </nav>
  </div>
</template>


<style lang="scss"></style>