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

    function editToDo(index) {
        // Create a new array 'newToDoList' by filtering out the to-do item at 
        // the given index.
        // The filter function checks if the current item's index (i) is not 
        // equal to the provided index. 
        let newToDoList = toDoList.filter((val, i) => {
            return i !== index;
        });
        // Save a reference to the to-do item that is being removed, located at 
        // the given index.
        // The removed item can be accessed through the 'currToDo' variable.
        currToDo = toDoList[index];
        // Update the 'toDoList' with the new filtered array, effectively 
        // removing the item at the given index.
        toDoList = newToDoList;
    }

    function removeToDo(index) {
        let newToDoList = toDoList.filter((val, i) => {
            return i !== index;
        });
        toDoList = newToDoList;
    }

</script>
<div class="mainContainer">   
        <div class="headerContainer">
            <h1>Todo List</h1>
            <div class="headerBtns">
                <button><i class="fa-regular fa-floppy-disk"></i>
                    <p>Save</p></button
            >    
            <button><i class="fa-solid fa-right-from-bracket"></i>
                <p>Logout</p></button
        >
            </div>
        </div>
    <main>
        {#if toDoList.length === 0}
        <p>
            You have nothing to do!
        </p>
        {/if}
        {#each toDoList as todo, index}
            <div class="todo">
                <p>
                    {index + 1}. {todo}
                </p>
                <div class="actions">
                    <i on:click={() => {
                        editToDo(index);
                    }}
                    on:keydown={() => {}} class="fa-regular fa-pen-to-square"></i>
                    <i on:click={() => {
                        removeToDo(index);
                    }}
                    on:keydown={() => {}} class="fa-regular fa-trash-can"></i>
                </div>
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

    .headerBtns {
        display: flex;
        align-items: center;
        gap: 14px ;
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

    .todo {
        border-left: 1px solid cyan;
        padding: 8px 14px;
        display: flex;
        align-items: center;
        justify-content: space-between;
    }

    .actions {
        display: flex;
        align-items: center;
        gap: 14px;
        font-size: 1.3rem;
    }

    .actions i {
        cursor: pointer;
    }

    .actions i:hover {
        color: coral;
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