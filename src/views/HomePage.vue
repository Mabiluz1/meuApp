<template>
<ion-page>
<ion-header :translucent="true">
<ion-toolbar>
<ion-title>Blank</ion-title>
</ion-toolbar>
</ion-header>
<ion-content :fullscreen="true">
<ion-header collapse="condense">
<ion-toolbar>
<ion-title size="large">Blank</ion-title>
</ion-toolbar>
</ion-header>
<div class="inicial">
 
<p>Bem Vindo A tela Inicial </p>
 
</div>
</ion-content>
<ion-button  @click="router.push('/tarefas')">ir para tarefa</ion-button>
</ion-page>
</template>
<script setup lang="ts">
import { IonButton, IonContent, IonHeader, IonPage, IonTitle, IonToolbar } from '@ionic/vue';
import router from '@/router';
</script>
<style scoped>

.inicial {
 
 
    display: flex;
    justify-content: center; /* horizontal */
    align-items: center; /* vertical */
    height: 100vh; /* altura total da viewport */
 
 
}
 
 
.botao {
 
   
 
}
</style>