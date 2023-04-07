<script>
    import { page } from '$app/stores'
    const diceId = $page.params.diceId
    let dicePic = null
    switch (diceId) {
        case (diceId == "d4"): {
            dicePic = "images/d4.png"
        }
        case (diceId == "d6"): {
            dicePic = "images/d6.png"
        }
        case (diceId == "d8"): {
            dicePic = "images/d8.png"
        }
        case (diceId == "d10"): {
            dicePic = "images/d10.png"
        }
        case (diceId == "d12"): {
            dicePic = "images/d12.png"
        }
        case (diceId == "d20"): {
            dicePic = "images/d20.png"
        }
    }
</script>

<h1>Dice View for {diceId}</h1>

<img src="" alt="{diceId}">

