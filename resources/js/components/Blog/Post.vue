<template>
    <div class="uk-card uk-card-default uk-width-1-3@m">
        <div class="uk-card-header">
            <div class="uk-grid-small uk-flex-middle" uk-grid>
                <div class="uk-width-auto">
                    <img class="uk-border-circle" width="40" height="40" :src="image">
                </div>
                <div class="uk-width-expand">
                    <h3 class="uk-card-title uk-margin-remove-bottom">{{ title }}</h3>
                    <p class="uk-text-meta uk-margin-remove-top"><time datetime="2016-04-01T19:00">{{ date }}</time></p>
                </div>
            </div>
        </div>
        <div class="uk-card-body">
            <p>{{ body }}</p>
        </div>
        <div class="uk-card-footer">
            <button @click.prevent="show(id)" href="#" class="uk-button uk-button-text">Read more</button>
        </div>
    </div>
</template>

<script>
export default {
    name: "Post",
    props: {
        title: {
            type: String,
            default: "NULL"
        },
        body: {
            type: String,
            default: "NULL"
        },
        date: {
            type: String,
            default: "NULL"
        },
        image: {
            type: String,
            default: "NULL"
        },
        id: {
            type: Number,
            default: "NULL"
        }
    },
    methods: {
        show(id) {
            this.$router.push('/post/' + id)
        }
    }
}
</script>

<style scoped>

</style>
