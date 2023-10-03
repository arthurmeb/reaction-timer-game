<template>
    <div>
        <h3> Congrats </h3>
        <p :style="{color: textColour}">Your score is: {{ score }}ms!</p>
    </div>
</template>

<script>
export default {
    props: ['score'],
    data () {
        return {
            textColour: null
        }
    },        
    mounted() {
        if (this.score <= 700) {
            this.textColour = 'green'
            }
        else if (this.score <= 900) {
            this.textColour = 'orange'
        }
        else {
            this.textColour = 'red'
        }
        }
}
</script>

