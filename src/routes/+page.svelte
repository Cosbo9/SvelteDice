<h1>Welcome to Svelte Dice 🎲</h1>
<h2>Choose an option to roll</h2>

<div class="choiceList">
    <a href="dice-list/4"><img src="../src/images/d4.png" alt="d4"></a>
    <a href="dice-list/6"><img src="../src/images/d6.png"></a>
    <a href="dice-list/8"><img src="../src/images/d8.png"></a>
    <a href="dice-list/10"><img src="../src/images/d10.png"></a>
    <a href="dice-list/12"><img src="../src/images/d12.png"></a>
    <a href="dice-list/20"><img src="../src/images/d20.png"></a>
    <button href="dice-list/custom"><p>Choose a custom range of numbers</p></button>
</div>

<style>
    h1 {
        text-align: center;
        font-size: 3.25rem;
        text-decoration: underline;
    }
    h2 {
        margin: 0 1rem;
    }
    img {
        width: 23vw;
        margin: 2rem;
    }
    button {
        margin: 2rem 4rem;
        cursor: pointer;
        background-color: cornflowerblue;
        color: white;
        border: none;
        border-radius: 5px;
        height: 3.5rem;
        font-weight: 600;
    }
</style>