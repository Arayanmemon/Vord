<template>
    <div>
        <select name="">
            <option v-for="font in fonts" :key="font">{{font}}</option>
        </select>
        <button @click="fontinc">Font+</button>
        <button @click="fontdec">Font-</button>
        <button @click="italic">Italic</button>
        <button @click="bold">Bold</button>
        <button @click="toLower">Lowercase</button>
        <button @click="toUpper">Uppercase</button>
        <button @click="copy">CopyText</button>
        <input type="color" v-model="color" @change="changecolor">
        <button @click="remSpace">Remove Space</button>
    </div>
    <div>
        <textarea cols="90" rows="20" @keyup="Check()" v-model="text"></textarea>
    </div>
    <div>
        <p>Words: {{words}}</p>
        <p>Characters: {{chars}}</p>
        <p>Lines: {{lines}}</p>
    </div>
</template>

<script>
import { ref } from 'vue';
export default {
    setup() {
        const words = ref(null)
        const chars = ref(null)
        const lines = ref(null)
        const text = ref("")
        const word = ref([])
        const fontsize = ref(14)
        const color = ref("#000000")
        const fonts = ref(['Arial'])

        const Check=()=>{
            lines.value = text.value.split('.').length
            word.value = text.value.split(' ')
            words.value = word.value.length
            chars.value = text.value.length
        }
        const toLower=()=>{
            text.value = text.value.toLowerCase()
        }
        const toUpper=()=>{
            text.value = text.value.toUpperCase()
        }
        const copy=()=>{
            navigator.clipboard.writeText(text.value)
        }
        const fontinc =()=>{
            fontsize.value += 2
            document.querySelector('textarea').style.fontSize = fontsize.value+'px'
        }
        const fontdec =()=>{
            fontsize.value -= 2
            document.querySelector('textarea').style.fontSize = fontsize.value+'px'
        }
        const remSpace=()=>{
            text.value = text.value.replace(/\s+/g,' ').trim()
        }
        const italic=()=>{
            if(document.querySelector('textarea').style.fontStyle == 'italic'){
                document.querySelector('textarea').style.fontStyle = 'normal'
            }else{
                document.querySelector('textarea').style.fontStyle = 'italic'
            }
        }
        const bold=()=>{
            if(document.querySelector('textarea').style.fontWeight == 'bold'){
                document.querySelector('textarea').style.fontWeight = 'normal'
            }else{
                document.querySelector('textarea').style.fontWeight = 'bold'
            }
        }
        const changecolor=()=>{
            document.querySelector('textarea').style.color = color.value
        }

        return{fonts, words, chars, text, lines, color, Check, toLower, toUpper, copy, fontinc, fontdec, remSpace, italic, bold, changecolor}
    }
}
</script>

<style scoped>
textarea{
    padding: 10px;
    border: 2px solid #ccc;
    border-radius: 5px;
    width: 50%;
}
button{
    padding: 3px;
    cursor: pointer;
    margin-bottom: 2px;
}
</style>