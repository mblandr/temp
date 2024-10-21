<script lang="ts">
	import "~a/global.css";
	import typia, { tags } from "typia";

	const formState = $state({
		name: "",
		email: "",
		comment: "",
	});

	type IValidState = {
		name: string & tags.MinLength<5> & tags.MaxLength<20>;
		email: string & tags.Format<"email">;
		comment: string & tags.MinLength<20>;
	};

	const formInvalid = $state(false);

	const clickHandler = (e: Event) => {
		e.preventDefault();
		const { success, errors } = typia.validate<IValidState>(formState);
		console.log({ success, errors });
	};


	
</script>

<p>SvelteKit</p>
<button onclick={clickHandler}>sample</button>
