<script>
import { ref } from '@vue/reactivity'
export default {
    name: 'ColorPicker',
    setup() {

        let colors = [
            'red', 'blue', 'green', 'black'
        ]
        let message = ref('Pick a color....')
        const matchColor = (value) => {

            const randomNumber = Math.floor(Math.random() * colors.length)

            if (colors[randomNumber] === value) {
                message.value = `You won.... [answer: ${colors[randomNumber]}]`
            } else {
                message.value = `You lose.... [answer: ${colors[randomNumber]}]`
            }
        }

        return { colors, message, matchColor }
    }

}

</script>
<template>
    <div class="main">
        <h3>Color Picker Game</h3>
        <div>{{ message }}</div>
            <div v-for="color in colors" :key="color" class="pickerBtns">
                <button @click="matchColor(color)" class="pickerBtn" :style="`color: ${color}`">{{ color }}</button>
            </div>
    </div>
</template>

<style scoped>
.main {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}

.pickerBtns{
    display: flex;
    align-items: center;
    justify-content: center;
}

.pickerBtn {
    padding: 10px 40px;
    margin: 5px;
    border: 1px solid #eee;
    cursor: pointer;
    border-radius: 5px;
}
</style>