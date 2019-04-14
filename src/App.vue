<template>
  <div id="app">
    
    <navbar-component></navbar-component>

    <about-component></about-component>
		
    <projects-component></projects-component>

    <contact-component></contact-component>

    <div class="footer">
			<social-component></social-component>			
			<p>
				Copyright &copy; 2019 Olen Daelhousen
			</p>
		</div>
  </div> <!-- End App -->
</template>

<script>
const ajax = {
    post(url, data) {
        return new Promise ((resolve, reject) => {
            let xhr = new XMLHttpRequest();
            xhr.open("POST", url);
            xhr.setRequestHeader("Content-Type", "application/json");
            xhr.onload = () => {
                if (xhr.status === 200) {
                    let res = xhr.responseText;
                    resolve(res);
                } else {
                    reject({
                        status: 500,
                        error: "Internal server error. Failed to post http:// request."
                    });
                }
            }
            xhr.send(JSON.stringify({
                data
            }));
        })
    },

    get(url) {
        return new Promise ((resolve, reject) => {
            let xhr = new XMLHttpRequest();
            xhr.open("GET", url);
            xhr.onload = () => {
                if (xhr.status === 200) {
                    let data = xhr.responseText;
                    resolve(data);
                } else {
                    reject({
                        status: 500,
                        login: false,
                        error: "Internal server error. Failed to get http:// request."
                    });
                }
            }
            xhr.send();
        });
    }
}

import NavbarComponent from "./components/NavbarComponent.vue";
import AboutComponent from "./components/AboutComponent.vue";
import ProjectsComponent from "./components/ProjectsComponent.vue";
import ContactComponent from "./components/ContactComponent.vue";
import SocialComponent from "./components/SocialComponent.vue";

export default {
  name: 'app',

  components: {
    NavbarComponent,
    AboutComponent,
    ProjectsComponent,
    ContactComponent,
    SocialComponent
  }
}

</script>

<style>
  @import "./assets/css/normalize.css";
  @import "./assets/css/skeleton.css";
  @import "./assets/css/style.css";

/* #app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
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
} */
</style>
