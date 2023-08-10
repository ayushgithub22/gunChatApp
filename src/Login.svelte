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
        var pass1 = document.getElementById("pass1").value
        var pass2 = document.getElementById("pass2").value
        if(pass1 === pass2){
          // Perform signup logic with name input
          user.create(username, password, ({ err }) => {
            if (err) {
              alert(err);
            } else {
              login();
            }
          });
        }
        else{alert("Wrong Password!")}
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
  <div>
    <h1><span class="apkName">#HASH</span><br>Privacy Like Never Before</h1>
    <ul>
      <li>⭕ Welcome to Hash!</li>
      <li>⭕ Here we like to protext your privacy by not storing the data anywhere but your own device.</li>
      <li>⭕ Make sure you don't Mis-Use this App!</li>
      <li>⭕ Have fun, freely!</li>
    </ul>
  </div>
  
  <div  class="loginClass">

    {#if showNameInput}
      <label for="name">Name</label>
      <input name="name" placeholder="Enter your name" />
    {/if}
    
      <label for="username">Username</label>
      <input name="username" bind:value={username} minlength="3" maxlength="16" placeholder="Enter your username" />
      <label for="password">Password</label>
      <input id="pass1" name="password" bind:value={password} type="password" placeholder="Enter your password" />

      <!-- newcode -->
      {#if showNameInput}
        <label for="name">Name</label>
        <input id="pass2" type="password" name="name" placeholder="Confirm your password" />
      {/if}

      {#if !showNameInput}
        <button class="login" on:click={login}>Login</button><br>
      {/if}


      <!-- <button class="login" on:click={login}>Login</button><br> -->
      <button class="signup"  on:click={signup}>Sign Up</button>
      <!-- <button class="signup"  on:click={() => signupPage('Signup.html')}>Sign Up</button> -->
  </div>
</div>