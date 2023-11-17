<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>To-Do</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">To-Do</ion-title>
        </ion-toolbar>
      </ion-header>

      <ion-button @click="showAlert">Mostrar Alerta</ion-button>
    </ion-content>
  </ion-page>
</template>

<script>
import { defineComponent } from "vue";
import { 
  IonAlert,
  alertController,
 } from "@ionic/vue";

export default defineComponent({
  components: {
    IonAlert,
    alertController,
  },
  data() {
    return {
      myList: ["Help", "Me", "Sleep"], // Substitua isso com sua lista
    };
  },
  methods: {
    async showAlert() {
      const alert = await alertController.create({
        header: "Minha Lista",
        message: this.renderList(),
        buttons: ["OK"],
      });

      await alert.present();
    },
    renderList() {
      // Função para renderizar a lista como uma string HTML
      return this.myList.map((item) => `<li>${item}</li>`).join("");
    },
  },
});
</script>