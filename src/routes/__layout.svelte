<script>
    
    import "../app.css";
    import {signOut,onAuthStateChanged} from 'firebase/auth';
    import {auth} from '../firebase';
    import { isLoggedIn,user } from "../stores";
    const logout = async()=>{
        try {
            await signOut(auth);
            $isLoggedIn=false;
            $user={};
        } catch (error) {
            console.log
        }
    };
    onAuthStateChanged(auth,authUser=>{
        $user=authUser;
        $isLoggedIn=!!authUser;
    });
</script>
<nav class="w-full bg-blue-900 text-white p-3 text-lg z-10 h-[calc(100vh-92vh)]">
    <a href="/" class="mr-6 fw-bold hover:text-blue-400">Home</a>
    {#if $isLoggedIn}
    <a href="/profile" class="mr-6 fw-bold hover:text-blue-400">Profile</a>
    <a href="/#" on:click={logout} class="mr-6 fw-bold hover:text-blue-400">Logout</a>
    {:else}
    <a href="/login" class="mr-6 fw-bold hover:text-blue-400">Login</a>
    {/if}
</nav>
<main class="h-[calc(100vh-8vh)] w-full bg-stone-900 text-white  flex justify-center items-center">
        <div class="text-center">
            <slot/>
        </div>
</main>

<style>

</style>