<script setup>
import { ref } from "vue";
import { useDropZone } from "@vueuse/core";

const fileInput = ref(null);
const files = ref([]);
const dropZoneRef = ref(null);

const triggerFileInput = () => {
	fileInput.value.click();
};

const removeFile = (index) => {
	files.value = files.value.filter((_, i) => i !== index);
};

const getFileIcon = (fileType) => {
	if (fileType.includes("image")) {
		return "https://cdn-icons-png.flaticon.com/512/1829/1829548.png";
	} else if (fileType.includes("pdf")) {
		return "https://cdn-icons-png.flaticon.com/512/2921/2921222.png";
	} else if (fileType.includes("word") || fileType.includes("document")) {
		return "https://cdn-icons-png.flaticon.com/512/281/281760.png";
	} else if (fileType.includes("spreadsheet") || fileType.includes("excel")) {
		return "https://cdn-icons-png.flaticon.com/512/281/281778.png";
	} else if (fileType.includes("text")) {
		return "https://cdn-icons-png.flaticon.com/512/3094/3094154.png";
	} else {
		return "https://cdn-icons-png.flaticon.com/512/25/25657.png";
	}
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
	<div class="files-wrapper">
		<div class="top-element">
			<font-awesome-icon
				icon="fa-file-lines"
				size="3x"
				style="color: #fff"
			/>
			<h1>FILES AND DOCUMENTS</h1>
		</div>
		<div class="lower-element">
			<div class="lower-grid">
				<div class="upload-file">
					<div
						ref="dropZoneRef"
						class="drop-zone"
						:class="{ 'drop-zone-active': isOverDropZone }"
					>
						<font-awesome-icon
							icon="fa-file-arrow-up"
							size="10x"
							:style="{
								color: isOverDropZone ? '#066678' : '#a6a6a6',
								opacity: isOverDropZone ? '0.3' : '0.1',
							}"
						/>
						<p>
							{{
								isOverDropZone
									? "Drop Files Here"
									: "Drag Files to Upload"
							}}
						</p>
					</div>
					<div class="browse-file">
						<input
							type="file"
							ref="fileInput"
							class="file-upload"
							@change="onFileInputChange"
							accept="*"
							style="display: none"
						/>
					</div>
					<div @click="triggerFileInput" class="custom-file-upload">
						<h1>Browse Files</h1>
					</div>
				</div>
				<div class="displayed-files">
					<h1>Uploaded Files</h1>
					<div class="displayed-container">
						<div
							v-if="files.length > 0"
							v-for="(file, index) in files"
							:key="index"
							class="files"
						>
							<div>
								<img :src="getFileIcon(file.type)" alt="file" />
								<p>{{ file.name }}</p>
							</div>
							<div>
								<font-awesome-icon
									icon="fa-xmark"
									size="2x"
									style="color: #066678; cursor: pointer"
									@click="removeFile(index)"
								/>
							</div>
						</div>
						<div v-else class="no-files">
							<p>No files uploaded yet</p>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>

<style scoped>
.files-wrapper {
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

.lower-element {
	display: flex;
	flex-direction: row;
	justify-content: center;
	align-items: center;
	background-color: #fff;
	border-radius: 0 0 20px 20px;
	overflow: hidden;
	border: 3px solid #0c434d;
	padding: 40px;
	height: 600px;
}

.lower-grid {
	display: grid;
	grid-template-columns: 1fr 1fr;
	grid-gap: 50px;
	width: 100%;
	height: 100%;
}

.displayed-container {
	height: 500px;
	overflow-y: auto;
	overflow-x: hidden;
	display: flex;
	gap: 10px;
	flex-direction: column;
}

.drop-zone {
	border-right: 3px dashed #a6a6a6;
	border-top: 3px dashed #a6a6a6;
	border-left: 3px dashed #a6a6a6;
	width: 100%;
	height: 100%;
	display: flex;
	justify-content: center;
	align-items: center;
	flex-direction: column;
}

.drop-zone p {
	color: #a6a6a6;
	font-size: 1.5rem;
	font-weight: 400;
	user-select: none;
}

.upload-file {
	display: flex;
	flex-direction: column;
	justify-content: center;
	align-items: center;
	padding: 20px;
}

.custom-file-upload {
	background-color: #0c434d;
	color: #fff;
	width: 100%;
	height: 20%;
	display: flex;
	justify-content: center;
	align-items: center;
	cursor: pointer;
	user-select: none;
}

.drop-zone-active {
	border: 3px dashed #066678 !important;
	background-color: rgba(6, 102, 120, 0.05);
}

.file-list {
	display: flex;
	flex-direction: column;
	gap: 10px;
	width: 100%;
}

.file-item {
	background-color: #f5f5f5;
	padding: 10px 15px;
	border-radius: 5px;
	border-left: 4px solid #066678;
}

.no-files {
	display: flex;
	justify-content: center;
	align-items: center;
	height: 100%;
	color: #a6a6a6;
}

.displayed-files {
	display: flex;
	flex-direction: column;
	gap: 20px;
}

.displayed-files h1 {
	color: #066678;
	font-size: 2rem;
	font-weight: 600;
	margin-bottom: 20px;
}

.displayed-files img {
	width: 40px;
	height: 40px;
	border-radius: 5px;
}

.files {
	display: flex;
	flex-direction: row;
	justify-content: space-between;
	align-items: center;
	background-color: #f5f5f5;
	padding: 10px 15px;
	border-radius: 5px;
	border-left: 4px solid #066678;
}

.files div:first-of-type {
	display: flex;
	flex-direction: row;
	justify-content: flex-start;
	align-items: center;
	gap: 10px;
}
</style>
