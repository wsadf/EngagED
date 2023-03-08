<template>
    <div>
        <v-text-field background-color="#FFF" label="Pesquise o nome do personagem..." filled v-model="search">
        </v-text-field>
        <v-row>
            <v-col v-for="item in filterCharacter" :key="item.id" cols="3" class="pa-0">
                <CardCharacter page="character" :id="item.id" :images="item.image" :title="item.name" :status="item.status"
                    :species="item.species" />
            </v-col>
        </v-row>
    </div>
</template>

<script>
import axios from "axios";
import CardCharacter from '@/components/CardCharacter.vue';


export default {
    name: 'ListCharacter',
    components: {
        CardCharacter,
    },
    data() {
        return {
            item: 1,
            list: null,
            search: ""
        }
    },
    computed: {
        filterCharacter: function () {
            if (this.search) {
                return this.list.filter(lists => {
                    return lists.name.toLowerCase().includes(this.search.toLowerCase());
                })
            } else {
                return this.list;
            }
        }
    },
    watch: {
        item: function () {
            this.fetchData(this.item);
        }
    },
    created() {
        this.fetchData(this.item);
        this.listPage();
    },
    methods: {
        fetchData: function (event) {
            axios.get('https://rickandmortyapi.com/api/character?page=' + event).then(response => this.list = response.data.results);
        },
        listPage: function () {
            axios.get('https://rickandmortyapi.com/api/character?page=' + event).then(response => this.pagition = response.data.info.pages);
        },
    }
}
</script>