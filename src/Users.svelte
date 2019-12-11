<script>
    let users;
    const getUsers = async () => {
        const res = await fetch("https://jsonplaceholder.typicode.com/users");
        const item = await res.json();

        if(res.ok) {
            return item;
        } else {
            throw new Error(item);
        }
    }

    const handleClick = () => {
        users = getUsers();
    }
</script>

<button on:click={handleClick}>Get Users</button>
{#await users}
    <p>...waiting</p>
{:then  data}
    {#if users}
        {#each data as item}
            <div>{item.name}</div>
        {/each}
    {:else}
		<div>-</div>
	{/if}
{:catch error}
    <p>{error}</p>
{/await}