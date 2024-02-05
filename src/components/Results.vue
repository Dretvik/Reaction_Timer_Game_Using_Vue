<template>
      <div class="resultsBlock">
        <p>Reaction time: {{ score }}ms</p>
        <p class="rank"> {{ rank }}</p>
    </div>
</template>

<script>
export default {
    props: ['score'],
    data() {
        return {
            rank: null,
        }
    },
    mounted() {
        if (this.score < 100) {
            this.rank = 'Unhuman! Hacker.. :P'
        } else if (this.score < 250) {
            this.rank = 'Ninja Fingers!';
        } else if (this.score < 400) {
            this.rank = 'Rapid Reflexes';
        } else {
            this.rank = 'Snail Pace!';
        }
        console.log('Your rank: ',this.rank);
    }
}
</script>

<style>
.resultsBlock {
    width: 400px;
    border-radius: 20px;
    background: crimson;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}
.rank {
    font-size: 1.4em;
    font-weight: bold;
}
</style>