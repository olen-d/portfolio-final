<!--SocialComponent.vue-->
<template>
    <div id="social">
        <span v-for="item in social" class="social-items">
            <a :href="item.href" :title="`Olen Daelhousen on ${item.text}`"><span :class="item.icon"></span></a>&nbsp;
        </span>
    </div>
</template>

<script>
 
    module.exports = {

        data: () => {
            return {
                social: []
            }
        },

        created() {
            fetch("http://localhost:3031/api/social/user/olen.d")
                .then((response) => {
                    return response.json();
                })
                .then((json) => {
                    this.social = json.social;
                });
            // ajax.get("http://localhost:3031/api/social/user/olen.d")
            // .then(response => {
            //     response = JSON.parse(response);
            //     this.social = response.social;
            // });
        }

    }
</script>
