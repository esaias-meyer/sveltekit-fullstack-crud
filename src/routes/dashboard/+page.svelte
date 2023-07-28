<script>
    let toDoList = ["Get groceries!"]
    let currToDo = "";
    let error = false;

    function addToDo() {
        error = false;
        if (!currToDo) {
            error = true;
        }       
        toDoList = [...toDoList, currToDo];
        currToDo = "";
    }
</script>
<div class="mainContainer">   
        <div class="headerContainer">
            <h1>Todo List</h1>
            <button><i class="fa-regular fa-floppy-disk"></i>
                    <p>Save</p></button
            >
        </div>
    <main>
        {#each toDoList as todo, index}
            <div class="todo">
                {index + 1}. {todo}
            </div>
        {/each}
    </main>
    <div class={"enterToDo " + (error ? 'errorBorder' : "")}>
        <input bind:value={currToDo} type="text" placeholder="Enter todo">
        <button on:click={addToDo}>ADD</button>
    </div>
</div>


<style>
    .mainContainer {
        display: flex;
        flex-direction: column;
        background: navy;
        min-height: 100vh;
        gap: 24px;
        padding: 24px;
        width: 100%;
        max-width: 1000px;
        margin: 0 auto;
    }

    .headerContainer {
        display: flex;
        align-items: center;
        justify-content: space-between;
    }

    .headerContainer button {
        background: #003c5b;
        color: white;
        padding: 10px 18px;
        border: none;
        border-radius: 4px;
        font-weight: 700;
        display: flex;
        align-items: center;
        gap: 10px;
        cursor: pointer;
    }

    .headerContainer button i {
        font-size: 1.1rem;
    }

    .headerContainer button:hover {
        opacity: 0.7;

    }
    main {
        display: flex;
        flex-direction: column;
        gap: 8px;
        flex: 1;
    }

    .enterToDo {
        display: flex;
        align-items: stretch;
        border: 1px solid #0891b2;
        border-radius: 5px;
        overflow: hidden;
    }

    .errorBorder {
        border-color: coral !important;
    }
    .enterToDo input {
        background: transparent;
        border: none;
        padding: 14px;
        color: white;
        flex: 1;
    }

    .enterToDo input:focus {
        outline: none;
    }
    
    .enterToDo button {
        padding: 0 14px;
        background: #003c5b;
        border: none;
        color: cyan;
        font-weight: 600; 
        cursor: pointer;
    }
    .enterToDo button:hover { 
        background: transparent;
    }

</style>