<script>
  import PageHeading from '../../components/pageHeading.svelte';
  import UserForm from './components/UserForm.svelte';
  import UserTable from './components/UserTable.svelte';

  let users = [];

  const handleCreateUser = ({ detail: user }) => {
    users = [...users, user];
  };
</script>

<section>
  <PageHeading title="Home page" />
  <UserForm on:userCreated={handleCreateUser} />
  <UserTable {users} />
</section>
