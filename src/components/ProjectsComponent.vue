<!--ProjectsComponent.vue-->
<template>
    <div id="projects" class="container">
        <div class="row">
            <div class="one column">
                &nbsp;
            </div>
            <div class="ten columns">
                <h1>Projects</h1>
            </div>
            <div class="one column">
                &nbsp;
            </div>
        </div>
        <div class="row">
            <div class="one column">
                &nbsp;
            </div>
            <div class="ten columns projects">
                <div v-for="project in results.projects" class="card u-pull-left">
                    <div class="card-title"> <!-- TODO - fix src hardcode -->
                        <img :src="`${publicPath}${project.screenshot}`" width="350" height="auto" :alt="`Screenshot of ${project.projectTitle}`">
                        <h2>
                            {{project.projectTitle}}
                        </h2>
                        <p>
                            {{project.description}}
                        </p>
                        <p>
                            <a :href="project.deployedLink">Visit the project</a>.
                        </p>
                        <p>
                            <a :href="project.repoLink">See the code on Github</a>
                        </p>
                    </div>
                </div>
            </div>
            <div class="one column">
                &nbsp;
            </div>
        </div>
    </div>
</template>

<script>

    module.exports = {

        data: () => {
            return {
            results: [],
            publicPath: process.env.BASE_URL
            }
        },

        created() {
            fetch("http://localhost:3031/api/projects")
                .then((response) => {
                    return response.json();
                })
                .then((json) => {
                    this.results = json;
                });
        }
    }

</script>
