<script setup>
import { ref } from "vue";

import { useDropZone } from "@vueuse/core";

const emit = defineEmits(["close"]);

const fileInput = ref(null);
const files = ref([]);
const dropZoneRef = ref(null);

const triggerFileInput = () => {
	fileInput.value.click();
};

const onFileInputChange = (event) => {
	const selectedFiles = Array.from(event.target.files);
	handleFiles(selectedFiles);
	event.target.value = "";
};

const handleFiles = (newFiles) => {
	if (!newFiles || newFiles.length === 0) return;

	files.value = [...files.value, ...newFiles];

	console.log("Files received:", newFiles);
};

const { isOverDropZone } = useDropZone(dropZoneRef, {
	onDrop: handleFiles,
	dataTypes: [
		"application/pdf",
		"image/jpeg",
		"image/png",
		"text/*",
		"text/plain",
		"text/html",
		"text/css",
		"text/javascript",
		"text/markdown",
		"application/json",
		"application/xml",
		"application/javascript",
		"application/x-httpd-php",
		"application/x-sh",
		"application/x-python",
		"application/x-java",
		"application/x-csharp",
		"application/sql",
		"application/x-ruby",
		"application/x-c",
		"application/x-cpp",
		"application/x-typescript",
		"application/x-shellscript",
		"application/x-yaml",
		"application/x-toml",
		"application/x-lua",
		"application/x-go",
		"application/x-swift",
		"application/x-rust",
		"application/x-kotlin",
		"application/x-vue",
		"application/x-react",
		"application/x-node",
		"application/x-svelte",
		"application/x-solidity",
	],
	accept: [
		".pdf",
		".jpeg",
		".jpg",
		".png",
		".txt",
		".html",
		".css",
		".js",
		".ts",
		".json",
		".xml",
		".php",
		".py",
		".java",
		".cs",
		".sql",
		".rb",
		".c",
		".cpp",
		".sh",
		".md",
		".vue",
		".jsx",
		".tsx",
		".yaml",
		".yml",
		".toml",
		".lua",
		".go",
		".swift",
		".rs",
		".kt",
		".svelte",
		".sol",
	],
	multiple: true,
});
</script>

<template>
	<div class="wrapper">
		<div class="upper-element">
			<h1>Leave us a Message</h1>
			<font-awesome-icon
				icon="fa-xmark"
				size="2x"
				color="white"
				style="cursor: pointer"
				@click="$emit('close')"
			/>
		</div>
		<div class="lower-element">
			<div class="name">
				<label>Your name (Optional)</label>
				<input type="text" />
			</div>
			<div class="email-address">
				<label>Email Address</label>
				<input type="email" />
			</div>
			<div class="help-section">
				<label>How can we help you?</label>
				<textarea></textarea>
			</div>
			<div class="files">
				<label>Attachment</label>
				<div
					ref="dropZoneRef"
					@click="triggerFileInput"
					class="custom-file-upload"
					:class="{ 'drop-active': isOverDropZone }"
				>
					<div class="drag-drop-area">
						<font-awesome-icon
							icon="fa-link"
							size="1x"
							:style="{
								color: isOverDropZone ? '#066678' : '#a6a6a6',
								opacity: isOverDropZone ? '0.3' : '0.8',
							}"
						/>
						<p>
							{{
								isOverDropZone
									? "Drop Files Here"
									: "Add up to 5 files"
							}}
						</p>
					</div>
					<input
						type="file"
						ref="fileInput"
						@change="handleFileUpload"
						style="display: none"
					/>
				</div>
			</div>
			<div class="footer">
				<p>GCCoEd</p>
				<button>Send</button>
			</div>
		</div>
	</div>
</template>

<style scoped>
.wrapper {
	display: flex;
	flex-direction: column;
	width: 100%;
	height: 100%;
	padding: 20px;
	overflow: hidden;
}

.upper-element {
	background-color: #309cb0;
	padding: 20px;
	display: flex;
	justify-content: space-between;
	border-radius: 20px 20px 0 0;
	align-items: center;
}

.upper-element h1 {
	font-size: 1.3rem;
	font-weight: 600;
	text-align: center;
}

.lower-element {
	display: flex;
	flex-direction: column;
	justify-content: center;
	align-items: center;
	background-color: #fff;
	border-radius: 0 0 20px 20px;
	overflow: hidden;
	height: max-content;
	padding: 20px;
	border: 3px solid #309cb0;
}

.name,
.email-address,
.help-section,
.files {
	display: flex;
	flex-direction: column;
	width: 100%;
	margin-bottom: 20px;
}

label {
	font-size: 1rem;
	font-weight: 600;
	margin-bottom: 10px;
}

textarea {
	resize: none;
	height: 100px;
}

input {
	height: 40px;
}

.footer {
	display: flex;
	justify-content: space-between;
	width: 100%;
	align-items: center;
	margin-top: 20px;
}

.footer p {
	color: #0c434d;
	font-weight: 600;
}

button {
	background-color: #066678;
	color: white;
	padding: 10px 20px;
	border-radius: 10px;
	border: none;
	cursor: pointer;
	font-size: 1rem;
}

.custom-file-upload {
	display: flex;
	justify-content: center;
	align-items: center;
	padding: 10px;
	border: 1px dashed #066678;
	cursor: pointer;
	user-select: none;
}

.drag-drop-area {
	display: flex;
	flex-direction: row;
}

.custom-file-upload {
	display: flex;
	justify-content: center;
	align-items: center;
	padding: 20px;
	border: 2px dashed #066678;
	border-radius: 8px;
	cursor: pointer;
	transition: all 0.2s;
	background-color: rgba(6, 102, 120, 0.05);
}

.drop-active {
	background-color: rgba(6, 102, 120, 0.1);
	border-color: #309cb0;
	transform: scale(1.01);
}

.drag-drop-area {
	display: flex;
	align-items: center;
	gap: 10px;
}
</style>
