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
  IonSegment,
  IonSegmentButton,
  IonLabel
} from '@ionic/vue'

import { useTarefas } from '../composables/useTarefas'
import CardTarefa from '../components/CardTarefa.vue'

const {
  busca,
  filtroAtivo,
  filtradas,
  totalPendentes,
  adicionar,
  remover,
  concluir
} = useTarefas()

const novaTarefa = ref('')

function adicionarNova() {
  adicionar(novaTarefa.value)
  novaTarefa.value = ''
}
</script>

<template>
  <IonPage>
    <IonHeader>
      <IonToolbar>
        <IonTitle>Minhas Tarefas</IonTitle>
      </IonToolbar>
    </IonHeader>

    <IonContent class="ion-padding">
      <IonItem>
        <IonInput
          v-model="novaTarefa"
          placeholder="Digite uma nova tarefa"
        />
        <IonButton @click="adicionarNova">Adicionar</IonButton>
      </IonItem>

      <IonItem>
        <IonInput
          v-model="busca"
          placeholder="Buscar tarefa"
        />
      </IonItem>

      <IonSegment v-model="filtroAtivo">
        <IonSegmentButton value="todas">
          <IonLabel>Todas</IonLabel>
        </IonSegmentButton>

        <IonSegmentButton value="pendentes">
          <IonLabel>Pendentes</IonLabel>
        </IonSegmentButton>

        <IonSegmentButton value="feitas">
          <IonLabel>Feitas</IonLabel>
        </IonSegmentButton>
      </IonSegment>

      <p>Pendentes: {{ totalPendentes }}</p>

      <CardTarefa
        v-for="tarefa in filtradas"
        :key="tarefa.id"
        :tarefa="tarefa"
        @remover="remover"
        @concluir="concluir"
      />
    </IonContent>
  </IonPage>
</template>


<style scoped>

</style>
```
