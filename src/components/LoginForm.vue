<template>
    <form @submit.prevent="handleSubmit">
        <div class="flex mb-5">
            <input type="text" class="input mr-3" v-model="firstName" placeholder="First name" required>
            <input type="text" class="input" v-model="lastName" placeholder="Last name" required>
        </div>

        <div class="mb-5">
            <input type="email" :class="{ 'focus:outline-red-600': emailError, 'outline-red-600': emailError }" class="input" v-model="email" @input="validateEmail" placeholder="Email address" required>
            <p v-if="emailError" class="text-red-500">{{ errMsg }}</p>
        </div>

        <div class="mb-5">
            <div class="flex">
                <div class="flex mr-3 w-full">
                    <input :type="passwordType" :class="{ 'focus:outline-red-600': passwordError, 'outline-red-600': passwordError }" class="input" v-model="password" @input="validatePassword" placeholder="Enter Password" required>
                    <i class="fa-regular icon text-gray-400 cursor-pointer" :class="{'fa-eye-slash': showEye, 'fa-eye': !showEye}" id="togglePassword" @click="toggleVisibility"></i>
                </div>
                <input type="password" :class="{ 'focus:outline-red-600': passwordError, 'outline-red-600': passwordError }" class="input" v-model="confirmPassword" @input="validateConfirmPassword" placeholder="Confirm Password" required>
            </div>
            <p v-if="passwordError" class="text-red-500">! {{ errMessage }}</p>
        </div>

        <button-comp class="bg-gray-600 text-white">Create Account</button-comp>
    </form>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import ButtonComp from './ButtonComp.vue';

@Options({
    components: {
        ButtonComp
    },
})
export default class LoginForm extends Vue {
    firstName = '';
    lastName = '';
    email = '';
    password = '';
    confirmPassword = '';
    mailformat = /^\w+([.-]?\w+)*@\w+([.-]?\w+)*(\.\w{2,3})+$/
    //To check a password between 6 to 20 characters which contain at least one numeric digit, one uppercase and one lowercase letter
    regPassword = /^(?=.*\d)(?=.*[a-z])(?=.*[A-Z]).{6,20}$/
    emailError = false
    errMsg = ''
    passwordError = false
    errMessage = ''
    passwordType = 'password'

    toggleVisibility() {
        if (this.showEye) this.passwordType = "text";
        else this.passwordType = "password";
    }
    get showEye() {
        return this.passwordType == "password";
    }

    validateEmail() {
        if (this.mailformat.test(this.email)) {
            this.emailError = false
        }else{
            this.emailError = true
            this.errMsg = 'Please input valid Email address'
        }
    }
    validatePassword() {
        if (this.regPassword.test(this.password)) {
            this.passwordError = false
        }else{
            this.passwordError = true
            this.errMessage = "Password should be at least 6 characters long, contain at least one uppercase & one digit"
        }
    }

    validateConfirmPassword(){
        if(this.password !== this.confirmPassword){
            this.passwordError = true
            this.errMessage = "Passwords don't match"
        }else{
            this.passwordError = false
        }
    }

    resetForm() {
        this.email = '' 
        this.password = ''
        this.confirmPassword = ''
        this.firstName = ''
        this.lastName = ''
    }

    handleSubmit(){
        if(this.firstName != "" && this.lastName != "" && this.email != "" && !this.passwordError && !this.emailError && this.password != '' && this.confirmPassword != '') {
            alert('Form submitted successfully')
            this.resetForm()
        }else if(this.passwordError || this.emailError){
            alert('Please enter valid details')
        }else{
            alert('Please fill out all fields')
        }
    }
}
</script>


<style scoped>
.icon{
    margin-left: -30px; 
    margin-top: 15px;
}
</style>