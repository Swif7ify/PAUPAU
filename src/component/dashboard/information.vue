<script setup>
import { ref, reactive } from "vue";

const personalData = reactive({});
const profileData = reactive({});

const emit = defineEmits(["close"]);

function toCamelCase(str) {
	return str
		.replace(/(?:^\w|[A-Z]|\b\w)/g, (word, index) => {
			return index === 0 ? word.toLowerCase() : word.toUpperCase();
		})
		.replace(/\s+/g, "");
}

const inputFieldPersonalInformation = ref([
	"Full Name",
	"Year Level",
	"Program",
	"City/Municipality",
	"Gender",
	"Department",
	"Contact Number",
	"Barangay",
]);

const inputFieldProfileInformation = ref([
	"Teaching Modality",
	"Days of Availability",
	"Proficiency Level",
	"Teaching Style",
	"Preferred Session Duration",
	"Course Offered",
	"Short Bio",
	"Tutoring Experience",
]);

inputFieldPersonalInformation.value.forEach((field) => {
	personalData[toCamelCase(field)] = "";
});

inputFieldProfileInformation.value.forEach((field) => {
	profileData[toCamelCase(field)] = "";
});

const closeEditInformation = () => {
	emit("close");
};
</script>

<template>
	<div class="edit-information">
		<div class="upper-element">
			<h1>Edit Information</h1>
			<img
				@click="closeEditInformation"
				src="../../../public/exit.svg"
				alt="exit"
			/>
		</div>
		<div class="lower-element">
			<div class="lower-grid">
				<div class="personal-information">
					<h1>I. PERSONAL INFORMATION</h1>
					<div class="input-wrapper">
						<div
							v-for="(
								field, index
							) in inputFieldPersonalInformation"
							:key="index"
							class="input-fields"
						>
							<label>{{ field }}</label>
							<input
								type="text"
								v-model="personalData[toCamelCase(field)]"
							/>
						</div>
					</div>
				</div>
				<div class="profile-information">
					<h1>II. PROFILE INFORMATION</h1>
					<div class="input-wrapper">
						<div
							v-for="(
								field, index
							) in inputFieldProfileInformation"
							:key="index"
							class="input-fields"
						>
							<label>{{ field }}</label>
							<input
								type="text"
								v-model="profileData[toCamelCase(field)]"
							/>
						</div>
					</div>
				</div>
			</div>
		</div>
		<div class="save">
			<button>Save Changes</button>
		</div>
	</div>
</template>

<style scoped>
.edit-information {
	width: 650px;
	height: max-content;
	display: flex;
	flex-direction: column;
	gap: 20px;
	z-index: 2000;
	box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
	border-radius: 20px;
	background-color: white;
}

.upper-element {
	display: flex;
	flex-direction: row;
	background-color: #0c434d;
	justify-content: center;
	align-items: center;
	padding: 15px 20px;
    border-radius: 20px 20px 0 0;
}

.upper-element h1 {
	font-size: 24px;
	color: #ffffff;
}

.upper-element img {
	position: absolute;
	right: 20px;
	width: 20px;
	height: 20px;
	cursor: pointer;
}

.lower-element {
	padding: 0 20px;
	background-color: white;
}

.lower-element h1 {
	font-size: 18px;
	color: #0c434d;
	margin-bottom: 20px;
}

.lower-grid {
	display: grid;
	grid-template-columns: 1fr 1fr;
	gap: 40px;
}

.input-wrapper {
	display: flex;
	flex-direction: column;
	gap: 15px;
}

.input-fields {
	display: flex;
	flex-direction: column;
}

.input-fields label {
	color: #116174;
	margin-bottom: 5px;
}

.input-fields input {
	border-radius: 10px;
	border: 1px solid #0c434d;
	font-size: 16px;
	color: #0c434d;
	background-color: #d9d9d9;
	padding: 5px;
}

.personal-information,
.profile-information {
	padding: 0 20px 0 20px;
	border-radius: 20px;
}

.save {
	display: flex;
	justify-content: flex-end;
	padding: 10px;
	border-radius: 0 0 20px 20px !important;
}

.save button {
	background-color: #006981;
	color: white;
	border: none;
	padding: 10px 20px;
	border-radius: 10px;
	cursor: pointer;
	font-size: 16px;
}
</style>
