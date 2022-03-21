<script>
    async function handleSubmit(data) {
      try {
        await fetch('https://formspree.io/f/xayapqvr', {
          method: 'POST', // *GET, POST, PUT, DELETE, etc.
          mode: 'cors', // no-cors, *cors, same-origin
          cache: 'no-cache', // *default, no-cache, reload, force-cache, only-if-cached
          credentials: 'same-origin', // include, *same-origin, omit
          headers: {
            'Content-Type': 'application/json'
            // 'Content-Type': 'application/x-www-form-urlencoded',
          },
          redirect: 'follow', // manual, *follow, error
          referrerPolicy: 'no-referrer', // no-referrer, *no-referrer-when-downgrade, origin, origin-when-cross-origin, same-origin, strict-origin, strict-origin-when-cross-origin, unsafe-url
          body: JSON.stringify({
            name,
            email,
            message
          }) // body data type must match "Content-Type" header
        });
        // await Promise.resolve();
        alert('thanks for reaching out! We will contact you as soon as possible.')
      } catch (error) {
        console.error(error);
      }
    }

    let name;
    let email;
    let message;
  </script>

  <style>

  </style>

  <div>
      <p>Contacts page</p>
            <form class="column" on:submit|preventDefault={handleSubmit}>
              FORM
            </form>
  </div>
