<script setup>
import { ref } from "vue";

const userInformation = ref([
	{
		userName: "Paulo Cordova",
		yearLevel: "2nd Year",
		course: "BSIT | CSS",
	},
	{
		userName: "Paulo Cordova",
		yearLevel: "2nd Year",
		course: "BSIT | CSS",
	},
	{
		userName: "Paulo Cordova",
		yearLevel: "2nd Year",
		course: "BSIT | CSS",
	},
	{
		userName: "Paulo Cordova",
		yearLevel: "2nd Year",
		course: "BSIT | CSS",
	},
	{
		userName: "Paulo Cordova",
		yearLevel: "2nd Year",
		course: "BSIT | CSS",
	},
	{
		userName: "Paulo Cordova",
		yearLevel: "2nd Year",
		course: "BSIT | CSS",
	},
	{
		userName: "Paulo Cordova",
		yearLevel: "2nd Year",
		course: "BSIT | CSS",
	},
	{
		userName: "Paulo Cordova",
		yearLevel: "2nd Year",
		course: "BSIT | CSS",
	},
	{
		userName: "Paulo Cordova",
		yearLevel: "2nd Year",
		course: "BSIT | CSS",
	},
	{
		userName: "Paulo Cordova",
		yearLevel: "2nd Year",
		course: "BSIT | CSS",
	},
	{
		userName: "Paulo Cordova",
		yearLevel: "2nd Year",
		course: "BSIT | CSS",
	},
	{
		userName: "Paulo Cordova",
		yearLevel: "2nd Year",
		course: "BSIT | CSS",
	},
	{
		userName: "Paulo Cordova",
		yearLevel: "2nd Year",
		course: "BSIT | CSS",
	},
	{
		userName: "Paulo Cordova",
		yearLevel: "2nd Year",
		course: "BSIT | CSS",
	},
	{
		userName: "Paulo Cordova",
		yearLevel: "2nd Year",
		course: "BSIT | CSS",
	},
	{
		userName: "Paulo Cordova",
		yearLevel: "2nd Year",
		course: "BSIT | CSS",
	},
	{
		userName: "Paulo Cordova",
		yearLevel: "2nd Year",
		course: "BSIT | CSS",
	},
	{
		userName: "Paulo Cordova",
		yearLevel: "2nd Year",
		course: "BSIT | CSS",
	},
	{
		userName: "Paulo Cordova",
		yearLevel: "2nd Year",
		course: "BSIT | CSS",
	},
	{
		userName: "Paulo Cordova",
		yearLevel: "2nd Year",
		course: "BSIT | CSS",
	},
	{
		userName: "Paulo Cordova",
		yearLevel: "2nd Year",
		course: "BSIT | CSS",
	},
	{
		userName: "Paulo Cordova",
		yearLevel: "2nd Year",
		course: "BSIT | CSS",
	},
	{
		userName: "Paulo Cordova",
		yearLevel: "2nd Year",
		course: "BSIT | CSS",
	},
	{
		userName: "Paulo Cordova",
		yearLevel: "2nd Year",
		course: "BSIT | CSS",
	},
	{
		userName: "Paulo Cordova",
		yearLevel: "2nd Year",
		course: "BSIT | CSS",
	},
	{
		userName: "Paulo Cordova",
		yearLevel: "2nd Year",
		course: "BSIT | CSS",
	},
	{
		userName: "Paulo Cordova",
		yearLevel: "2nd Year",
		course: "BSIT | CSS",
	},
	{
		userName: "Paulo Cordova",
		yearLevel: "2nd Year",
		course: "BSIT | CSS",
	},
	{
		userName: "Paulo Cordova",
		yearLevel: "2nd Year",
		course: "BSIT | CSS",
	},
	{
		userName: "Paulo Cordova",
		yearLevel: "2nd Year",
		course: "BSIT | CSS",
	},
	{
		userName: "Paulo Cordova",
		yearLevel: "2nd Year",
		course: "BSIT | CSS",
	},
	{
		userName: "Paulo Cordova",
		yearLevel: "2nd Year",
		course: "BSIT | CSS",
	},
]);
</script>

<template>
	<div class="main-wrapper">
		<div class="user-grid">
			<div v-for="user in userInformation" class="user-card">
				<div class="upper-element">
					<img src="https://placehold.co/600x400" alt="profile-pic" />
					<h1>{{ user.userName }}</h1>
				</div>
				<div class="lower-element">
					<p>{{ user.yearLevel }}</p>
					<p>{{ user.course }}</p>
					<button>See More</button>
				</div>
			</div>
		</div>
	</div>
</template>

<style scoped>
.main-wrapper {
	display: flex;
	justify-content: center;
	align-items: center;
	width: 100%;
	height: 100%;
}

.user-grid {
	display: grid;
	grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
	gap: 20px;
	width: 100%;
	height: 100%;
	padding: 20px;
}

.user-card {
	background-color: #006981;
	border: 3px solid #0c434d;
	border-radius: 10px;
	padding: 20px;
}

.user-card img {
	width: 120px;
	height: 120px;
	object-fit: cover;
	border-radius: 50%;
}

.user-card h1 {
	color: #fff;
	font-size: 17px;
	text-align: center;
	margin: 10px 0;
}

.upper-element {
	display: flex;
	flex-direction: column;
	justify-content: center;
	align-items: center;
}

.lower-element {
	display: flex;
	flex-direction: column;
	justify-content: center;
	align-items: center;
}

.lower-element p {
	color: #fff;
	font-size: 14px;
	text-align: center;
}

.lower-element button {
	background-color: #349eb1;
	color: #fff;
	border: none;
	padding: 10px 20px;
	border-radius: 5px;
	cursor: pointer;
	margin-top: 20px;
}
</style>
