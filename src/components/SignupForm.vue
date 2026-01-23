<template>
    <form>
        <label>Email:</label>
        <input type="email" required v-model="email" />
        <label>Password:</label>
        <input type="password" required v-model="password" />

        <label>Role:</label>
        <select v-model="role">
            <option value="developer">Web Developer</option>
            <option value="designer">Web Designer</option>
        </select>

        <label>Skills:</label>
        <input type="text" placeholder="e.g. JavaScript" v-model="tempSkill" @keyup="addSkill" />
        <div v-for="(skill) in skills" :key="skill" class="pill">
            <li>{{ skill }}</li>
        </div>

        <div class="terms">
            <input type="checkbox" required v-model="termsAccepted">
            <label>Accept Terms and Conditions</label>
        </div>

    </form>
    <p>Email: {{ email }}</p>
    <p>Password: {{ password }}</p>
    <p>Role: {{ role }}</p>
    <p>Terms Accepted: {{ termsAccepted }}</p>
</template>

<script>
export default {
    data() {
        return {
            email: '',
            password: '',
            role: '',
            termsAccepted: false,
            tempSkill: '',
            skills: [],
        }
    },
    methods: {
        addSkill(event) {
            if (event.key === 'Enter' && this.tempSkill) {
                if (!this.skills.includes(this.tempSkill)) {
                    this.skills.push(this.tempSkill)
                }
                this.tempSkill = ''
            }
        }
    }

}
</script>

<style>
form {
    max-width: 420px;
    margin: 20px auto;
    background: white;
    text-align: left;
    padding: 40px;
    border-radius: 10px;
}

label {
    display: inline-block;
    margin: 25px 0 15px;
    font-size: 0.6em;
    font-weight: bold;
    text-transform: uppercase;
    letter-spacing: 1px;
    color: #aaa;
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

input[type="checkbox"] {
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0;
    position: relative;
    top: 2px;
}
</style>