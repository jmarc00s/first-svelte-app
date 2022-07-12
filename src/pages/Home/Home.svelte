<script>
  import PageHeading from '../../components/pageHeading.svelte';
  import UserForm from './components/UserForm.svelte';
  import UserTable from './components/UserTable.svelte';

  let users = [];
  let editingUser = false;
  let userToEdit;

  const handleCreateUser = ({ detail: user }) => {
    users = [...users, user];
  };

  const handleEditUser = ({ detail: editedUser }) => {
    const userIndex = users.indexOf(userToEdit);
    users = users.map((user, index) => {
      if (index === userIndex) return editedUser;
      return user;
    });
  };

  const onRemoveUser = ({ detail: user }) => {
    const userIndex = users.indexOf(user);

    users = users.filter((_, i) => {
      return i !== userIndex;
    });
  };

  const onEditUser = ({ detail: user }) => {
    editingUser = true;
    userToEdit = user;
  };
</script>

<section>
  <PageHeading title="Home page" />
  <UserForm
    editing={editingUser}
    {userToEdit}
    on:userCreated={handleCreateUser}
    on:userEdited={handleEditUser}
  />
  <UserTable on:editUser={onEditUser} on:removeUser={onRemoveUser} {users} />
</section>
