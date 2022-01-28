<template>
    <v-main fluid>
        <v-form>
            <v-file-input 
                label="Seleciona o arquivo"
                append-outer-icon="mdi-send"
                multiple 
                chips 
                v-model="files"
                @click:append-outer="processaArquivo" />

            
        </v-form>
        <div class="pills">
            <pill v-for="word in groupedWords" :key="word.name" :name="word.name" :amount="word.amount"/>
        </div>
    </v-main>
</template>

<script>
import {ipcRenderer} from 'electron';
import Pill from './Pill.vue'

export default {
    components: { Pill },
    
    data: function() {
        return {
            files: [],
            groupedWords: []
        }
    },

    methods: {
        processaArquivo() {    
            const paths = this.files.map(f => f.path)            
            ipcRenderer.send('process-subtitles', paths)
            ipcRenderer.on('process-subtitles', (event, resp) => {
                this.groupedWords = resp                
            })
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