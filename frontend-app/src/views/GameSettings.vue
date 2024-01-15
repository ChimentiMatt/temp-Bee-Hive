<template>
    <div class="bg-primary-green h-screen">

        <Navbar />

        <form v-if="!settingsChosen" v-on:submit.prevent="submitForm" class="flex flex-col justify-center items-center drop-shadow-lg">
            <div class="w-[20rem] flex flex-col border-b-2 items-center mt-[2rem] text-[24px] font-bold text-primary-blue">

                <h1 class="text-[40px] text-white drop-shadow-lg">Game Settings</h1>
                
                <div class="w-[20rem] flex border-b-2 items-center mt-[4rem] text-right">
                    <label>Difficulty</label>
                    <select v-model="forms.difficulty" class="w-full ml-[2rem]  mt-2 bg-transparent text-right pr-2">
                        <option value="easy">Easy</option>
                        <option value="hard">Hard</option>
                        <option value="myWords">My Words</option>
                    </select>
                </div>
                
                <div class="w-[20rem] flex border-b-2 items-center mt-[1rem] whitespace-nowrap">
                    <label>Number of Words</label>
                    <input
                        v-model="forms.numOfWords"
                        type="number"
                        class="text-right w-full mt-2 py-4 px-6 border border-gray-200 rounded-lg bg-transparent border-none outline-none"
                    >
                </div>
                
                <div class="w-[20rem] flex border-b-2 items-center mt-[2rem]">
                    <label>Voice</label>
                    <select v-model="forms.voice" class="w-full ml-[2rem]  mt-2 bg-transparent text-right pr-2">
                        <option value="bob">Bob</option>
                        <option value="sara">Sara</option>
                    </select>
                </div>
            </div>
            
            <SubmitBtn text="Game Start"/>
        </form>
        <div v-else> 
            <PlayView v-model="settingsChosen" :difficulty="forms.difficulty" :numOfWords="forms.numOfWords" :forms.voice="voice" :settingsChosen="settingsChosen"/>
        </div>
    </div>
        
</template>

<script>
import Input from '@/components/Input.vue';
import Navbar from '@/components/Navbar.vue';
import PlayView from './PlayView.vue';
import LogoutBtn from '@/components/LogoutBtn.vue'
import SubmitBtn from '@/components/SubmitBtn.vue';


export default {
    components: { 
        Input,
        SubmitBtn,
        Navbar,
        PlayView,
        LogoutBtn
    },

    data() {
        return {
            settingsChosen: false,
            forms: {
                difficulty: 'easy',
                numOfWords: 10,
                voice: 'Bob',
            },
            errors: []
        }
    },

    methods: {
        submitForm() {
            this.settingsChosen = true
        }
    }
}
</script>