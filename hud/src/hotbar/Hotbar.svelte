<script>
    let position = "";
    let offHand = false;

    function handleChangeSlot(event) {
        position = `transform: translateX(${event.getSlot() * 42}px)`;
    }

    function handleChangeOffHand(event) {
        offHand = !event.getItemStack().isEmpty();
    }

    try {
        events.on("changeSlot", handleChangeSlot);
        events.on("changeOffHand", handleChangeOffHand);
    } catch (err) {
        console.log(err);
    }
</script>

{#if offHand}
    <div class="off-hand"></div>
{/if}
<div class="hotbar">
    <div style={position} class="active-slot"></div>
</div>

<style>
    .hotbar {
        position: absolute;
        bottom: 8px;
        left: 50%;
        transform: translateX(-50%);
        width: 378px;
        background: rgba(0, 0, 0, 0.5);
        border-radius: 4px;
        overflow: hidden;
    }

    .hotbar .active-slot {
        height: 42px;
        width: 42px;
        background: rgba(0, 0, 0, 0.36);
        transition: ease transform .2s;
    }

    .off-hand {
        position: absolute;
        bottom: 8px;
        left: 50%;
        transform: translateX(calc(-50% - 211px - 8px));
        height: 42px;
        width: 42px;
        border-radius: 4px;
        background: rgba(0, 0, 0, 0.5);
    }
</style>
