<template>
	<ion-page>
		<ion-header>
			<ion-toolbar>
				<ion-title>Hello!</ion-title>
			</ion-toolbar>
		</ion-header>
		<ion-content :fullscreen="true">
			<ion-header collapse="condense">
				<ion-toolbar>
					<ion-title size="large">Tab 1</ion-title>
				</ion-toolbar>
			</ion-header>

			<ion-fab vertical="bottom" horizontal="center" slot="fixed">
				<ion-fab-button id="hello-alert"> Hello! </ion-fab-button>
			</ion-fab>

			<ion-alert
				trigger="hello-alert"
				header="Hello World!"
				sub-header="Welcome to the Ionic Vue app."
				:buttons="alertButtons"
			></ion-alert>
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
	IonFab,
	IonFabButton,
	IonAlert,
} from "@ionic/vue";

const alertButtons = ["Thank you!"];
</script>
