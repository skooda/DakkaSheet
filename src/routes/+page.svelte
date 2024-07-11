<script>
    import { onMount } from 'svelte';
    import Datasheet from './Datasheet.svelte';

    let csvInput = `Space Marine Tactical Squad,6",3+,3+,4,4,1,1,7,3+,Any model may take a Boltgun.;The Sergeant may replace his Bolt Pistol with a Chainsword.;Up to two models may take a special weapon.,And They Shall Know No Fear:You can re-roll failed Morale tests for this unit.;Combat Squads:Before any models are deployed at the start of the game, a Tactical Squad containing 10 models may be split into two units, each containing 5 models.,Imperium;Adeptus Astartes,Infantry;Tactical Squad`;
    let datasheets = [];

    const parseCSV = () => {
        datasheets = csvInput.trim().split('\n').map(line => {
            const [
                unitName,
                movement,
                ws,
                bs,
                strength,
                toughness,
                wounds,
                attacks,
                leadership,
                save,
                wargearOptions,
                abilities,
                factionKeywords,
                keywords
            ] = line.split(',');

            return {
                unitName,
                movement,
                ws,
                bs,
                strength: parseInt(strength),
                toughness: parseInt(toughness),
                wounds: parseInt(wounds),
                attacks: parseInt(attacks),
                leadership: parseInt(leadership),
                save,
                wargearOptions: wargearOptions.split(';'),
                abilities: abilities.split(';').map(a => {
                    const [name, description] = a.split(':');
                    return { name, description };
                }),
                factionKeywords: factionKeywords.split(';'),
                keywords: keywords.split(';')
            };
        });
    };

    // Parse the initial CSV input on mount
    onMount(() => {
        parseCSV();
    });
</script>

<style>
    .input-area {
        max-width: 600px;
        margin: 20px auto;
        padding: 10px;
        background-color: #fff;
        border: 1px solid #ccc;
        border-radius: 4px;
        box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    }
    textarea {
        width: 100%;
        height: 100px;
        padding: 10px;
        border: 1px solid #ccc;
        border-radius: 4px;
        font-family: Arial, sans-serif;
        margin-bottom: 10px;
		text-wrap: nowrap;
    }
    button {
        padding: 10px 15px;
        background-color: #007bff;
        color: white;
        border: none;
        border-radius: 4px;
        cursor: pointer;
        font-size: 16px;
    }
    button:hover {
        background-color: #0056b3;
    }
</style>

<div class="input-area">
    <textarea bind:value={csvInput} placeholder="Enter CSV data here..."></textarea>
    <button on:click={parseCSV}>Generate Datasheets</button>
</div>

{#each datasheets as datasheet}
    <Datasheet {...datasheet} />
{/each}
