<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
  </div>
  <body>
    <div class="btnToCopy">
      <p></p>
      <button>Copy to Clipboard</button>
      <p class="success-copy">
        Password was succesfully copied to your clipboard!
      </p>
    </div>
    <div class="pre-condition-navigation">
      <div class="btn-low">
        <input
          checked
          v-model="characterInclLowerCase"
          type="checkbox"
          class="box-lower"
          id="box-designed"
        />
        <label for="box-designed" class="designed-box">Lowercase</label>
      </div>
      <div class="btn-up">
        <input
          checked
          v-model="characterInclUpperCase"
          type="checkbox"
          class="box-upper"
          id="box-designed"
        />
        <label for="box-designed" class="designed-box">Uppercase</label>
      </div>
      <div class="btn-numb">
        <input
          checked
          v-model="characterInclNumber"
          type="checkbox"
          class="box-number"
          id="box-designed"
        />
        <label for="box-designed" class="designed-box">Number</label>
      </div>
      <div class="btn-spec">
        <input
          checked
          v-model="characterInclSpecific"
          type="checkbox"
          class="box-specific"
          id="box-designed"
        />
        <label for="box-designed" class="designed-box">Specific</label>
      </div>
    </div>
    <div>
      <label for="myRange" class="password-length">Password Length:</label>
      <br />
      <input
        class="regulator-password-length"
        type="range"
        min="8"
        max="35"
        v-model="value"
        id="myRange"
        step="1"
        @input="generatePassword()"
      />

      <label class="length-of-password" for="myRange">{{
        lengthpassword
      }}</label>
    </div>
  </body>
</template>

<script>
export default {
  name: "PasswordGenerator",
  data() {
    return {
      lengthpassword: 8,
      characterInclLowerCase: true,
      characterInclUpperCase: false,
      characterInclNumber: false,
      characterInclSpecific: false,
    };
  },
  methods: {
    generatePassword() {
      if (!this.lengthpassword) return;
      this.triggerLoading(true);
      let password = "";
      let characters = "abcdefghijklmnopqrstuvwxyz";
      if (this.characterInclUpperCase)
        characters += "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
      if (this.characterInclNumber) characters += "0123456789";
      if (this.characterInclSpecific)
        characters += "!\"#$%&'()*+,-./:;<=>?@[\\]^_`{|}~";
      for (let i = 0; i < this.lengthpassword; i++) {
        password += characters.charAt(
          Math.floor(Math.random() * characters.length)
        );
      }
      this.generatedPassword = password;
      this.triggerLoading(false);
    },
    triggerLoading(state) {
      this.isLoading = state;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Arvo&display=swap");

html {
  font-family: "Arvo", serif;
}
body {
  display: flex;
  justify-content: center;
  flex-direction: column;
}

.btnToCopy {
  width: 50%;
}
button::before {
  content: "📓";
}

button {
  color: #0f0a0a;
  background-color: #2292a4;
  border-radius: 0.25rem;
  border-style: none;
  margin: 1rem;
}
.success-copy {
  color: #0f0a0a;
  background-color: #cbe896;
  padding: 0.25rem;
  border-radius: 0.25rem;
}
h1 {
  color: #f5efed;
  margin: 2rem;
}
.pre-condition-navigation {
  display: grid;
  width: 40vw;
  height: 14vh;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: 1fr 1fr;
  grid-template-areas:
    "btn-1 btn-2"
    "btn-3 btn-4";
}
@media screen and (min-width: 800px) {
  .pre-condition-navigation {
    grid-template-columns: 1fr 1fr 1fr 1fr;
    grid-template-rows: 1fr;
    grid-template-areas: "btn-1 btn-2 btn-3 btn-4";
    gap: 2rem;
  }
}
.btn-low {
  grid-area: btn-1;
}
.btn-up {
  grid-area: btn-2;
}
.btn-numb {
  grid-area: btn-3;
}
.btn-spec {
  grid-area: btn-4;
}

/*{
  width: 50%;
  padding-top: 5rem;
  margin: auto;
  display: flex;
  justify-content: space-around;
  gap: 2rem;
}*/
input {
  all: unset;
}
.designed-box {
  padding: 0.25rem;
  color: #2292a4;
  border: 0.15rem solid #2292a4;
  background-color: #0f0a0a;
  border-radius: 0.2rem;
}
input[type="checkbox"]:checked + .designed-box {
  background-color: #2292a4;
  color: #f5efed;
  border: 0.15rem solid #2292a4;
}

.box-upper:focus + .designed-box {
  background-color: #2292a4;
  color: #f5efed;
  border: 0.15rem solid #2292a4;
}
.box-number:checked + .designed-box {
  background-color: #2292a4;
  color: #f5efed;
  border: 0.15rem solid #2292a4;
}
.box-specific:checked + .designed-box {
  background-color: #2292a4;
  color: #f5efed;
  border: 0.15rem solid #2292a4;
}

.box-lowercase:focus + .designed-box {
  border: 0.2rem solid #2292a4;
}
.password-length {
  color: #f5efed;
  padding-bottom: 2rem;
  border-style: none;
}

.regulator-password-length {
  -webkit-appearance: none;
  appearance: none;
  width: 30vw;
  background-color: #f5efed;
  height: 0.5rem;
  border-radius: 0.5rem;
}
.regulator-password-length::-webkit-slider-thumb {
  -webkit-appearance: none;
  appearance: none;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background: red;
  cursor: pointer;
}

.regulator-password-length::-moz-range-thumb {
  width: 25px;
  height: 25px;
  background: #04aa6d;
  cursor: pointer;
}

.length-of-password {
  border-style: none;
  color: f5efed;
}
</style>
