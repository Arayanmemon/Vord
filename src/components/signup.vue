<template>
    <div class="form">
        <label>Email: </label>
        <input type="email" v-model="email">
        <label>Password: </label>
        <input type="password" v-model="pass">
        <span v-if="passerror" class="p">{{passerror}}</span>

        <label>Role: </label>
        <select v-model="role">
            <option value="developer">Web developer</option>
            <option value="designer">Web designer</option>
            <option value="tester">Web tester</option>
        </select>

        <label>Skills:</label>
        <input type="text" v-model="tempSkill" @keydown="addSkill">
        <div class="sk">
            <div v-for="skill in skills" :key="skill" class="pill">
                <span @click="delskill(skill)">{{skill}}</span>
            </div>
        </div>
        <div class="chk">
            <input type="checkbox" v-model="privacy">
            <p>Accept terms and Privacy</p>
        </div>
        <div class="btn">
            <button @click="Submitevent">Submit</button>
        </div>
    </div>
    <p>Email: {{email}}</p>
    <p>Password:  {{pass}}</p>
    <p>Role: {{role}}</p>
    <p>Privacy: {{privacy}}</p>
    <p>Skills: {{skills}}</p>
</template>
<script>
export default {
        data() {
            return {  
                email: '@gmail.com',
                pass: '',
                role: '',
                privacy: false,
                tempSkill: '',
                skills: [],
                passerror: ''
            }
        },
        methods: {
            addSkill(e) {
                console.log(e.key);
                if (this.tempSkill.length > 2 && e.key === 'Enter') {
                    if(this.skills.includes(this.tempSkill)) {
                        return;
                    }
                    else{
                        this.skills.push(this.tempSkill);
                        this.tempSkill = '';
                    }
                }
            },
            delskill(e){
               this.skills = this.skills.filter((skill)=>{
                    return e !== skill;
               })
            },
            Submitevent(){
                this.passerror = this.pass.length > 5 ?
                '': 'password must be greater than 5 characters'

                if(!this.passerror){
                    console.log("Form submitted")
                }
            }
        }
    }
</script>
<style>
body{
    margin: 0;
    padding: 0;
}
.form{
    width: 60vw;
    margin: 0 auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    display: flex;
    flex-direction: column;
    align-items: center;
}
input,select{
    width: 50%;
    padding: 10px;
    margin: 10px 0;
    border: 1px solid #ccc;
    border-radius: 5px;
}
label{
    margin-top: 10px;
    width: 50%;
    text-align: left;
}
.chk{
    display: flex;
    flex-direction: row;
}
input[type="checkbox"]{
    display: block;
    width: 50px;
    margin: 20px;
}
.pill{
    display: inline-block;
    margin: 10px 5px;
    padding: 5px;
    background: #ccc;
    border-radius: 5px;
    cursor: pointer;
}
.sk{
    display: inline;
}
.p{
    font-size: smaller;
    color: red;
}
</style>