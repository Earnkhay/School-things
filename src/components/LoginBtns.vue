<template>
    <div>
        <button-comp>{{ pageType == "signUp" ? "Sign Up with Google" : "Sign In with Google"}}</button-comp>
        <button-comp>{{ pageType == "signUp" ? "Sign Up with Facebook" : "Sign In with Facebook"}}</button-comp>
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
  