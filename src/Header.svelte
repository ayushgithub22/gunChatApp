<script>
  import { username, user } from './user';

  function signout() {
    user.leave();
    username.set('');
  }
</script>

<header>
<h1 id="headerIcon">#</h1>
  {#if $username}
    <div class="user-bio">
      
      <span>Signed in as <strong>{$username}</strong></span>
      <!-- <img src={`https://source.unsplash.com/400x400/?blackavatar`} alt="avatar" />  -->
    </div>

    <button class="signout-button" on:click={signout}>Sign Out</button>

    {:else}

      <h3>D-Chat App</h3>
  {/if}
</header>