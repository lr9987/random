<script lang="ts">
let isHeads:boolean = $state(true);
let audioElement:HTMLAudioElement;
function playAudio() {
    audioElement.currentTime = 0; 
    audioElement.play();
}
</script>
<audio bind:this={audioElement} src="/flip.mp3"></audio>
{#if isHeads}
    <figure style="text-align:center; font-size:20px">
        <img src="/heads.png" 
        alt="Heads side of quarter coin"/>
        <figcaption style="font-family: sans-serif;">Heads</figcaption>
    </figure>
{:else}
    <figure style="text-align:center; font-size:20px">
        <img src="/tails.png" 
        alt="Tails side of quarter coin"/>
        <figcaption style="font-family: sans-serif;">Tails</figcaption>
    </figure>
{/if}
<div style="text-align:center">
<button style="padding:8px 20px; border-radius:10px;" onclick={() => {isHeads = Math.random() < 0.5; playAudio();}}>Flip</button>
</div>