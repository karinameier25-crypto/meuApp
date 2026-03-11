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

<ion-item>
<ion-input
placeholder="Digite uma tarefa"
v-model="novaTarefa">
</ion-input>
</ion-item>

<ion-button expand="block" @click="adicionarTarefa">
Adicionar
</ion-button>

<p v-if="tarefas.length === 0">
Nenhuma tarefa cadastrada. Adicione a primeira!
</p>

<ion-list>

<ion-item v-for="(t, i) in tarefas" :key="i">

<ion-label>
{{ t }}
</ion-label>

<ion-button color="danger" @click="removerTarefa(i)">
Remover
</ion-button>

</ion-item>

</ion-list>

</ion-content>

</ion-page>

</template>

<script setup lang="ts">

import { ref } from 'vue'

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
IonButtons
} from '@ionic/vue'

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
