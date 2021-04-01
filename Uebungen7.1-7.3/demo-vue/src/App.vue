<template>
<div>
  <div class="main">
    <h1>Hello World</h1>

    <ul class="todos">
        <li v-for="item in tasks">{{ item }}</li>
    </ul>

    <input type="text" placeholder="Neues Item hinzufügen" v-model="newItem" />
    <input type="submit" value="Hinzufügen" v-on:click="addItem(newItem)" />
    </div>
<div class="school">
   <h1>Schulnoten</h1>
    <span v-for="fach in noten">
      <p>{{fach.name}}</p>
    <ul>
      <li v-for="grade in fach.grades">{{grade}}</li>
    </ul>
      
    </span>
</div>
</div>
  
</template>

<script>
    export default {
    data: function() {
        return {
            tasks: [
                "Einkaufen",
                "Rasen mähen",
                "Katze füttern"
            ],
            noten: [
                {
                    name: "Mathematik",
                    grades: [5,4.7,3.5,4.1] 
                },
                {
                    name: "Geschichte",
                    grades: [5.5,4.9,5.75] 
                },
                {
                    name: "Physik",
                    grades: [2,2.7,4.3] 
                },
                {
                    name: "Deutsch",
                    grades: [4.25,4.1,3.5] 
                }
            ]
        }
    },
    methods: {
        addItem: function(item) {
            this.tasks.push(item);
        }
    },
    computed: {
    itemCount: function() {
        return this.tasks.length;
    }
}
}
</script>

<style lang="scss">
    div {
        max-width: 500px;
        margin: 0 auto;
        background-color: #eee;
        padding: 20px;

        h1 {
            text-align: center;
        }
    }
</style>