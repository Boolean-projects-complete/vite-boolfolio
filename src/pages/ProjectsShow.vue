<script>
import axios from 'axios';
import { store } from '../store';
import { DateTime } from 'luxon';
import App404 from "./App404.vue";

export default {
    data() {
        return {
            store,
            DateTime,
            is404: false,
            project: [],
        };
    },

    created() {
        // fai la richiesta axios
        axios
            .get(this.store.baseUrl + 'api/projects/' + this.$route.params.slug)
            .then((response) => {
                if (response.data.success) {
                    this.project = response.data.results;
                } else {
                    // this.$router.push({ name: "page404" });
                    this.is404 = true;
                }
            });
        console.log(this.project);
    },
    components: { App404 },
};
</script>

<template>
    <App404 v-if="is404" />
    <template v-else-if="project">
        <div class="d-flex flex-column">
            <div style="margin-left: 6rem;">
                <h1>{{ project.title }}</h1>
                <h5>Last update: {{ this.DateTime.now().toFormat("dd-MM-yyyy") }}</h5>
            </div>

            <div class="h-100 w-100 d-flex justify-content-center">
                <img :src="this.store.baseUrl + 'storage/' + project.image" class="img-fluid" :alt="project.id" />
            </div>

            <h5 class="py-3" style="text-align: justify; padding-inline: 6rem;">
                Lorem ipsum dolor sit amet consectetur adipisicing elit. Corporis excepturi aperiam sunt repudiandae,
                provident
                quo quidem hic quis voluptatem, alias, velit odio blanditiis? Non ratione vitae, a velit praesentium neque.
                Vero eveniet maiores voluptate nihil enim quaerat delectus ea, necessitatibus aliquam, unde porro numquam
                repellat! Pariatur qui nesciunt ea, libero excepturi reprehenderit laborum maiores repellat voluptatem
                eveniet
                natus reiciendis sequi!
                Suscipit, nulla ipsum dolorum autem sed odio labore molestias, hic voluptate soluta dolor! Autem quibusdam
                iste
                tenetur fugiat saepe obcaecati repellendus earum, laudantium et ab temporibus maxime atque qui inventore?
                Sed facilis veritatis totam voluptatum nemo ea sequi aut molestiae sunt assumenda quia neque eligendi veniam
                hic
                ipsa eaque ullam dolorum quasi, deleniti delectus obcaecati aliquam, tempora, quidem alias. Ipsum?
                Iste quibusdam incidunt repellat debitis molestiae placeat ratione quasi. Magni, excepturi laudantium saepe
                sint
                suscipit alias nostrum dignissimos sapiente, accusantium tenetur soluta facilis sit dolorem, deleniti
                consequatur cupiditate ullam nihil!
                Assumenda quam maiores rerum earum sit temporibus pariatur dolore repellat nisi deserunt neque, ut
                exercitationem officiis beatae, hic commodi itaque doloribus aliquam accusantium numquam facere dicta
                labore.
                Modi, voluptatibus amet!
                Consequuntur dolorum ad cumque alias voluptates quas ipsum nihil nam excepturi sunt! Unde, deleniti ducimus
                illo
                asperiores et quam, molestiae dolore corporis tempore quod neque libero, optio mollitia. Quod, reiciendis.
                Iste, praesentium quasi. Consequatur, tenetur. Corporis eveniet impedit debitis. Velit, pariatur aliquid
                ducimus
                rem labore voluptas dignissimos saepe unde asperiores quibusdam aspernatur laudantium, adipisci rerum
                obcaecati
                architecto blanditiis natus iusto.
                Autem unde aliquid, hic laudantium consequatur architecto itaque tenetur placeat omnis provident ea iusto ad
                quae officia at recusandae animi, natus aliquam incidunt nulla. Sapiente accusantium ut totam odio omnis!
                Suscipit aut molestias minus commodi ab, nam optio facilis harum quam similique assumenda nisi, quisquam
                fuga?
                Eos, dignissimos molestias totam maxime ipsa dolorem! Architecto, voluptates rerum! Incidunt aut doloribus
                tempore.
            </h5>
        </div>
    </template>
</template>

<style lang="scss"></style>