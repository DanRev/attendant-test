<script>
  let persons = [];
  let value = "";
  
  const addPerson = () => {
    if (!value) {
      alert("Please enter a name");
      return;
    }

    persons = [...persons, value];
    value = "";
  };

  const attendPerson = () => {
    if (persons.length === 0) {
      alert("No one to attend");
      return;
    }

    persons = persons.slice(1);
  };
</script>

<main>
  <div class="container">
    <div class="box">
      <input type="text" bind:value />
      <button class="btn btn-add" on:click={addPerson}>Add</button>
    </div>
    <div class="box">
      {#if persons.length === 0}
        <p>No one to attend</p>
      {:else}
        <ul>
          {#each persons as person}
            <li>{person}</li>
          {/each}
        </ul>
      {/if}
    </div>
    <div class="box">
      <button class="btn btn-attend" on:click={attendPerson}>Attend</button>
    </div>
  </div>
</main>

<style>
  .container {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
  }

  .box {
    padding: 10px;
    border: 3px solid rgb(0, 0, 0);
    margin: 10px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    height: 300px;
  }

  .box input {
    margin-bottom: 10px;
  }

  ul {
    padding: 0;
  }

  .box li {
    list-style: none;
    text-align: center;
  }

  .btn {
    color: white;
    border: none;
    padding: 10px 20px;
    border-radius: 5px;
  }

  .btn-add {
    background-color: rgb(19, 185, 19);
  }

  .btn-attend {
    background-color: rgb(11, 107, 233);
  }
</style>
