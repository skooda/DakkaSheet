<script>
    import { onMount } from 'svelte';
    import Datasheet from './Datasheet.svelte';
    import yaml from 'js-yaml';

    let yamlInput = `
- unitName: Space Marine Tactical Squad
  movement: 6"
  ws: 3+
  bs: 3+
  strength: 4
  toughness: 4
  wounds: 1
  attacks: 1
  leadership: 7
  save: 3+
  wargearOptions:
    - Any model may take a Boltgun.
    - The Sergeant may replace his Bolt Pistol with a Chainsword.
    - Up to two models may take a special weapon.
  abilities:
    - name: And They Shall Know No Fear
      description: You can re-roll failed Morale tests for this unit.
    - name: Combat Squads
      description: Before any models are deployed at the start of the game, a Tactical Squad containing 10 models may be split into two units, each containing 5 models.
  factionKeywords:
    - Imperium
    - Adeptus Astartes
  keywords:
    - Infantry
    - Tactical Squad
`;
    let datasheets = [];

    const parseYAML = () => {
        try {
            datasheets = yaml.load(yamlInput);
        } catch (e) {
            console.error(e);
        }
    };

    // Parse the initial YAML input on mount
    onMount(() => {
        parseYAML();
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
        height: 200px;
        padding: 10px;
        border: 1px solid #ccc;
        border-radius: 4px;
        font-family: Arial, sans-serif;
        margin-bottom: 10px;
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
    <textarea bind:value={yamlInput} placeholder="Enter YAML data here..."></textarea>
    <button on:click={parseYAML}>Generate Datasheets</button>
</div>

{#each datasheets as datasheet}
    <Datasheet {...datasheet} />
{/each}
