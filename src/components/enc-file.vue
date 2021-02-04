<template>
	<div id="efile">
		<div class="main">
			<div class="left">
				<p>Sorry now we only support txt files !</p>
				<input
					class="input"
					@change="readFile"
					id="file"
					type="file"
					accept="txt"
				/>
				<input class="input" v-model.lazy="key" type="number" />
				<button @click="encrypt">Encrypt</button>
			</div>
			<div v-show="fileReady" class="right">
				<h3>Here is your encrypted data you can download it :)</h3>
				<hr />
				<a download id="dLink">Download</a>
			</div>
		</div>
	</div>
</template>
<script>
export default {
	name: "etext",
	data() {
		return {
      fileReady: false,
			text: "",
			cLetters: "ABCDEFGHIJKLMNOPQRSTUVWXYZ".split(""),
			sLetters: "abcdefghijklmnopqrstuvwxyz".split(""),
      key: 0,
      encrypted: ""
		};
	},
	methods: {
		encrypt() {
			var arr = this.text.split("");
			var k = parseInt(this.key, 10);
			var enT = [];
			arr.forEach((l) => {
				if (l.match(/^[A-Za-z]+$/)) {
					if (l == l.toUpperCase()) {
						enT.push(
							this.cLetters[
								(this.cLetters.indexOf(l) + k) % this.cLetters.length
							]
						);
					} else {
						enT.push(
							this.sLetters[
								(this.sLetters.indexOf(l) + k) % this.sLetters.length
							]
						);
					}
				} else {
					enT.push(l);
				}
      });
			this.text = "";
      this.key = 0;
      this.encrypted = enT.join("")
      this.fileReady = true
      this.activateDlink()
    },
    // creates a text file from encrypted text
    makeTextFile(text){
      let textFile = null
      const data = new Blob([text], {type: 'text/plain'})
      // manualy revoke the object Url to avoid memory leaks
      if(textFile !== null){
        window.URL.revokeObjectURL(textFile)
      }
      textFile = window.URL.createObjectURL(data)
      return textFile
    },
    activateDlink(){
			const link = document.getElementById('dLink')
			let fName = document.getElementById('file').files[0].name
			const fileEndIndex = fName.split('').indexOf('.')
			fName = fName.slice(0,fileEndIndex)
			link.href = this.makeTextFile(this.encrypted)
      link.download = `encrypted_${fName}`

    },
    // Reads the uploaded file and assign its text to the text variable
		readFile() {
			const file = document.getElementById("file").files[0];
			const reader = new FileReader();
			reader.addEventListener("load", (e) => {
				let t = e.target.result;
				console.log(t);
				this.text = t;
			});
			reader.readAsText(file);
		},
	},
};
</script>

<style>
.main {
	margin: 2rem auto;
	border: 2px solid rgb(199, 100, 64);
	width: 90%;
	height: 80%;
	display: flex;
	justify-content: space-evenly;
	align-items: center;
	padding: 2rem;
	color: snow;
}
.left {
	width: 30%;
	display: flex;
	flex-direction: column;
}

.right {
	box-shadow: 3px 2px 10px 1px grey;
	padding: 1rem;
	color: snow;
	text-align: center;
}

.input {
	text-align: center;
	background-color: transparent;
	color: snow;
	padding: 1rem;
	border: none;
	border-bottom: 2px solid rgb(199, 100, 64);
	margin-bottom: 2rem;
}

.main button {
	background-color: rgb(199, 100, 64);
	border: none;
	border-radius: 2rem 1rem;
	color: snow;
	padding: 1rem;
	font-size: 1.5rem;
}

.main button:hover {
	background-color: transparent;
	cursor: pointer;
	border: 2px solid rgb(199, 100, 64);
}
</style>
