<template>
<ion-page>
<ion-header>
<ion-toolbar>
<ion-buttons slot="start">
<ion-back-button default-href="/" />
</ion-buttons>
<ion-title>Tarefas</ion-title>
</ion-toolbar>
</ion-header>
<ion-content class="ion-padding">
<!-- Campo para nova tarefa -->
 <ion-card>
  <ion-card-header>
    <ion-card-title>
      Minhas Tarefas
    </ion-card-title>
  </ion-card-header>
  <ion-card-content>
<ion-item>
<ion-input
      v-model="novaTarefa"
      placeholder="Digite uma tarefa">
</ion-input>
</ion-item>
<ion-button button=true expand="block" @click="adicionarTarefa">
    Adicionar <ion-icon :icon="checkmarkDoneOutline"></ion-icon>
</ion-button>
</ion-card-content>
</ion-card>
<!-- Estado vazio -->
<p v-if="tarefas.length === 0">
    Nenhuma tarefa cadastrada. Adicione a primeira!
</p>
<ion-card>
  <ion-card-header>
    <ion-card-title>
      Lista Mabi
    </ion-card-title>
  </ion-card-header>
  <ion-card-content>
<!-- Lista de tarefas -->
<ion-list v-else->
<ion-item v-for="(tarefa, index) in tarefas" :key="index">
<ion-label>
        {{ tarefa }}
</ion-label>
<ion-button color="danger" fill="clear" @click="removerTarefa(index)"> <ion-icon :icon="closeCircleOutline"></ion-icon></ion-button>
</ion-item>
</ion-list>
</ion-card-content>
</ion-card>
</ion-content>
</ion-page>
</template>
<script setup lang="ts">
import {IonPage,IonHeader,IonToolbar,IonTitle,IonContent,IonItem,IonInput,IonButton,IonList,IonLabel,IonButtons,IonBackButton,IonIcon} from '@ionic/vue'
import { ref } from 'vue'
import {closeCircleOutline} from "ionicons/icons"
import {checkmarkDoneOutline} from "ionicons/icons"
const novaTarefa = ref('')
const tarefas = ref<string[]>([])
const adicionarTarefa = () => {
  if (novaTarefa.value.trim() === '') return
  tarefas.value.push(novaTarefa.value)
  novaTarefa.value = ''
}
const removerTarefa = (index:number) => {
  tarefas.value.splice(index, 1)
}
</script>

<style scoped>

ion-content::part(background){
    background: #c95e93;
  }

  ion-button::part(background){
    background-color: #eb93bf;
  }

</style>