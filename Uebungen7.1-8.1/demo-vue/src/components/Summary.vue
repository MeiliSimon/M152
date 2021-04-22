<template>
 Gesamter Durschnitt: {{ totalAverage }}<br />
        Mangelpunkte: {{ pointsBelow4 }}
        <hr />
        {{ passed ? 'Bestanden!' : 'Nicht bestanden!' }}
</template>

<script>
export default {
  name: 'Summary',
  props: {
    subjects: Array
  },
  methods: {
            getAverage: function(grades) {
                let total = 0;
                grades.forEach(grade => total += grade);
                const avg = total / grades.length;
                return Math.round(avg * 2) / 2; // Round to 0.5
            },
        },
   computed: {
       totalAverage: function() {
           let subjectsTotal = 0;
           this.subjects.forEach(subject => {
               subjectsTotal += this.getAverage(subject.grades);
           })
           const avg = subjectsTotal / this.subjects.length;
           return Math.round(avg * 2) / 2;
       },
       pointsBelow4: function() {
           let total = 0;
           this.subjects.forEach(subject => {
               const subjectAvg = this.getAverage(subject.grades);
               if (subjectAvg < 4) {
                   total += (4 - subjectAvg)
               }
           });
           return total;
       },
       passed: function() {
           if (this.totalAverage < 4) {
               return false;
           }
           if (this.pointsBelow4 > 1 && this.totalAverage < 4.2) {
               return false;
           }
           if (this.pointsBelow4 > 2 && this.totalAverage < 4.5) {
               return false;
           }
           return true;
       }
   }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
