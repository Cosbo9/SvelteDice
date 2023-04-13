<script>
    import { page } from '$app/stores'
    let maxAmount = 1;
    let minAmount = 1;
    let rollTimes = 1;
    const diceId = $page.params.diceId;
    let rollResult = 0;
    let resultList = [];
    let invalidAmount = false;

    function handleRoll(rollTimes, minAmount, maxAmount) {
        if (diceId != "custom") {
            maxAmount = diceId;
        }
        else {
            maxAmount = 1;
        }
        resultList = [];
        maxAmount = parseInt(diceId, 10)
        console.log("times", rollTimes)
        console.log("min", minAmount)
        console.log("max", maxAmount)
        for (let a = 0; a < rollTimes; a++) {
            rollResult = Math.floor(Math.random() * maxAmount + minAmount);
            resultList = [...resultList, rollResult];
        }
        console.log(resultList)
    }
</script>

<h1>Dice View for {diceId}</h1>

<div class="imageContainer">
    {#if diceId === "4"}
        <img src="../src/images/d4.png" alt="d4">
    {/if}
    {#if diceId === "6"}
        <img src="../src/images/d6.png">
    {/if}
    {#if diceId === "8"}
        <img src="../src/images/d8.png">
    {/if}
    {#if diceId === "10"}
        <img src="../src/images/d10.png">
    {/if}
    {#if diceId === "12"}
        <img src="../src/images/d12.png">
    {/if}
    {#if diceId === "20"}
        <img src="../src/images/d20.png">
    {/if}
    {#if diceId === "custom"}
        <span>
            select a random number between <input type="number" bind:value={minAmount}> and <input type="number" bind:value={maxAmount}>
        </span>
    {/if}
</div>
<div class="amount">
    <p>select how many dice to roll</p>
    <input type="number" bind:value={rollTimes}>
    <button on:click={handleRoll(rollTimes, minAmount, maxAmount)}>Roll!</button>
    {#if invalidAmount}
        <p>Please enter a valid amount</p>
    {/if}
</div>
<div class="results">
    {#each resultList as result, i}
        <p>roll number {i + 1} is {result}</p>
    {/each}
</div>


<style>
    h1 {
        text-decoration: underline;
    }
    img {
        width: 13vw;
        cursor: pointer;
    }
</style>