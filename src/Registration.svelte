<script>
	const EMAIL_REGEXP =
		/^(([^<>()[\].,;:\s@"]+(\.[^<>()[\].,;:\s@"]+)*)|(".+"))@(([^<>()[\].,;:\s@"]+\.)+[^<>()[\].,;:\s@"]{2,})$/iu;

	let email;
	let username;
	let password;
	let repeatThePassword;
	let messageForUser = "";

	const checkEqualityPassword = () =>
		password === repeatThePassword && password && repeatThePassword;

	const checkEmailValid = () => EMAIL_REGEXP.test(email);

	const changeStyleValidation = (validationResult, element) => {
		if (validationResult) {
			element.style.borderColor = "green";
		} else {
			element.style.borderColor = "red";
		}
	};

	let emailElement;
	let usernameElement;
	let passwordElement;
	let repeatPasswordElement;

	let messageForUserElement;

	const register = (event) => {
		event.preventDefault();

		const isEmailValid = checkEmailValid();
		const isUsernameValid = !!username;
		const isPasswordValid = checkEqualityPassword();

		changeStyleValidation(isEmailValid, emailElement);
		changeStyleValidation(isPasswordValid, passwordElement);
		changeStyleValidation(isPasswordValid, repeatPasswordElement);
		changeStyleValidation(isUsernameValid, usernameElement);

		if (isEmailValid && isUsernameValid && isPasswordValid) {
			messageForUser = "Congratulations on completing the registration!";
			messageForUserElement.style.color = "green";
		} else {
			messageForUser = "Check the correctness of the entered data!";
			messageForUserElement.style.color = "red";
		}
	};
</script>

<div class="container">
	<form action="" class="input-form">
		<input
			bind:this={emailElement}
			bind:value={email}
			class="input-register"
			type="text"
			placeholder="E-mail"
		/>
		<input
			bind:this={usernameElement}
			bind:value={username}
			class="input-register"
			type="text"
			placeholder="Username"
		/>
		<input
			bind:this={passwordElement}
			bind:value={password}
			class="input-register"
			type="password"
			placeholder="Password"
		/>
		<input
			bind:this={repeatPasswordElement}
			bind:value={repeatThePassword}
			class="input-register"
			type="password"
			placeholder="Repeat the password"
		/>
		<button on:click={register} type="submit">Register</button>
		<p bind:this={messageForUserElement} class="form-message">
			{messageForUser}
		</p>
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
		border-radius: 20px;
		text-align: center;
	}

	.input-register {
		margin-top: 10px;
		border-radius: 50px;
		background: #e6e6e6;
		color: #666;
		outline: none;
		border-width: medium;
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

	.form-message {
		color: green;
		font-weight: 700;
	}
</style>
