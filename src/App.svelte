<script>
	import { afterUpdate, beforeUpdate, onMount } from 'svelte';
	const EMAIL_REGEXP = /^(([^<>()[\].,;:\s@"]+(\.[^<>()[\].,;:\s@"]+)*)|(".+"))@(([^<>()[\].,;:\s@"]+\.)+[^<>()[\].,;:\s@"]{2,})$/iu;

	let email;
	let username;
	let password;
	let repeatThePassword;
	
	let errorMessage;
	
	const checkEqualityPassword = () => password === repeatThePassword && password && repeatThePassword
	


	const isEmailValid = () => {
		return EMAIL_REGEXP.test(email)
	}

	

	let emailElement;
	let usernameElement;
	let passwordElement;
	let repeatPasswordElement;
	

	

	const register = (event) => {
		event.preventDefault()

		let isValidationPassed = false;

		if (isEmailValid()) {
			emailElement.style.borderColor = "green"
			isValidationPassed = true
		} else {
			emailElement.style.borderColor = "red"
			isValidationPassed = false
		}
		
		if (checkEqualityPassword()) {
			passwordElement.style.borderColor = "green"
			repeatPasswordElement.style.borderColor = "green"
			isValidationPassed = true
		} else {
			passwordElement.style.borderColor = "red"
			repeatPasswordElement.style.borderColor = "red"
			isValidationPassed = false
		}

		if (username) {
			usernameElement.style.borderColor = "green"
			isValidationPassed = true
		} else {
			usernameElement.style.borderColor = "red"
			isValidationPassed = false
		}

		console.log(isValidationPassed)

	}
	

</script>

<div class="container">
	<form action="" class="input-form">
		<input bind:this={emailElement} bind:value={email}  class="input-register" type="text" placeholder="E-mail" />
		<input bind:this={usernameElement} bind:value={username} class="input-register" type="text" placeholder="Username" />
		<input bind:this={passwordElement} bind:value={password} class="input-register" type="password" placeholder="Password" />
		<input bind:this={repeatPasswordElement} bind:value={repeatThePassword} class="input-register" type="password" placeholder="Repeat the password" />
		<button on:click={register} type="submit">Register</button>
		<p></p>
	</form>
</div>

<style>
	.container {
		min-width: 30%;
  		margin: 0 auto;
		/* width: 50vw;
  		height: 50vh; */
  		background: red;
		background-color: white;
		border-radius: 20px
	}

	.input-register {
        margin-top: 10px;
        border-radius: 50px;
        background: #e6e6e6;
        color: #666;
		outline: none;
    }

	.input-form {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

	:global(body) {
  		display: flex;
  		justify-content: center;
  		align-items: center;
  		height: 100%;
	}

	button {
		margin-top: 20px;
		background: #57b846;
		border-radius: 50px;
		width: 200px;
		height: 40px;
		color: #fff;
		text-transform: uppercase;
		font-family: Arial, Helvetica, sans-serif;
		font-size: 15px;
		font-weight: 700;
	}
</style>