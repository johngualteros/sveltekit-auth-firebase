<script>
    import { user,isLoggedIn } from "../stores";
    console.log(user);
</script>
<div class="bg-blue-700 px-10 py-10 flex flex-col items-center gap-y-4">
  <h1 class="text-4xl font-extrabold">Profile</h1>

  {#if $isLoggedIn}
    <img
      src="{$user.photoURL}"
      alt={$user.displayName}
      class="w-40 h-40 rounded-full m-auto"
    />
    <h3>{$user.displayName}</h3>
    <p>{$user.email}</p>
  {/if}
</div>