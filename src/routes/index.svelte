<script>
    import { onMount } from 'svelte';

    let position = 350;
    let keys = [];
    let wordList = ['Strong', 'Noisy', 'Imperviousness']

    function handleKey(e) {
        console.log(typeof(e))
        keys[e.keyCode] = true;
    }

    function handleUp(e) {
        keys[e.keyCode] = false;
    }

    function checkWord() {
        
    }

    onMount(() => {
        function update() {
            requestAnimationFrame(update);
            if (keys[37]) {
                position--
            }
            if (keys[39]) {
                position++
            }

            if(position <= 0) {
                position = 0
            }
            if (position >= 700) {
                position = 700
            }
        }
        update();
    })


</script>

<svelte:window on:keydown|preventDefault="{handleKey}" on:keyup|preventDefault="{handleUp}" />

<div class="w-[800px] h-[800px] bg-slate-200 flex flex-col justify-between">
    <div class="w-[100px] h-[100px] bg-red-500"></div>
    <div style="transform: translateX({position}px);" class="w-[100px] h-[100px] bg-blue-500"></div>
</div>