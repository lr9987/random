<script lang="ts">
    let min:number = $state(1);
    let max:number = $state(10);
    let num:number = $state(1);
    function randomInt(min: number, max: number){
        return Math.floor(Math.random() * (max - min + 1)) + min;
    };
    async function startGen(min: number, max: number): Promise<void> {
        const steps = 20;
        const initialInterval = 40;
        const finalInterval = 80; 

        for (let step = 0; step <= steps; step++) {
            num = randomInt(min, max);
            const interval = initialInterval + ((finalInterval - initialInterval) * step) / steps;
            await new Promise(resolve => setTimeout(resolve, interval)); 
        }
        num = randomInt(min, max);
    }
</script>
<div style="font-size: 100px; text-align: center; margin-top:30px">{num}</div>
<div style="text-align:center; font-family:sans-serif;">
<button style="padding:8px 20px; border-radius:10px; margin-bottom:5px" onclick={() => startGen(min,max)}>Generate</button>
<br/>
<label style="margin-top:10px" for="min-input">Min:</label>
<input style="margin-top:10px" type="number" id="min-input" bind:value={min} min="1" />
<label for="max-input">Max:</label>
<input style="margin-top:10px" type="number" id="max-input" bind:value={max} min="1" />
</div>