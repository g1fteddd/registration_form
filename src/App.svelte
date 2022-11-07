<script>
	import Input from "./Input.svelte";



</script>

<div class="container">
	<form action="" class="input-form">
		<Input placeholder="E-mail" type="email"/>
		<Input placeholder="Username"/>
		<Input placeholder="Password" type="password"/>
		<Input placeholder="Repeat the password" type="password"/>
		<button type="submit">Register</button>
	</form>
</div>

<style>
	.container {
		/* width: 50%;
  		margin: 0 auto; */
		width: 50vw;
  		height: 50vh;
  		background: red;
		background-color: white;
		border-radius: 20px
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