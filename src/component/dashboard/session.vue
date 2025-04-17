<script setup>
import { ref } from "vue";
import Message from "../dashboard/message.vue";

const todaySchedule = ref([
	{
		subject: "Discrete Structures",
		name: "Paulo Cordova",
		data: "11/23/25",
		time: "8:00 AM - 10:00 AM",
		location: "Library, Room 101",
	},
	{
		subject: "Data Structures",
		name: "Aisha Patel",
		data: "11/23/25",
		time: "10:00 AM - 12:00 PM",
		location: "Library, Room 102",
	},
	{
		subject: "Software Engineering",
		name: "Rafael Gutierrez",
		data: "11/23/25",
		time: "1:00 PM - 3:00 PM",
		location: "Library, Room 103",
	},
	{
		subject: "Database Management",
		name: "Nina Thompson",
		data: "11/23/25",
		time: "3:00 PM - 5:00 PM",
		location: "Library, Room 104",
	},
	{
		subject: "Database Management",
		name: "Nina Thompson",
		data: "11/23/25",
		time: "3:00 PM - 5:00 PM",
		location: "Library, Room 104",
	},
]);

const upcommingSchedule = ref([
	{
		subject: "Discrete Structures",
		name: "Paulo Cordova",
		data: "11/23/25",
		time: "8:00 AM - 10:00 AM",
		location: "Library, Room 101",
	},
	{
		subject: "Data Structures",
		name: "Aisha Patel",
		data: "11/23/25",
		time: "10:00 AM - 12:00 PM",
		location: "Library, Room 102",
	},
	{
		subject: "Software Engineering",
		name: "Rafael Gutierrez",
		data: "11/23/25",
		time: "1:00 PM - 3:00 PM",
		location: "Library, Room 103",
	},
	{
		subject: "Database Management",
		name: "Nina Thompson",
		data: "11/23/25",
		time: "3:00 PM - 5:00 PM",
		location: "Library, Room 104",
	},
	{
		subject: "Database Management",
		name: "Nina Thompson",
		data: "11/23/25",
		time: "3:00 PM - 5:00 PM",
		location: "Library, Room 104",
	},
]);

const isMessage = ref(false);

const activePopup = ref({
	type: null,
	index: null,
});

const togglePopup = (type, index) => {
	if (activePopup.value.type === type && activePopup.value.index === index) {
		activePopup.value = { type: null, index: null };
	} else {
		activePopup.value = { type, index };
	}
};

const handleOptionClick = (option, item) => {
	switch (option) {
		case "remind":
			alert(`Set reminder for ${item.subject}`);
			break;
		case "reschedule":
			alert(`Reschedule ${item.subject}`);
			break;
		case "cancel":
			alert(`Cancel ${item.subject}`);
			break;
	}
	activePopup.value = { type: null, index: null };
};

const toggleMessage = () => {
	isMessage.value = !isMessage.value;
};
</script>

<template>
	<div class="session-wrapper">
		<div class="top-element">
			<font-awesome-icon icon="fa-calendar" size="3x" color="#fff" />
			<h1>SESSION SCHEDULE</h1>
		</div>
		<div class="lower-element">
			<div class="session-grid">
				<div class="session-card">
					<h1>TODAY</h1>
					<div
						v-for="(item, index) in todaySchedule"
						:key="index"
						class="today-card"
					>
						<div>
							<h1>{{ item.subject }}</h1>
							<div class="ellipsis-container">
								<font-awesome-icon
									icon="fa-ellipsis-h"
									size="2x"
									color="#066678"
									style="cursor: pointer"
									@click="togglePopup('today', index)"
								/>
								<!-- Popup Menu -->
								<transition name="fade" mode="out-in">
									<div
										v-if="
											activePopup.type === 'today' &&
											activePopup.index === index
										"
										class="popup-menu"
									>
										<div
											class="popup-option"
											@click="
												handleOptionClick(
													'remind',
													item
												)
											"
										>
											<font-awesome-icon
												icon="fa-bell"
												size="1x"
												color="#066678"
												style="margin-right: 10px"
											/>
											<p>Remind</p>
										</div>
										<div
											class="popup-option"
											@click="
												handleOptionClick(
													'reschedule',
													item
												)
											"
										>
											<font-awesome-icon
												icon="fa-calendar-alt"
												size="1x"
												color="#066678"
												style="margin-right: 10px"
											/>
											<p>Reschedule</p>
										</div>
										<div
											class="popup-option"
											@click="
												handleOptionClick(
													'cancel',
													item
												)
											"
										>
											<font-awesome-icon
												icon="fa-times"
												size="1x"
												color="#066678"
												style="margin-right: 10px"
											/>
											<p>Cancel</p>
										</div>
									</div>
								</transition>
							</div>
						</div>
						<div class="info name">
							<font-awesome-icon
								icon="fa-user"
								size="2x"
								color="#533566"
							/>
							<h2>{{ item.name }}</h2>
						</div>
						<div class="info">
							<font-awesome-icon
								icon="fa-calendar-alt"
								size="2x"
								color="#0084ce"
							/>
							<p>{{ item.data }}</p>
						</div>
						<div class="info">
							<font-awesome-icon
								icon="fa-clock"
								size="2x"
								color="#f8312f"
							/>
							<p>{{ item.time }}</p>
						</div>
						<div class="info last">
							<div>
								<font-awesome-icon
									icon="fa-map-marker-alt"
									size="2x"
									color="#f72197"
								/>
								<p>
									{{ item.location }}
								</p>
							</div>
							<div>
								<font-awesome-icon
									icon="fa-envelope"
									size="2x"
									color="#f72197"
									class="envelope"
									@click="toggleMessage"
								/>
							</div>
						</div>
					</div>
				</div>
				<div class="session-card">
					<h1>UPCOMING</h1>
					<div
						v-for="(item, index) in upcommingSchedule"
						:key="index"
						class="upcomming-card"
					>
						<div>
							<h1>{{ item.subject }}</h1>
							<div class="ellipsis-container">
								<font-awesome-icon
									icon="fa-ellipsis-h"
									size="2x"
									color="#066678"
									style="cursor: pointer"
									@click="togglePopup('upcoming', index)"
								/>
								<!-- Popup Menu -->
								<transition name="fade" mode="out-in">
									<div
										v-if="
											activePopup.type === 'upcoming' &&
											activePopup.index === index
										"
										class="popup-menu"
									>
										<div
											class="popup-option"
											@click="
												handleOptionClick(
													'remind',
													item
												)
											"
										>
											<font-awesome-icon
												icon="fa-bell"
												size="1x"
												color="#066678"
												style="margin-right: 10px"
											/>
											<p>Remind</p>
										</div>
										<div
											class="popup-option"
											@click="
												handleOptionClick(
													'reschedule',
													item
												)
											"
										>
											<font-awesome-icon
												icon="fa-calendar-alt"
												size="1x"
												color="#066678"
												style="margin-right: 10px"
											/>
											<p>Reschedule</p>
										</div>
										<div
											class="popup-option"
											@click="
												handleOptionClick(
													'cancel',
													item
												)
											"
										>
											<font-awesome-icon
												icon="fa-times"
												size="1x"
												color="#066678"
												style="margin-right: 10px"
											/>
											<p>Cancel</p>
										</div>
									</div>
								</transition>
							</div>
						</div>
						<div class="info name">
							<font-awesome-icon
								icon="fa-user"
								size="2x"
								color="#533566"
							/>
							<h2>{{ item.name }}</h2>
						</div>
						<div class="info">
							<font-awesome-icon
								icon="fa-calendar-alt"
								size="2x"
								color="#0084ce"
							/>
							<p>{{ item.data }}</p>
						</div>
						<div class="info">
							<font-awesome-icon
								icon="fa-clock"
								size="2x"
								color="#f8312f"
							/>
							<p>{{ item.time }}</p>
						</div>
						<div class="info last">
							<div>
								<font-awesome-icon
									icon="fa-map-marker-alt"
									size="2x"
									color="#f72197"
								/>
								<p>
									{{ item.location }}
								</p>
							</div>
							<div>
								<font-awesome-icon
									icon="fa-envelope"
									size="2x"
									color="#f72197"
									class="envelope"
									@click="toggleMessage"
								/>
							</div>
						</div>
					</div>
				</div>
			</div>
		</div>

		<Transition name="fade" mode="out-in">
			<div v-if="isMessage" class="message-pop-up">
				<Message @close="toggleMessage" />
			</div>
		</Transition>
	</div>
</template>

<style scoped>
.session-wrapper {
	display: flex;
	justify-content: center;
	flex-direction: column;
	width: 100%;
	overflow: hidden;
}

.top-element {
	display: flex;
	flex-direction: row;
	justify-content: flex-start;
	align-items: center;
	gap: 10px;
	background-color: #0c434d;
	padding: 20px 30px;
	border-radius: 20px 20px 0 0;
}

.top-element h1 {
	color: #fff;
	font-size: 2rem;
	font-weight: 600;
}

.ellipsis-container {
	position: relative;
}

.popup-menu {
	position: absolute;
	display: flex;
	flex-direction: column;
	justify-content: flex-start !important;
	top: 100%;
	right: 0;
	width: 150px;
	background-color: white;
	border: 1px solid #ddd;
	border-radius: 5px;
	box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
	z-index: 1000;
}

.popup-option {
	padding: 10px 15px;
	cursor: pointer;
	transition: background-color 0.2s;
	display: flex;
	flex-direction: row;
	justify-content: flex-start !important;
}

.popup-option:hover {
	background-color: #f5f5f5;
	color: #066678;
}

.popup-option:not(:last-child) {
	border-bottom: 1px solid #eee;
}

.lower-element {
	background-color: #fff;
	border: 3px solid #0c434d;
	padding: 10px 30px;
	flex: 1;
	overflow-y: auto;
}

.session-grid {
	display: grid;
	grid-template-columns: 1fr 1fr;
	gap: 100px;
	margin-top: 20px;
	height: 650px;
}

.session-card {
	display: flex;
	flex-direction: column;
	gap: 20px;
	padding: 0 0 20px 0;
}

.session-card h1 {
	color: #066678;
}

/* card */

.today-card,
.upcomming-card {
	display: flex;
	flex-direction: column;
	padding: 10px 20px;
	background-color: #f0f0f0;
}

.today-card:nth-of-type(4n + 1) {
	border-left: 10px solid #ff3131;
}

.today-card:nth-of-type(4n + 2) {
	border-left: 10px solid #ff66c4;
}

.today-card:nth-of-type(4n + 3) {
	border-left: 10px solid #ffe063;
}

.today-card:nth-of-type(4n) {
	border-left: 10px solid #ff914d;
}

.today-card div:nth-of-type(1),
.upcomming-card div:nth-of-type(1) {
	display: flex;
	justify-content: space-between;
	align-items: center;
}

.upcomming-card {
	border-left: 10px solid #006981;
}

.today-card div:nth-of-type(1) h1,
.upcomming-card div:nth-of-type(1) h1 {
	color: #0c434d;
	font-size: 1.3rem;
	font-weight: 600;
	text-decoration: underline;
}

.info {
	display: flex;
	flex-direction: row;
	align-items: center;
	gap: 10px;
}

.info h2 {
	color: #0c434d;
	font-size: 1rem;
	font-weight: 600;
}

.info p {
	color: #0c434d;
	font-size: 0.9rem;
}

.info svg {
	width: 15px;
}

.last {
	display: flex;
	justify-content: space-between;
	align-items: center;
	width: 100%;
}

.last div:first-of-type {
	gap: 10px;
}

.envelope {
	width: 25px !important;
	cursor: pointer;
}

.fade-enter-active,
.fade-leave-active {
	transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
	opacity: 0;
}

.fade-enter-to,
.fade-leave-from {
	opacity: 1;
}

.message-pop-up {
	position: fixed;
	top: 50%;
	left: 55%;
	transform: translate(-50%, -50%);
}
</style>
