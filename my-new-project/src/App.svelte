<script>
  let firstName = "Tien";
  let lastName = "Nguyen";
  $: name = firstName + " " + lastName;
  let color = "blue";
  let showText = false;
  let users = [
    {
      id: 1,
      name: "John",
    },
    {
      id: 2,
      name: "Sara",
    },
    {
      id: 3,
      name: "Tien",
    },
  ];

  const toggle = () => {
    color = color === "blue" ? "red" : "blue";
  };
  const toggleText = () => {
    showText = !showText;
  };
  const addUser = () =>{
	  users = [...users, {id : 4, name : 'Tung'}];
  }
</script>

<main>
  <h1 style="color: {color};">Hello {name}!</h1>
  {#if showText}
    <p>
      Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn
      how to build Svelte apps.
    </p>
  {:else}
    <p>No Text</p>
  {/if}
	{#each users as user (user.id)}
		<h3>{user.id}: {user.name}</h3>
	{/each}
  <button on:click={toggleText}>Show Text</button>
  <button on:click={toggle}>Change Color</button>
  <button on:click={addUser}>Add User</button>
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
