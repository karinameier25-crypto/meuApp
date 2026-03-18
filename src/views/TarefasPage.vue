```vue
<template>

<ion-page>

<ion-header>
<ion-toolbar>

<ion-buttons slot="start">
<ion-back-button defaultHref="/home"></ion-back-button>
</ion-buttons>

<ion-title>Tarefas</ion-title>

</ion-toolbar>
</ion-header>

<ion-content class="ion-padding">

    <ion-card>
        <ion-card-header>
            <ion-card-title>Nova Tarefa</ion-card-title>
        </ion-card-header>
        <ion-card-content>
<ion-item>
<ion-input
placeholder="Digite uma tarefa"
v-model="novaTarefa">
</ion-input>
</ion-item>


<ion-button expand="block" @click="adicionarTarefa">
Adicionar

<ion-icon slot="start" :icon="addOutline"></ion-icon>
</ion-button>
</ion-card-content>
</ion-card>

<p v-if="tarefas.length === 0">
Nenhuma tarefa cadastrada. Adicione a primeira!
</p>

<ion-card>
    <ion-card-header>
        <ion-card-title>Minhas Tarefas</ion-card-title>
    </ion-card-header>
    <ion-card-content>
<ion-list>

<ion-item v-for="(t, i) in tarefas" :key="i">

<ion-label>
{{ t }}
</ion-label>

<ion-button color="danger" @click="removerTarefa(i)">
Remover

<ion-icon slot="start" :icon="trashOutline"></ion-icon>


</ion-button>

</ion-item>

</ion-list>
</ion-card-content>
</ion-card>

</ion-content>

</ion-page>

</template>

<script setup lang="ts">

import {
IonPage,
IonHeader,
IonToolbar,
IonTitle,
IonContent,
IonItem,
IonInput,
IonButton,
IonList,
IonLabel,
IonBackButton,
IonButtons,
IonCard,
IonCardHeader,
IonCardTitle,
IonCardContent
} from '@ionic/vue'
import { IonIcon } from '@ionic/vue'
import {
addOutline, trashOutline,
} from 'ionicons/icons'

import { ref } from 'vue'
const novaTarefa = ref('')
const tarefas = ref<string[]>([])

function adicionarTarefa() {

if (novaTarefa.value.trim() === '') {
return
}

tarefas.value.push(novaTarefa.value)

novaTarefa.value = ''

}

function removerTarefa(index: number) {
tarefas.value.splice(index, 1)
}

</script>

<style scoped>

</style>
```
