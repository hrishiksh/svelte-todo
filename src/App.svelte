<script>
  import logo from "./assets/svelte.png";
  import Element from "./lib/Element.svelte";

  let todo;
  let todos = [];
  function addTodoBtn() {
    todos = [...todos, { todo, id: Date.now() }];
    todo = "";
  }

  function deleteTodoBtn(id) {
    todos = todos.filter((t) => t.id !== id);
  }

  function editTodoBtn(id) {
    let [todoElement] = todos.filter((t) => t.id === id);
    todo = todoElement.todo;
    todos = todos.filter((t) => t.id !== id);
  }
</script>

<svelte:head>
  <title>Todo app</title>
</svelte:head>
<header>
  <img src={logo} alt="Svelte logo" />
</header>
<main>
  <div>
    <input type="text" bind:value={todo} />
    <button on:click={addTodoBtn}> Add </button>
  </div>
  <section>
    {#each todos as t (t.id)}
      <Element
        todoData={t.todo}
        on:delete={() => deleteTodoBtn(t.id)}
        on:edit={() => editTodoBtn(t.id)}
      />
    {/each}
  </section>
</main>

<style>
  header {
    display: flex;
    justify-content: center;
  }
  header > img {
    width: 3rem;
    margin: 1rem;
  }
  main {
    width: 30%;
    margin: auto;
  }
  div {
    display: flex;
    justify-content: center;
    margin: 2rem 0rem;
  }
  input {
    padding: 0.5rem 0.7rem;
    width: 100%;
    margin-right: 1rem;
    font-size: 1rem;
  }
  button {
    background-color: orangered;
    border: none;
    border-radius: 0.2rem;
    color: white;
    font-size: 1rem;
    padding: 0 2rem;
  }
</style>
