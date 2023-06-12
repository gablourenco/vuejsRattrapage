<script setup>
import { onMounted,ref } from 'vue';
import axios from 'axios'

let data = ref('')

onMounted(async () => {
    const response = await axios.get('https://data.nantesmetropole.fr/api/records/1.0/search/?dataset=244400404_agenda-evenements-nantes-nantes-metropole&q=&facet=emetteur&facet=rubrique&facet=lieu&facet=ville&facet=lieu_quartier')
    data.value = response.data
    console.log(data)
})
</script>

<template>
    <div>
        <input class="dateDebut" type="date">
        <input class="dateFin" type="date">
        <input class="quartier" type="text">
        <iframe src="https://data.nantesmetropole.fr/explore/embed/dataset/244400404_agenda-evenements-nantes-nantes-metropole/map/?disjunctive.emetteur&disjunctive.rubrique&disjunctive.lieu&disjunctive.ville&disjunctive.lieu_quartier&location=7,47.34301,-1.63147&basemap=jawg.streets&static=false&datasetcard=false&scrollWheelZoom=false" width="400" height="300" frameborder="0"></iframe>
        <iframe src="https://data.nantesmetropole.fr/explore/embed/dataset/244400404_agenda-evenements-nantes-nantes-metropole/table/?disjunctive.emetteur&disjunctive.rubrique&disjunctive.lieu&disjunctive.ville&disjunctive.lieu_quartier&location=15,47.19095,-1.68293&basemap=jawg.streets&static=false&datasetcard=false" width="400" height="300" frameborder="0"></iframe>
        <p>{{ data.records }}</p>
    </div>
</template>