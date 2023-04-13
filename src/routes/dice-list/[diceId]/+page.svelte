<script>
    import {page} from '$app/stores'

    let maxAmount = 1;
    let minAmount = 1;
    let rollTimes = 1;
    const diceId = $page.params.diceId;
    let rollResult = 0;
    let resultList = [];
    let invalidAmount = false;
    let invalidTimes = false;

    function handleRoll(rollTimes, minAmount, maxAmount) {
        invalidTimes = false;
        invalidAmount = false;
        resultList = [];
        if (rollTimes < 1) {
            invalidTimes = true;
        }
        if (diceId !== "custom") {
            maxAmount = parseInt(diceId, 10)
            maxAmount = diceId;
        }
        if (maxAmount > minAmount && minAmount > 0) {
            console.log("min", minAmount)
            console.log("max", maxAmount
            )
            for (let a = 0; a < rollTimes; a++) {
                rollResult = Math.floor(Math.random() * maxAmount + minAmount);
                resultList = [...resultList, rollResult];
            }
            console.log("results", resultList)
        } else {
            invalidAmount = true
        }
    }
</script>

<h1>Dice View for {diceId}</h1>

<div class="imageContainer">
    {#if diceId === "4"}
        <img src="../src/images/d4.png" alt="d4">
    {/if}
    {#if diceId === "6"}
        <img src="../src/images/d6.png" alt="d6">
    {/if}
    {#if diceId === "8"}
        <img src="../src/images/d8.png" alt="d8">
    {/if}
    {#if diceId === "10"}
        <img src="../src/images/d10.png" alt="d10">
    {/if}
    {#if diceId === "12"}
        <img src="../src/images/d12.png" alt="d12">
    {/if}
    {#if diceId === "20"}
        <img src="../src/images/d20.png" alt="d20">
    {/if}
    {#if diceId === "custom"}
        <span>
            select a random number between
            <input type="number" bind:value={minAmount}> and
            <input type="number" bind:value={maxAmount}>
            {#if invalidAmount}
                <p>Please enter a valid amount (first amount must be greater than 0 and less than second amount)</p>
            {/if}
        </span>
    {/if}
</div>
<div class="amount">
    <p>select how many dice to roll</p>
    <div class="interactContainer">
        <input type="number" bind:value={rollTimes}>
        <button on:click={handleRoll(rollTimes, minAmount, maxAmount)}>Roll!</button>
        {#if invalidTimes}
            <p>Please enter a valid amount</p>
        {/if}
    </div>
</div>
<div class="results">
    {#each resultList as result, i}
        <p>roll number {i + 1} is {result}</p>
    {/each}
</div>

<style>
    h1 {
        text-align: center;
        text-decoration: underline;
        font-size: 3rem;
    }

    .imageContainer {
        display: flex;
        justify-content: center;
    }

    .amount {
        width: 20vw;
        /*display: flex;*/
        /*flex-direction: column;*/
        /*justify-content: center;*/
    }

    img {
        width: 18vw;
    }
</style>