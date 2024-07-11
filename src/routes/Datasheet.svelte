<script>
    export let unitName;
    export let movement;
    export let toughness;
    export let wounds;
    export let leadership;
    export let save;
    export let objectiveControl;
    export let wargearOptions;
    export let abilities;
    export let factionKeywords;
    export let keywords;
    export let meleeWeapons = [];
    export let rangedWeapons = [];
</script>

<style>
    .container {
        background-color: #fff;
        border: 2px solid #000;
        padding: 15px;
        max-width: 600px;
        margin: auto;
        font-family: Arial, sans-serif;
        color: #333;
        background-color: #f4f4f4;
        margin-bottom: 20px;
    }
    .title {
        text-align: center;
        color: #444;
    }
    h2 {
        border-bottom: 2px solid #000;
        padding-bottom: 5px;
    }
    table {
        width: 100%;
        border-collapse: collapse;
        margin-bottom: 15px;
    }
    th, td {
        border: 1px solid #000;
        padding: 8px;
        text-align: center;
    }
    ul {
        list-style-type: none;
        padding-left: 0;
    }
    li {
        margin-bottom: 5px;
    }
    p {
        margin-top: 5px;
    }
</style>

<div class="container">
    <h1 class="title">{unitName}</h1>

    <h2>Unit Characteristics</h2>
    <table>
        <tr>
            <th>M</th>
            <th>T</th>
            <th>W</th>
            <th>Ld</th>
            <th>Sv</th>
            <th>OC</th>
        </tr>
        <tr>
            <td>{movement}</td>
            <td>{toughness}</td>
            <td>{wounds}</td>
            <td>{leadership}</td>
            <td>{save}</td>
            <td>{objectiveControl}</td>
        </tr>
    </table>

    <h2>Wargear Options</h2>
    <ul>
        {#each wargearOptions as option}
            <li>• {option}</li>
        {/each}
    </ul>

    <h2>Abilities</h2>
    <ul>
        {#each abilities as ability}
            <li><strong>{ability.name}:</strong> {ability.description}</li>
        {/each}
    </ul>

    <h2>Melee Weapons</h2>
    <table>
        <tr>
            <th>Name</th>
            <th>Range</th>
            <th>WS</th>
            <th>Strength</th>
            <th>AP</th>
            <th>Damage</th>
            <th>Weapon Keywords</th>
        </tr>
        {#each meleeWeapons as weapon}
        <tr>
            <td>{weapon.name}</td>
            <td>{weapon.range}</td>
            <td>{weapon.ws}</td>
            <td>{weapon.strength}</td>
            <td>{weapon.ap}</td>
            <td>{weapon.damage}</td>
            <td>{weapon.weaponKeywords.join(", ")}</td>
        </tr>
        {/each}
    </table>

    <h2>Ranged Weapons</h2>
    <table>
        <tr>
            <th>Name</th>
            <th>Range</th>
            <th>BS</th>
            <th>Strength</th>
            <th>AP</th>
            <th>Damage</th>
            <th>Weapon Keywords</th>
        </tr>
        {#each rangedWeapons as weapon}
        <tr>
            <td>{weapon.name}</td>
            <td>{weapon.range}</td>
            <td>{weapon.bs}</td>
            <td>{weapon.strength}</td>
            <td>{weapon.ap}</td>
            <td>{weapon.damage}</td>
            <td>{weapon.weaponKeywords.join(", ")}</td>
        </tr>
        {/each}
    </table>

    <h2>Faction Keywords</h2>
    <p>{factionKeywords.join(", ")}</p>

    <h2>Keywords</h2>
    <p>{keywords.join(", ")}</p>
</div>
