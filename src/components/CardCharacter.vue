<template>
    <InternaMain>
    <div>
        <v-card class="" max-width="344" color="#5dff18" v-on:click="detailsPage(id)">
            <v-img v-if="images" :alt="`Imagem do produto ${title}`" :src="images" height="200" />
            <v-card-text>
                <strong class="red--text text--lighten-5">{{ title }}</strong>
            </v-card-text>
        </v-card>
    </div>
</InternaMain>
</template>
  
<script>
import InternaMain from '@/components/InternaMain.vue';
export default {
    name: 'CardCharacter',
  components: {
    InternaMain,
  },
    props: {
        images: String,
        title: String,
        status: String,
        species: String,
        page: String,
        id: Number,
    },
    methods: {
        detailsPage(event) {
            this.$router.push({ name: 'Details page', params: { id: event } })
        }
    },
}
</script>