# sorc.loot.rng

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TTRPG Loot System</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        #lootResult {
            margin-top: 20px;
            font-weight: bold;
        }
    </style>
</head>
<body>

    <h1>TTRPG Loot Generator</h1>
    <button id="generateLootButton">Generate Loot</button>
    <div id="lootResult"></div>

    <script>
        function generateLoot() {
            const lootTable = [
                { name: "Uniquely Rare", probability: 0.42 },
                { name: "Extremely Rare", probability: 1.48 },
                { name: "Rare", probability: 4 },
                { name: "Uncommon", probability: 12 },
                { name: "Common", probability: 32 },
                { name: "No Loot", probability: 50 }
            ];

            // Generate a random number between 0 and 100
            const randomNum = Math.random() * 100;

            // Calculate cumulative probability and determine loot
            let cumulativeProbability = 0;
            for (const loot of lootTable) {
                cumulativeProbability += loot.probability;
                if (randomNum <= cumulativeProbability) {
                    document.getElementById('lootResult').innerText = `You found: ${loot.name}!`;
                    return;
                }
            }

            // In case no loot is determined (should not happen with given probabilities)
            document.getElementById('lootResult').innerText = 'No loot received.';
        }

        document.getElementById('generateLootButton').onclick = generateLoot;
    </script>

</body>
</html>
