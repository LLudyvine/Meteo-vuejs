<script setup lang="ts">
import { ref } from 'vue'

const titre = ref('Météo');
const informationMeteo = ref([{
    ville : "Beauvais",
    humidité : 55,
    temps : "🌦️ Légère pluie",
    temperature : 18,
    ressenti : 15,
    vent : {
        vitesse : 15,
        direction : "Nord-Est"
    }
},
{
    ville : "Brest",
    humidité : 76,
    temps : "🌧️ Pluie",
    temperature : 15,
    ressenti : 13,
    vent : {
        vitesse : 20,
        direction : "Nord-Est"
    }
},
{
    ville : "Paris",
    humidité : 44,
    temps : "☁️ Nuageux",
    temperature : 20,
    ressenti : 17,
    vent : {
        vitesse : 14,
        direction : "Nord-Est"
    }
},
{
    ville : "Pisseleu",
    humidité : 67,
    temps : "🌦️ Légère Pluie",
    temperature : 17,
    ressenti : 15,
    vent : {
        vitesse : 16,
        direction : "Nord-Est"
    }
},
{
    ville : "Lyon ",
    humidité : 33,
    temps : "🌤️ Ensoleillé",
    temperature : 25,
    ressenti : 24,
    vent : {
        vitesse : 10,
        direction : "Nord-Est"
    }
}
]);

const showInfo = ref(false);
function moreInformations(element) {
    elementSelectione.value = elementSelectione.value === null ? element : null
};
const elementSelectione = ref(null);


</script>

<template>
    <h1 class="titre">{{ titre }}</h1>
    <div class="content">
    <div v-for="element in informationMeteo" :key="element.ville" class="case" @click="moreInformations(element)">
        <p>{{ element.ville }}</p>
        <p>💧{{ element.humidité }}%</p>
        <p>{{ element.temps }}</p>
        <p> {{ element.temperature }}°C</p>
        <p>Ressenti {{ element.ressenti }}°C</p>
    </div>
    <div v-if="elementSelectione" class="deuxiemecase">
        <h3>Informations sur le vent :</h3>
            <p>🌬️{{ elementSelectione.vent.vitesse }}km/h</p>
            <p>{{ elementSelectione.vent.direction}}</p>
            <button @click="moreInformations" class="boutonvent">Fermer</button>
    </div>
    </div>
</template>

<style scoped>
    .titre {
        font-size : 25px;
        color : white;
        text-align: center;
        font-family: Arial, Helvetica, sans-serif;
        font-weight: bold;
    }
    .case {
        border : solid ;
        border-radius: 10px;
        border-style : none;
        display: flex;
        flex-direction: row;
        background : linear-gradient(#86B9EB, #CADCED);
        margin : 0px 400px 0px 400px;
        justify-content: center;
        font-family: Arial, Helvetica, sans-serif;
    }
    p {
        color : white;
        padding : 5px;
    }
    h3 {
        font-size : 15px;
        font-family: Arial, Helvetica, sans-serif;
        color : white;
    }
    .deuxiemecase {
        border : solid ;
        border-radius: 10px;
        border-style : none;
        display: flex;
        flex-direction: row;
        background : linear-gradient(#86B9EB, #CADCED);
        margin : 0px 400px 0px 400px;
        justify-content: center;
        font-family: Arial, Helvetica, sans-serif;
    }
    .boutonvent {
        border : solid #5E9CD6;
        border-radius: 10px;
        height: 30px;
        width: 60px;
        background-color: #86B9EB;
        color : white;
        margin : 10px;
    }
</style>