<script>
  import { createEventDispatcher } from "svelte";
  import trashicon from "../assets/trash.svg";
  import editicon from "../assets/edit.svg";

  const dispatch = createEventDispatcher();

  export let todoData;
</script>

<div>
  <p>
    {todoData}
  </p>
  <button on:click={() => dispatch("edit")}>
    <img src={editicon} alt="edit icon" />
  </button>
  <button on:click={() => dispatch("delete")} class="btn">
    <img src={trashicon} alt="Delete icon" />
  </button>
</div>

<style>
  div {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
  }
  p {
    font-size: 1rem;
    font-family: sans-serif;
    padding: 0.8rem;
    width: 100%;
    margin-right: 1rem;
    background-color: gainsboro;
    border-radius: 0.2rem;
  }
  button {
    background-color: orangered;
    border: none;
    border-radius: 0.2rem;
    color: white;
    font-size: 1rem;
    padding: 0.7rem 2rem;
    margin-right: 1rem;
  }
  .btn {
    margin-right: 0rem;
  }
</style>
