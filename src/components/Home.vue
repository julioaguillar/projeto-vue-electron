<template>
    <v-main fluid>
        <v-form>
            <v-file-input 
                label="Seleciona o arquivo"
                append-icon="mdi-send"
                multiple 
                chips 
                v-model="files"
                @click:append="processaArquivo" />

            
        </v-form>
        <div class="pills">
            <pill v-for="word in groupedWords" :key="word.name" :name="word.name" :amount="word.amount"/>
        </div>
    </v-main>
</template>

<script>
import Pill from './Pill.vue'

export default {
    components: { Pill },

    data: function() {
        return {
            files: [],
            groupedWords: [
                { name: 'i', amount: 1234 },
                { name: 'you', amount: 900 },
                { name: 'he', amount: 853 },                
            ]

        }
    },

    methods: {
        processaArquivo() {
            console.log(this.files)
        }        
    }

}
</script>

<style>

    .pills {
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;
    }

</style>