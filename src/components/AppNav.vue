<script>
export default {
    data() {
        return {
            searchStr: "",
        };
    }

}
</script>


<template>
    <nav class="navbar navbar-expand-lg bg-body-tertiary d-flex justify-content-between px-3">
        <div class="container-fluid">
            <a class="navbar-brand" href="#">Navbar</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav"
                aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav">
                    <li class="nav-item">
                        <router-link :to="{ name: 'home' }" class="nav-link active" aria-current="page">
                            Home
                        </router-link>
                    </li>
                    <li class="nav-item">
                        <router-link :to="{ name: 'projects.index' }" class="nav-link active" aria-current="page">
                            Projects
                        </router-link>
                    </li>
                </ul>
            </div>
        </div>
        <div class="container-fluid d-flex justify-content-end">
            <form class="d-flex" role="search" @submit.prevent="
                $router.push({
                    name: 'projects.index',
                    query: { q: searchStr },
                })
                ">
                <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search" name="q"
                    v-model="searchStr" />
                <button class="btn btn-outline-success" type="submit">
                    Search
                </button>
            </form>

        </div>
    </nav>
</template>


<style></style>