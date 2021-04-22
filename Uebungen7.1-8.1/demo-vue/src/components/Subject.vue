<template>
   <h2>{{ subject.name }}</h2>

            <ul>
                <li v-for="grade in subject.grades">{{ grade }}</li>
            </ul>

            Durchschnitt: {{ getAverage(subject.grades) }}
            <hr />
</template>

<script>
export default {
  name: 'Subject',
  props: {
    subject: Array
  },
     methods: {
            getAverage: function(grades) {
                let total = 0;
                grades.forEach(grade => total += grade);
                const avg = total / grades.length;
                return Math.round(avg * 2) / 2; // Round to 0.5
            },
        }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
