<template>
    <InternaMain>
        <v-img v-if="list.image" :alt="`Imagem Detalhes ${title}`" :src="list.image" contain max-height="500" />
        <h1 class="bg-white">Episódios com {{ list.name }}.</h1>
        <v-row>
            <v-col v-for="item in episode" :key="item.id" cols="3" class="pa-0">
                <CardCharacter page="episode" :status="list.status" :title="item.name" :species="item.air_date"
                    :key="item.index" />
            </v-col>
        </v-row>
    </InternaMain>
</template>
  
<script>
import axios from "axios";
import CardCharacter from '@/components/CardCharacter.vue';
import InternaMain from '@/components/InternaMain.vue';

export default {
    name: 'CharacterDetail',

    components: {
        CardCharacter,
        InternaMain,
    },

    data() {
        return {
            id: null,
            list: null,
            episode: null,
        }
    },
    watch: {
        id: function () {
            this.fetchData(this.id);
        },
        list: function () {
            this.episode = [];
            this.list.episode.forEach(element =>
                axios.get(element).then(
                    response => this.episode.push(response.data),
                )
            );
        }
    },
    created() {
        this.id = this.$route.params.id;
    },
    methods: {
        fetchData: function (event) {
            axios.get('https://rickandmortyapi.com/api/character/' + event).then(
                response => this.list = response.data,
            );
        }
    }
}
</script>