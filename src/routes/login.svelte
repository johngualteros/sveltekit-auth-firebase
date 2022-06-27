<script>
    import {auth} from '../firebase';
    import { GoogleAuthProvider,signInWithPopup } from "firebase/auth";
    import { isLoggedIn,user } from "../stores";
    import { goto } from "$app/navigation";
    const login=async()=>{
        try {
            const provider = new GoogleAuthProvider();
            const res =await signInWithPopup(auth,provider);
            $user=res.user;
            $isLoggedIn=true;
            goto("/profile");
        } catch (error) {
            console.error(error)
        }
    }
</script>
<div>
    <button on:click={login} class="bg-blue-600 text-white font-bold px-6 py-3 rounded-md shadow-lg hover:bg-blue-800">Login with Google</button>
</div>
<style>

</style>