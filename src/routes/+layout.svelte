<div class="maincontainer">
    <slot/>
</div>

<style>
    .maincontainer {
        min-height: 100vh;
        background: linear-gradient(to right, #000428, #000046);
        color: white;
        position: relative;
        display: flex;
        flex-direction: column;
    }
</style>