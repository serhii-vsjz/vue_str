<template>
    <nav class="uk-navbar-container" uk-navbar>
        <div class="uk-navbar-center">

            <ul class="uk-navbar-nav">
<!--                <li class="uk-active"><a href="#">Active</a></li>-->
                <li v-for="link in links">
                    <router-link :to="link.href">{{ link.title }}</router-link>
                </li>
            </ul>

        </div>
    </nav>
</template>

<script>
export default {
    data() {
        return {
            links: [
                {
                    title: "Главная",
                    href: "/"
                },
                {
                    title: "Блог",
                    href: "/blog"
                },
                {
                    title: "Создать пост",
                    href: "/create"
                },
            ]
        }
    }
}
</script>

<style scoped>

</style>
