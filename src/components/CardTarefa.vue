<script setup lang='ts'>
import {IonCard, IonItem, IonCardContent, IonIcon, IonLabel, IonButton } from "@ionic/vue"
import {checkmarkCircle} from "ionicons/icons"
import {ellipseOutline} from "ionicons/icons"
import {trashOutline} from "ionicons/icons"
interface Tarefa { id: number; texto: string; feita: boolean }
const props = defineProps<{ tarefa: Tarefa }>()
const emit = defineEmits<{
    remover: [id: number]
    concluir: [id: number]
}>()
</script>
<template>
    <IonCard>
        <IonCardContent>
            <IonItem lines='none'>
                <IonIcon slot='start' :icon='props.tarefa.feita ? checkmarkCircle : ellipseOutline'
                    :color='props.tarefa.feita ? "success" : "medium"' @click='emit("concluir", props.tarefa.id)' />
                <IonLabel :style='props.tarefa.feita ? "text-decoration:line-through" : ""'>
                    {{ props.tarefa.texto }}
                </IonLabel>
                <IonButton slot='end' color='danger' @click='emit("remover", props.tarefa.id)'>
                    <IonIcon :icon='trashOutline' />
                </IonButton>
            </IonItem>
        </IonCardContent>
    </IonCard>
</template>