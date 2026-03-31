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
            <ion-input v-model="novaTarefa" placeholder="Digite uma tarefa">
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
          <CardTarefa
            v-for="tarefa in tarefas"
            :key="tarefa.id"
            :tarefa="tarefa"
            @remover="removerTarefa"
            @concluir="concluirTarefa"
          ></CardTarefa>
        </ion-card-content>
      </ion-card>
    </ion-content>
  </ion-page>
</template>
<script setup lang="ts">
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent, IonItem, IonInput, IonButton, IonButtons, IonBackButton, IonIcon } from '@ionic/vue'
import { ref, watch } from 'vue'
import { checkmarkDoneOutline } from "ionicons/icons"
import { useTarefas } from '../composables/useTarefas'
import CardTarefa from '../components/CardTarefa.vue'
const novaTarefa = ref('')
const {
  tarefas,
  // busca,
  // filtroAtivo,
  // filtradas,
  adicionar,
  remover,
  totalPendentes,
  concluir

} = useTarefas()

const adicionarTarefa = () => {
  adicionar(novaTarefa.value)
  novaTarefa.value = ''
}
const removerTarefa = (index: number) => {
  remover(index)
}

const concluirTarefa = (id: number) => {
  concluir(id)
}

watch(totalPendentes, (valor) => {
 if (valor === 0 && tarefas.value.length > 0) {
 // Exibir IonAlert, IonToast ou alert() simples
 alert('🎉 Parabéns! Todas as tarefas foram concluídas!')
 }
})

</script>

<style scoped>
ion-content::part(background) {
  background: #c95e93;
}
</style>