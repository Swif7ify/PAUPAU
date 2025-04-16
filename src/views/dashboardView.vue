<script setup>
import { ref, onMounted } from 'vue';

const userName = ref('John Doe Mendoza')
const proficiency = ref('Advanced')

const bio = ref('Lorem ipsum dolor sit amet,Lorem ipsum dolor sit amet,Lorem ipsum dolor sit amet,Lorem ipsum dolor sit amet,Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis')

const starFilled = ref(4); // number of star na ma fifilled
const yearLevel = ref(2)
const department = ref('College of Computer Studies')
const program = ref('BSCS')

const days = ref('MONDAY-TUESDAY')
const duration = ref(2)

const isEdit = ref(false)

const courseCard = ref([
    "Computer Programming", "Ethics", "Information Management", "Networking", "Database"
    , "Discrete Mathematics"
])

const openEditInformation = () => {
    isEdit.value = !isEdit.value
}


</script>


<template>
    <div class="sidebar">
        <div class="upper-element">
            <div>
                <h1>Hi, Mentor!</h1>
                <img src="https://placehold.co/600x400" alt="profile-pic">
            </div>
            <div>
                <h2>{{ userName }}</h2>
                <i><p>{{ proficiency }}</p></i>
                <div class="stars">
                    <span class="filledStar" v-for="i in 5" :key="i">
                        <span v-if="i <= starFilled">★</span>
                        <span v-else>☆</span>
                    </span>
                </div>
            </div>
        </div>
        <div class="footer-element">
            <div class="bio-container">
                <h1>BIO</h1>
                <div>
                    <p v-if="!isEdit">{{ bio }}</p>
                    <textarea v-else :value="bio" placeholder="Write your bio here..."></textarea>
                </div>
            </div>
            <div class="user-information">
                <h1>User Information</h1>
                <div class="lines">
                    <h3>Year Level: </h3>
                    <div>
                        <p v-if="!isEdit">{{ yearLevel }}</p>
                        <input v-else :value="yearLevel" type="text">
                    </div>
                </div>
                <div class="lines">
                    <h3>Department: </h3>
                    <div>
                        <p v-if="!isEdit">{{ department }}</p>
                        <input v-else :value="department" type="text">
                    </div>
                </div>
                <div class="lines">
                    <h3>Program: </h3>
                    <div>
                        <p v-if="!isEdit">{{ program }}</p>
                        <input v-else :value="program" type="text">
                    </div>
                </div>
            </div>
            <div class="availability">
                <h1>Availability</h1>
                <div class="lines">
                    <h3>Days: </h3>
                    <div>
                        <p v-if="!isEdit">{{ days }}</p>
                        <input v-else :value="days" type="text">
                    </div>
                </div>
                <div class="lines">
                    <h3>Duration: </h3>
                    <div>
                        <p v-if="!isEdit">{{ duration }}</p>
                        <input v-else :value="duration" type="text">
                    </div>
                </div>
            </div>
            <div class="course-offered">
                <h1>Course Offered</h1>
                <div class="course-grid">
                    <div v-for="(card, index) in courseCard" :key="index" class="course-card">
                        <div class="lines">
                           <div>
                                <p :title="card" v-if="!isEdit">{{ card }}</p>
                                <input v-else :value="card" type="text">
                           </div>
                        </div>
                    </div>
                </div>
            </div>
            <div class="edit-information">
                <button @click="openEditInformation">{{isEdit ? 'Save' : 'Edit'}}</button>
            </div>
        </div>
    </div>

    <div class="main-content">
        <div class="topbar">
            <div class="topbar-container">
                <p>Sessions</p>
                <p>Records</p>
                <p>Files</p>
            </div>
        </div>
    </div>
</template>

<style scoped src="../assets/dashboard/dashboard.css"></style>
<style scoped src="../assets/dashboard/color.css"></style>