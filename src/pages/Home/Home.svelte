<script>
  import PageHeading from '../../components/pageHeading.svelte';
  import UserForm from './components/UserForm.svelte';

  let users = [];

  const handleCreateUser = ({ detail: user }) => {
    users = [...users, user];
  };
</script>

<section>
  <PageHeading title="Home page" />
  <UserForm on:userCreated={handleCreateUser} />
</section>

<style></style>
