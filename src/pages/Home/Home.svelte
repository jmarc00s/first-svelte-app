<script>
  import PageHeading from '../../components/pageHeading.svelte';
  import UserForm from './components/UserForm.svelte';
  import UserTable from './components/UserTable.svelte';

  let users = [];

  const handleCreateUser = ({ detail: user }) => {
    users = [...users, user];
  };

  const onRemoveUser = ({ detail: user }) => {
    const userIndex = users.indexOf(user);

    users = users.filter((_, i) => {
      return i !== userIndex;
    });
  };
</script>

<section>
  <PageHeading title="Home page" />
  <UserForm on:userCreated={handleCreateUser} />
  <UserTable on:removeUser={(user) => onRemoveUser(user)} {users} />
</section>
