<template>
    <div class="text-sm sm:text-lg">
        <button-comp class="flex justify-center items-center">
            <img src="../assets/icons8-google-48.png" class="mr-2" width="20" height="25" alt="">
            {{ pageType == "signUp" ? "Sign Up with Google" : "Sign In with Google"}}
        </button-comp>
        <button-comp class="flex justify-center items-center">
            <i class="fa-brands fa-facebook text-blue-600 mr-2"></i>
            {{ pageType == "signUp" ? "Sign Up with Facebook" : "Sign In with Facebook"}}
        </button-comp>
    </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import ButtonComp from './ButtonComp.vue';

@Options({
    components: {
        ButtonComp
    },
    props: {
        pageType: String
    }
})
export default class LoginBtns extends Vue {
  pageType!: string;
}
</script>
  