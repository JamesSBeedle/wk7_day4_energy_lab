<template>
    <div class="timings">
        <p><b>Start Time: {{startTime}}</b></p>
        <p><b>End Time: {{endTime}}</b></p>
    </div>
</template>

<script>
export default {
    name: 'date-range',
    props: ['startTime', 'endTime'],
}
</script>

<style>
.timings{
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-column-gap: 30px;
}
</style>