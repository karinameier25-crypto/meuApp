<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Mini app de Tarefas</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content class="ion-padding">
      <h2>Bem-vinda!</h2>
      <p>Este aplicativo permite adicionar e gerenciar tarefas.</p>
      <ion-button id="btn" @click='router.push("/tarefas")'>
        Ir para Tarefas
      </ion-button>
    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
import router from '@/router';
import { IonContent, IonHeader, IonPage, IonTitle, IonToolbar, IonButton } from '@ionic/vue';
</script>

<style scoped>
#container {
  text-align: center;
  
  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}

#container strong {
  font-size: 20px;
  line-height: 26px;
}

#container p {
  font-size: 16px;
  line-height: 22px;
  
  color: #f3f3f3;
  
  margin: 0;
}

#container a {
  text-decoration: none;
}
</style>
