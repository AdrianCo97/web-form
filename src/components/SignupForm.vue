<template>
  <form>
    <label>Email:</label>
    <input type="email" required v-model="email" />

    <label>Password:</label>
    <input type="password" required v-model="password" />

    <label>Role: </label>
    <select v-model="role">
      <option value="developer">Developer</option>
      <option value="designer">Designer</option>
    </select>

    <label>Skills:</label>
    <input type="text" v-model="tempSkill" v-on:keyup.enter="addSkill" />

    <div class="skills">
      <div v-for="skill in skills">
        <p class="skill">{{ skill }}</p>
      </div>
    </div>

    <div class="terms">
      <input type="checkbox" required v-model="terms" />
      <label>Accept terms and Conditions</label>
    </div>
  </form>

  <p>Email: {{ email }}</p>
  <p>Password: {{ password }}</p>
  <p>Role: {{ role }}</p>
  <p>Terms: {{ terms }}</p>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      role: "",
      tempSkill: "",
      skills: [],
      terms: false,
    };
  },
  methods: {
    addSkill() {
      if (this.tempSkill) {
        const skillWithoutCapitalLetters = this.tempSkill.toLowerCase();
        if (!this.skills.includes(skillWithoutCapitalLetters)) {
          this.skills.push(skillWithoutCapitalLetters);
        }
        this.tempSkill = "";
      }
    },
  },
};
</script>

<style>
form {
  max-width: 420px;
  margin: 30px auto;
  background: white;
  text-align: left;
  padding: 40px;
  border-radius: 10px;
}
label {
  color: #aaa;
  display: inline-block;
  margin: 25px 0 15px;
  font-size: 0.6em;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}
input,
select {
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid #ddd;
  color: #555;
}
.skills{
    display: flex;
    flex-wrap: wrap;
}
.skill {
  background-color: rgb(182, 216, 224);
  width: fit-content;
  padding: 10px;
  margin: 10px 10px 0 0;
  border-radius: 4px;
}
input[type="checkbox"] {
  display: inline-block;
  width: 16px;
  margin: 0 10px 0 0;
  position: relative;
  top: 2px;
}
</style>
