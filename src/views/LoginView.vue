<template>
    <div class="p-3 sm:p-7">
        <div class="flex justify-center items-center xl:items-start flex-wrap lg:flex-nowrap">
            <div class="flex-auto px-3">
                <img src="../assets/st-logo.png" alt="">
                <div class="mb-6">
                    <p class="text-lg sm:text-2xl mb-2 leading-relaxed">Bringing you <b class="text-xl sm:text-3xl">Prompt</b> and 
                        <br>
                        <b class="text-xl sm:text-3xl">Accurate</b> updates at all times.</p>
                    <p>{{ pageType == "signUp" ? "Sign Up to get started!" : "Sign In."}}</p>
                </div>

                <login-btns :pageType="pageType"/>

                <div class="flex items-center mb-5">
                    <div class="flex-1 h-px bg-gray-600"></div>
                    <div class="mx-4 text-gray-700">or</div>
                    <div class="flex-1 h-px bg-gray-600"></div>
                </div>

                <div>
                    <login-form/>

                    <p id="account" class="text-center mb-2"> {{pageType == "signUp" ? "Already have an account?" : "Don't have an account?"}} 
                        <a class="font-bold cursor-pointer" @click.prevent="setLoginPage"> {{ pageType == "signUp" ? "LOG IN" : "SIGN UP" }}</a>
                    </p>
                </div>
            </div>
            <div class="flex-initial p-4 hidden sm:block">
                <img class=".img" src="../assets/login-img.png" alt="">
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import ButtonComp from '@/components/ButtonComp.vue';
import LoginForm from '@/components/LoginForm.vue';
import LoginBtns from '@/components/LoginBtns.vue';

@Options({
    components: {
        ButtonComp,
        LoginForm,
        LoginBtns
    },
})
export default class LoginView extends Vue {
    pageType = 'signUp'

    setLoginPage(){     
        this.pageType = this.pageType === "signUp" ? "login" : "signUp";
    }
}
</script>
  