<script>
  import { auth, db } from '../firebase'
  import { onAuthStateChanged } from 'firebase/auth'
  import LoginForm from '$lib/components/page/LoginForm.svelte'
  import Admin from '$lib/components/page/Admin.svelte'

  let isUser;
 
  auth.onAuthStateChanged((user) => {
		if (user) {
			isUser = true;
		} else {
			isUser = false;
		}
	});

</script>


{#if !isUser}
  <LoginForm />
{:else if isUser}
  <Admin />
{/if}
