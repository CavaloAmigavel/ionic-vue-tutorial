<template>
	<ion-page>
		<ion-header>
			<ion-toolbar>
				<ion-title>Info</ion-title>
			</ion-toolbar>
		</ion-header>
		<ion-content :fullscreen="true">
			<ion-header collapse="condense">
				<ion-toolbar>
					<ion-title size="large">Tab 2</ion-title>
				</ion-toolbar>
			</ion-header>

			<ion-button style="display: flex; justify-content: center;" id="present-alert">Update information</ion-button>
			<ion-alert
				trigger="present-alert"
				header="Please enter your info"
				:buttons="alertButtons"
				:inputs="alertInputs"
				@didDismiss="onDismiss"
			>
			</ion-alert>
			<ion-button style="display: flex; justify-content: center;" @click="showList">Show information</ion-button>
			
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
	IonButton,
	IonAlert,
	IonList,
	IonItem,
	IonLabel,
	IonInput,
	alertController 
} from "@ionic/vue";
import { onMounted, ref } from "vue";

let info = {
	name: "",
	nickname: "",
	age: "",
	about: "",
};

const showButton = ["Ok"];

const alertButtons = [
	{
		text: "Cancel",
		role: "cancel",
		handler: () => {
			console.log("Alert Cancel");
		},
	},
	{
		text: "Ok",
		role: "ok",
		handler: () => {
			console.log("Alert Ok");
		},
	},
];

const alertInputs = [
	{
		placeholder: "Name",
	},
	{
		placeholder: "Nickname (max 8 characters)",
		attributes: {
			maxlength: 8,
		},
	},
	{
		type: "number",
		placeholder: "Age",
		min: 1,
		max: 100,
	},
	{
		type: "textarea",
		placeholder: "A little about yourself",
	},
];

const showList = async () => {
	console.log("oi");
	console.log(info);

	const alert = await alertController.create({
    header: 'Information',
    message: "I'm " + info.name + ", but you can call me " + info.nickname + ". I'm " + info.age + " years old and " + info.about + ".",
    buttons: ['OK'],
  });

  await alert.present();
};



const onDismiss = (event: CustomEvent) => {
	if (event.detail.role === "ok") {
		//info = event.detail.data.values;

		info.name = event.detail.data.values[0];
		info.nickname = event.detail.data.values[1];
		info.age = event.detail.data.values[2];
		info.about = event.detail.data.values[3];

		console.log(info);
	}
};
</script>
