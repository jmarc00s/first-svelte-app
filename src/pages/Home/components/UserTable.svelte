<script>
  import { createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();
  export let users;

  const handleEditUserClick = (user) => {
    dispatch('editUser', user);
  };

  const handleRemoveUserClick = (user) => {
    dispatch('removeUser', user);
  };
</script>

<div class="table-container">
  <table>
    <thead>
      <tr>
        <th>Nome</th>
        <th>Sobrenome</th>
        <th>Email</th>
        <th>Ações</th>
      </tr>
    </thead>
    <tbody>
      {#each users as user}
        <tr>
          <td>{user.firstName}</td>
          <td>{user.lastName}</td>
          <td>{user.email || '-'}</td>
          <td class="actions-container">
            <button class="edit-button">Editar</button>
            <button class="remove-button">Remover</button>
          </td>
        </tr>
      {/each}
    </tbody>
  </table>
</div>

<style>
  .table-container {
    @apply overflow-auto;
  }

  .actions-container {
    @apply flex gap-4 justify-center;
  }

  button {
    @apply px-4 py-2 shadow rounded text-white;
  }

  .edit-button {
    @apply bg-green-600;
  }

  .remove-button {
    @apply bg-red-600;
  }

  table {
    @apply w-full mt-4 shadow;
  }

  thead th {
    @apply border p-4 bg-white;
  }

  td {
    @apply text-center p-2 border;
  }

  tr {
    @apply bg-white;
  }

  tr:nth-child(2n) {
    @apply bg-gray-200;
  }
</style>
