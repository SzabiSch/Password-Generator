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
        <input type="checkbox" id="box-designed" />
        <label for="box-designed" class="designed-box">Lowercase</label>
      </div>
      <div class="btn-up">
        <input type="checkbox" id="box-designed" />
        <label for="box-designed" class="designed-box">Uppercase</label>
      </div>
      <div class="btn-numb">
        <input type="checkbox" id="box-designed" />
        <label for="box-designed" class="designed-box">Number</label>
      </div>
      <div class="btn-spec">
        <input type="checkbox" id="box-designed" />
        <label for="box-designed" class="designed-box">Specific</label>
      </div>
    </div>
    <div>
      <p>Password Length:</p>
      <input
        class="regulator-password-length"
        type="range"
        min="8"
        max="35"
        value="8"
      />
    </div>
  </body>
</template>

<script>
export default {
  name: "PasswordGenerator",
  props: {
    msg: String,
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
  width: 50vw;
  height: 30vh;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: 1fr 1fr;
  grid-template-areas:
    "btn-1 btn-2"
    "btn-3 btn-4";
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
label {
  padding: 0.25rem;
  color: #2292a4;
  border: 0.15rem solid #2292a4;
  background-color: #0f0a0a;
  border-radius: 0.2rem;
}

input:checked + label {
  background-color: #2292a4;
  color: #f5efed;
  border: 0.15rem solid #2292a4;
}

input:focus:unchecked + label {
  border: 0.2rem solid navy;
}
</style>
