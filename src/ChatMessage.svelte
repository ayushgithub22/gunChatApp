<script>
  export let message;
  export let sender;

  const messageClass = message.who === sender ? 'sent' : 'received';

  const avatar = `https://source.unsplash.com/400x400/?${message.who},avatar`;

  const ts = new Date(message.when);

  //Time set too dissapear message
  setTimeout(() => {
    const messageElements = document.querySelectorAll('.message');
    messageElements.forEach((element) => {
      element.remove();
    });
  }, 60000);

</script>

<div class={`message ${messageClass}`}>
  <img src={avatar} alt="avatar" />
  <div class="message-text">
    <p>{message.what}</p>

    <time>{ts.toLocaleTimeString()}</time>
  </div>
</div>
