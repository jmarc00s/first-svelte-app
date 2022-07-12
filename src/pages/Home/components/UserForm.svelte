<script>
  import { createEventDispatcher } from 'svelte';

  export let editing;
  export let userToEdit;

  const dispatch = createEventDispatcher();

  $: if (editing) {
    user = userToEdit;
  }

  $: formIsValid = user.firstName && user.lastName;

  let user = {
    firstName: '',
    lastName: '',
    email: '',
  };

  const handleCreateUserClick = () => {
    if (editing) dispatch('userEdited', user);
    if (!editing) dispatch('userCreated', user);

    clearUserForm();
  };

  const clearUserForm = () => {
    user = {
      firstName: '',
      lastName: '',
      email: '',
    };
  };
</script>

<div class="container">
  <div class="input-container">
    <label for="user">Nome</label>
    <input
      type="text"
      name="user"
      id="user"
      bind:value={user.firstName}
      placeholder="Nome"
    />
  </div>
  <div class="input-container">
    <label for="lastName">Sobrenome</label>
    <input
      type="text"
      name="lastName"
      id="lastName"
      bind:value={user.lastName}
      placeholder="Sobrenome"
    />
  </div>
  <div class="input-container">
    <label for="email">Email</label>
    <input
      type="email"
      name="email"
      id="email"
      bind:value={user.email}
      placeholder="Email"
    />
  </div>
  <button disabled={!formIsValid} on:click={handleCreateUserClick}
    >Create user</button
  >
</div>

<style>
  .container {
    @apply flex flex-col justify-center items-center w-1/3 mx-auto;
  }

  .input-container {
    @apply w-full;
  }

  input {
    @apply p-3 my-3 bg-white w-full;
  }

  button {
    @apply bg-blue-500 py-2 px-4 text-white text-center rounded shadow w-full;
  }

  button:disabled {
    @apply bg-gray-300 cursor-not-allowed;
  }
</style>
