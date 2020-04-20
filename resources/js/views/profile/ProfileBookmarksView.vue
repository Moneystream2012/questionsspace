<template>
    <div class="container my-3">
        <div class="row justify-content-center">
            <sidebar></sidebar>
            <div class="col-lg-8">
                <card-question-component v-for="(question, index) in this.user.bookmarks" :key="index" :question="question"></card-question-component>
            </div>
        </div>
    </div>
</template>

<script>
    import {mapState, mapActions } from "vuex";
    import sidebar from "../../components/profile/SidebarMenuComponent";
    import CardQuestionComponent from "../../components/questions/CardQuestionComponent";


    export default {
        components: {sidebar, CardQuestionComponent},

        computed:{
            ...mapState('auth', [
                'user'
            ]),
        },
        methods: {
            ...mapActions('auth', [
                'getUser'
            ]),
        },

        mounted() {
            console.log('Component mounted.');

            this.getUser();
        }
    }
</script>
