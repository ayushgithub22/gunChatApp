<script>
  import { user } from './user';

  let username;
  let password;

  function login() {
    user.auth(username, password, ({ err }) => err && alert(err));
  }

  // function signup() {
  //   user.create(username, password, ({ err }) => {
  //     if (err) {
  //       alert(err);
  //     } else {
  //       login();
  //     }
  //   });
  // }

  // new function
  let showNameInput = false;

  function signup() {
  if (showNameInput) {
    // Perform signup logic with name input
    user.create(username, password, ({ err }) => {
      if (err) {
        alert(err);
      } else {
        login();
      }
    });
  } else {
    // Show name input box
    showNameInput = true;
  }
}


  function signupPage(pageURL) {
    window.location.href = pageURL;
  }
</script>

<div class="loginMain">
  <h1><span class="apkName">#HASH</span><br>Privacy Like Never Before</h1>
  
  <div  class="loginClass">

    {#if showNameInput}
      <label for="name">Name</label>
      <input name="name" placeholder="Enter your name" />
    {/if}
    
      <label for="username">Username</label>
      <input name="username" bind:value={username} minlength="3" maxlength="16" placeholder="Enter your username" />
      <label for="password">Password</label>
      <input name="password" bind:value={password} type="password" placeholder="Enter your password" />

      <!-- newcode -->
      {#if showNameInput}
        <label for="name">Name</label>
        <input type="password" name="name" placeholder="Confirm your password" />
      {/if}

      {#if !showNameInput}
        <button class="login" on:click={login}>Login</button><br>
      {/if}


      <!-- <button class="login" on:click={login}>Login</button><br> -->
      <button class="signup"  on:click={signup}>Sign Up</button>
      <!-- <button class="signup"  on:click={() => signupPage('Signup.html')}>Sign Up</button> -->
  </div>
</div>