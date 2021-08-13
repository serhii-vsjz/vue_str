<template>
    <div>
        <div uk-alert v-if="error">
            <a class="uk-alert-close" uk-close></a>
            <h3>Проверте правильность введенных полей</h3>
        </div>
        <form>
            <fieldset class="uk-fieldset">

                <legend class="uk-legend">Опубликовать пост</legend>

                <div class="uk-margin">
                    <input class="uk-input" v-model="form.title" type="text" placeholder="Заголовок">
                </div>


                <div class="uk-margin">
                    <textarea class="uk-textarea" v-model="form.body" rows="5" placeholder="Текст"></textarea>
                </div>

                <button class="uk-button uk-button-secondary uk-width-1-1" @click.prevent="store">
                    <div uk-spinner v-if="loading"></div>
                    <span v-else>Опубликовать</span>
                </button>
            </fieldset>
        </form>
    </div>
</template>

<script>
import axios from 'axios';

export default {

    components: {

    },
    data: () => ({
        form: {
            title: "",
            body: "",
        },
        loading: false,
        error: false
    }),
    methods: {
        store() {
            this.loading = true;
            axios.post('/api/posts', this.form, {
                headers: {
                    "Content-type": "application/json"
                }
            })
            .then(res => {
                if (res.data.status) {
                    this.$router.push('/post/' + res.data.post.id)
                } else {
                    this.loading = false;
                    this.error = true;
                }
            })
        }
    }
}
</script>

<style scoped>

</style>
