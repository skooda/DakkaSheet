# Dakkasheet Generator

Dakkasheet Generator is a simple Svelte application designed to generate Warhammer 40K datasheets from YAML data. This tool allows you to input YAML data representing unit attributes, wargear options, abilities, and weapons, and it dynamically generates a formatted datasheet for easy reference.

## Features

- **Dynamic Datasheet Generation**: Automatically generate datasheets based on YAML input.
- **Multiple Weapon Types**: Support for both melee and ranged weapons with detailed attributes.
- **Model Attributes**: Include key model attributes such as movement, toughness, wounds, leadership, save, and objective control.
- **Wargear Options and Abilities**: Display wargear options and special abilities for units.
- **Faction and Keywords**: Include faction keywords and unit keywords for comprehensive datasheets.

## Getting Started

### Prerequisites

- Node.js and npm installed on your machine.

### Installation

1. Clone the repository:
    ```bash
    git clone https://github.com/yourusername/dakkasheet-generator.git
    cd dakkasheet-generator
    ```

2. Install dependencies:
    ```bash
    npm install
    ```

3. Run the application:
    ```bash
    npm run dev
    ```

4. Open your browser and navigate to `http://localhost:5000`.

## Usage

1. Open the application in your browser.
2. Enter your YAML data into the provided textarea. The format should follow the example below:

    ```yaml
    - unitName: Space Marine Tactical Squad
      movement: 6"
      toughness: 4
      wounds: 1
      leadership: 7
      save: 3+
      objectiveControl: 2
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
      meleeWeapons:
        - name: Chainsword
          range: Melee
          ws: 3+
          strength: User
          ap: 0
          damage: 1
          weaponKeywords:
            - Melee
        - name: Power Fist
          range: Melee
          ws: 4+
          strength: x2
          ap: -3
          damage: D3
          weaponKeywords:
            - Melee
      rangedWeapons:
        - name: Boltgun
          range: 24"
          bs: 3+
          strength: 4
          ap: 0
          damage: 1
          weaponKeywords:
            - Rapid Fire 1
        - name: Plasma Gun
          range: 24"
          bs: 3+
          strength: 7
          ap: -3
          damage: 1
          weaponKeywords:
            - Rapid Fire 1
            - Overheat
    ```

3. Click the "Generate Datasheets" button to render the datasheets based on your input.

## Contributing

Contributions are welcome! If you have suggestions for improvements or encounter any issues, feel free to open an issue or submit a pull request.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgements

- This project uses [Svelte](https://svelte.dev/).
- YAML parsing is handled by [js-yaml](https://github.com/nodeca/js-yaml).

---

Enjoy generating your datasheets with Dakkasheet Generator!
