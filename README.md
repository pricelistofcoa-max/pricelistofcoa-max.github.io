<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>CoA Price List</title>
  <style>
  .red {
  color: red;
  font-weight: bold;
  }
  .eblue {
  color: #5865F2;
  font-weight: bold;
  }
  header, h1 {
  display: none;
  }
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background-color: black;
      color: white;
    }
header {
  background-color: #472678;
  color: white;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;       /* iç boşluk */
  position: fixed;      /* üstte sabitlemek için */
  top: 0;               /* sayfanın en üstüne yapışık */
  left: 0;              /* sol kenara yapışık */
  width: 100%;          /* ekranın tamamını kapsar */
  z-index: 1000;        /* diğer içeriklerin üstünde */
}
    .burger {
      font-size: 28px;
      cursor: pointer;
      color: white;
      background: none;
      border: none;
      user-select: none;
    }
    /* Burger Menü */
    .menu {
      position: absolute;
      top: 60px;
      right: 10px;
      background-color: #000;
      border: 2px solid #472678;
      padding: 10px;
      border-radius: 10px;
      display: none;
      flex-direction: column;
      gap: 5px;
      max-height: 400px;
      overflow-y: auto;
      z-index: 1000;
    }
    .menu a {
      color: white;
      text-decoration: none;
      padding: 6px 12px;
      border: 1px solid #472678;
      border-radius: 6px;
      background-color: black;
    }
    .menu a:hover {
      background-color: #472678;
    }
    .search-container {
      padding: 10px;
      text-align: center;
      margin-top: 50px;
    }
    .search-container input {
      width: 92%;
      padding: 8px;
      border: 2px solid #472678;
      border-radius: 5px;
      background-color: black;
      color: white;
    }
    .content {
      padding: 20px;
    }
    .item {
      border: 1px solid #472678;
      padding: 10px;
      margin: 10px 0;
      border-radius: 5px;
      background-color: #111;
      color: white;
    }
    .home {
      text-align: center;
      margin-top: 10px;
    }
    .home .note {
      margin-top: 6px;
      opacity: 0.9;
    }
    .btn-discord {
      display: inline-block;
      margin-top: 14px;
      padding: 10px 18px;
      border-radius: 12px;
      background-color: #5865F2;
      color: #fff;
      text-decoration: none;
      font-weight: 600;
      border: none;
      cursor: pointer;
    }
    .btn-discord:hover {
      background-color: #4752C4;
    }
    .btn-discord:active {
      transform: translateY(1px);
    }
    #header-title {
  font-size: 24px;    
  color: white;      
  font-weight: bold;  
}
  </style>
</head>
<body>
  <header>
    <div id="header-title">COA PRICE LIST</div>
    <button class="burger">☰</button>
    <div class="menu" id="burgerMenu">
      <a href="#" data-section="home">Home</a>
      <a href="#" data-section="Ores">Ores</a>
      <a href="#" data-section="Bars">Bars</a>
      <a href="#" data-section="Logs">Logs</a>
      <a href="#" data-section="Relics">Relics</a>
      <a href="#" data-section="Fishes">Fishes</a>
      <a href="#" data-section="Baits">Baits</a>
      <a href="#" data-section="SpellBinding">Spellbinding</a>
      <a href="#" data-section="Alchemy">Alchemy</a>
      <a href="#" data-section="Potions">Potions</a>
      <a href="#" data-section="Armors">Armors</a>
      <a href="#" data-section="Weapons">Weapons</a>
      <a href="#" data-section="Tools">Tools</a>
      <a href="#" data-section="BossParts">Boss Parts</a>
      <a href="#" data-section="EventItems">Event Items</a>
      <a href="#" data-section="Others">Others</a>
    </div>
  </header>

  <div class="search-container">
    <input type="text" id="search" placeholder="Search items...">
  </div>

  <div class="content" id="content"></div>

  <script>
    const burger = document.querySelector('.burger');
    const menu = document.getElementById('burgerMenu');
    const content = document.getElementById('content');
    const search = document.getElementById('search');

    const items = {
      Ores: ["Copper Ore : 400 each","Tin Ore : 400 each","Iron Ore : 800 each","Salt : 4k each","Coal : 3k-4k each","Crimstell Ore : 3k-4k each","Silver Ore : 4k-5k each","Gold Ore : 2.5k-3k each","Pink Salt : 7k each","Mythan Ore : 10k-12k each","Sandstone : 10k each","Cobalt Ore : 12k-14k each","Varaxium : 13k-15k each","Black Salt : 10k each","Magic Ore : 4k-4.5k each"],
      Bars: ["Copper Bar : 1k each","Iron Bar : 2k each","Steel Bar : 5k each","Crimsteel Bar : 20k each","Silver Bar : 25k-30k each","Gold Nugget : 30k-40k each","Gold Bar : 700k-800k each","Mythan Bar : 120k-140k each","Cobalt Bar : 120k each","Varax Bar : 160k each ","Magic Bar : 50k-55kk each"],
      Logs: ["Pine Logs  : 1k each","Dead Logs : 2k each","Birch Logs : 3k each","Applewood : 2k each","Willow Logs : 5k each","Oak Logs : 4k-5k each","Chestnut Logs : 7k-8k each","Maple Logs : 7k-8k each","Olive Logs : 11k-12k each","Stinkwood : 8-9k each","Magic Log : 2.3k each","Palm Wood : 4k each","PearWood : 6k-7k each","Lime Wood : 4k-5k each"],
      Relics: ["Relic of Accuracy : 2k-3k each","Relic of Guarding : 3k each","Relic of Healing : 4k each","Relic of Wealth : 3k each","Relic of Power : 5k each","Relic of Nature : 6k each","Relic of Fire : 8k each","Relic of Damage : 5k each","Relic of Leeching : 4k-5k each","Relic of Experience : 11k each","Relic of Wisdom : 13k each ","Ice relic : 4k-5k each","Cursed relic : 4k each","Relic of Efficiency : 4k each","Relic of Affliction : 4k each"],
      Fishes: ["Anchovies : 50 each","Gold Fish : 100 each","Mackerel : 500 each","Squid : 1k each","Sardine : 2k each","Eel : 1k each","Anglerfish : 1.5k-2k each","Trout : 10k each","Jellyfish : 500 each","Bass : 20k each","Herringbone : 500 each","Tuna : 5k-6k each","Lobster : 7k each","Sea Turtle : 13k-15k each","Manta Ray : 3k-4k each","Shark : 10k each","Orca : 25k each","Giant Squid : 40k each",],
      Baits: ["Earthworm : 10 each","Iceworm : 20 each","Corpseworm : 30 each","Toxicworm : 40 each","Sandworm : 50 each","Beetle : 1k-2k each","Grasshopper : 3k-5k each","Wasp : 3k-4k each","Scallop : 7k-9k each","Crab : 600 each",],
      SpellBinding: ["Book : 1k-1.5k each","Magic Essence : 600 each"],
      Alchemy: ["Bat Eye : 1k each","Pink Gelatin : 3k each","Fishing Spider Eye : 4k each","Brown Mushroom : 4k each","Forest Spider Eye : 4k each","Cow Skull : 8k each","Forest Bat Eye : 8k each","Frozen Gelatin : 8k each","Snow Core : 8k each","Sapling Leaf : 8k each","Ice Spider Eye : 8k each","Cave Spider Eye : 8k each","Skeletal Bat Eye : 8k each","Sapphire Scarab Leg : 10k each","Cave Bat Eye : 8.5k each","Envenomed Blood : 11k each","Raptor Claw : 9k each","Ruby Scarab Leg : 9k each","Forest Fiend Eye : 10k each","Desert Raptor Claw : 12k each","Rock Fiend Eye : 10k each","Hornet Antena : 11k each","Luminant Gelatin : 10k each","Juvenile Eye : 8k each","Ancient Bat Eye : 10k each","Ice Raptor Claw : 10k each","Spectral Flintstone  : 11k each","Arocite Scarab Leg : 10k each","Shadow Flintstone : 8k each","Phantom Flintstone : 12k each","Spectral Fiend Eye : 11k  each","Phantom Fiend Eye : 12k each","Magnetite Scarab Leg : 11k each","Corrupted Eye : 11k each","Golemite Bat Eye : 10k each","Golemite Fiend Eye : 10k each","Tormented Eye : 15k each","Disdain Eye : 20k-22k each","Baby Dragon Spine : 10k each","Ragefull Eye : 15k each"],
      Potions:["Potion : each","Mining Potion : 10k each","Woodcutting Potion : 10k each","Fishing Potion : 10k each","Smithing Potion : 10k each","Crafting Potion : 15k each","Cooking Potion : 15k each","Spellbinding Potion : 17k each","Taskmaster's Brew : 7k each","Prospector's Brew : 15k-20k each","Lumberjack's Ale : 20k each","Blacksmith's Stout : 13k each","Artisan's Syrup : 20k each","Angler's Elixir : 20k each","Chef's Kiss : 18k each","Imbuer's Wine : 25k each","Spellpower Potion : 12k each","Concentrated Elixir : 15k each","Divine Clarity : 20k each","Titan's Strength : 15k each","Duelist's Draft : 10k each","Stonebound Salve : 22k each","Backlash Balm : 15k each","Berserker Potion : 14k each","Arcanist's Wrath : 25k each","Forsworn Focus : 20k each","Antidote : 20k each","Frostskin Potion : 10k each","Arctic Potion : 12k each","Scavenger's Balm : 25k each","Vampirism Potion : 20k each","Assassin's Tonic : 18k each","Auric Bloom : 10k each","Mirrorback Brew : 22k each","Golem's Power : 23k  each","Guardian's Bulwark : 23k each","Quietus : 25k each","Midas Brew : 30k each","Featherwalk Potion : 30k each","Sanguiene Oath : 25k each","Dance of the Undead : 30k each","Gilded Transmutation : 50k each","Cloudwalk Potion : 40k each","Distilled Extract : 50k each","Provocation Potion : 40k each","Strigoi's Covenant : 40k each","Death's Rally : 35k-40k each"],
      Armors: ["Cobalt Armor : each","Varax Armor : 5m each","Glacial Armor : each","Deadrock Armor : each","Spectral Armor : each","Phantom Armor : 30m each","Nightspun Armor : 400k each"],
      Weapons: ["Sharper Mythan Sword : 80k-100k each","Cobalt Sword : 100k-150k each","Chaotic Mythan Sword : 200k each","Varaxite Sword : 300k each","Glacial Blade : 1m-1.2m each","Nature's Blade : 2m each","Spectral Sword : 13m each","Phantom Sword : 15m each","Ancient Scimitar : 130m each","Fire Staff : 50k each","Ice Staff : 50k each","Nature Staff : 50k each","Cursed Staff : 50k each","Elder Fire Staff : 200k  each","Elder Ice Staff : 200k each","Elder Nature Staff : 200k each","Elder Cursed Staff : 200k each","Nightspun Staff : 200k each"],
      Tools: ["Mythan Axe : 100k each","Mythan Pickaxe : 100k each","Mythan Rod : 100k each","Mythan Secateurs : 80k-100k each","Cobalt Axe : 200k-300k each","Cobalt Pickaxe : 200k-300k each","Cobalt Rod : 200k-300k each","Cobalt Secateurs : 100k-200k each","Varaxite Axe : 300k-400k each","Varaxite Pickaxe : 300k-400k each","Varaxite Rod : 300k-400k  each","Varaxite Secateurs : 300k-400k each","Magic Axe : 300k-400k each","Magic Pickaxe : 300k -400k each","Magic Rod : 300k-400k each","Bryomera Secateurs : 30m-40m each","Ancient Axe : 16-17m each","Ancient Pickaxe : 16-17m each","Ancient Rod : 8m-11m each"],
      BossParts: ["Balance fragment :  3m each","Golemite Slab : 3m each","Golemite Shard : 4m each","Eye of Golemite : 2m each","Golemite Orb : 3m each","Golemite Artifact : 1.5m each","Dragon Scale : 15k each","Dragon Eye : 11m each","Dragon Claw : 16m each","Dragon Horn : 2m each","Slivers of Rage : 6m/100 each","Slivers of Corruption : 8.5m/100 each","Slivers of Disdain : 8m/100 each","Slivers of Torment : 8m/100 each","Leg of Nydarax : 40m-45m each","Eye of Nydarax : 2m each","Gold Key : each","Mummy Bandage : each","Mummy Soul : each","Ancient Tablet : 5k each"],
      EventItems: ["Sugar Brew : each","Party Hat : each","Santa Hat : each","Jingle Top : each","Jingle Pants : each","Candy Cane : each","Easter Egg : each","Bag of Tricks : each","Bag of Sweets : each","Magic Bag of Treats : each","Pumpking Helm : each","Pumpking Sword : each","Pumpking Shield : each","Party Hat 2 : each","Jester Hat : each","Based Santa Hat : each","Scrooge Hat : each","Scrooge Shirt : each","Pack of Snow : each","Xmas Tree Sword : each","Candy Cane Staff : each","Egg Head : each","Hand of Baphomet : each","Head of Baphomet : each","Pumpkin Zombie Hat : each","Party Hat 3 : each","Classy Jacket : each","Classy Pants : each","Sparkling Grapejuice : each","Antlers : each","Christmas Tree Hat : each","Jingle Hat : each","White Present : each","Red Present : each","Gold Present : each","Carrot Launcher : each","Carrotproof Helmet : each","Carrotproof Vest : each","Egg Ring : each","Party Hat 4 : each","Box of Chocolate : each","Box of Pralines : each","Loveshot : each","Arrow Head : each","Heartseeker : each","Eternal Love : each","Lootkin : each","Bionic Skull : each","Bionic Ribcage : each","Bionic Limbs : each","Scream Mask : each","Birthday Cake : each","Party Hat 5 : each","Blue Balloon : each","Red Balloon : each","Yellow Balloon : each","Green Balloon : each","Bunch of Balloons : each","Snowball Ammo : each","Ring of Snow : each","Snowball Launcher : each","Black Santa Hat : each","Lucky Egg : each","Carrot Rocket : each","Bonka's Barrier : each","Eggy Bludgeon : each","Wabbit Hat : each","Party Hat 6 : each","Party-Crasher : each","Smelly Key : each","Leaky Leek : each","Evileek Staff : each","Evileek Shield : each","Evileek Mask : each","Sleekest : each","Chicken Head : each","Chicken Wings : each","Chicken Feathers : each"
    ],
      Others: ["Ruby : 50k each","Sapphire : 50k each","Emerald : 70k each","Arosite : 80k each","Sandstone Shield : 2m-3m each","Scorpion Shield : 3.5m each","Deadrock Shield : 4m-4.5m each","Ancient Shield : 130m each","Iron Spade : 20k each","Crimsteel Spade : 20k-40k each","Mythan Spade : 50k-130k each","Golemite Spade : 120k-150k each","Ancient Spade : 800k-1m each","Saving Grace : 120k-150k each","Bat Amulet : 200k each","Nature Amulet : 50k each","Amulet of Focus : 3m each","Prospector's Necklace : 4m each","Ruby Necklace : 300k each","Sapphire Necklace : 300k each","Emerald Necklace : 400k each","Arosite Necklace : 450k each","Magnetite Necklace : 3m each","Battle Necklace : 5m each","Scorpion Gauntlets : 500k each","Raptor Gloves : 700k each","Desert Raptor Gloves : 800k each","Ice Raptor Gloves : 1m each","Cactus Gloves : 4m-5m each","Frozen Skull : 35m each","Icy Right Half : 2m each","Icy Left Half : 2m each","Ring of Treasure : 1m each","Nature Ring : 50k each","Bat Ring : 200k each","Ring of Might : 2m each","Infernal Ring : 3m-4m each","Cactus Ring : 8m each","Snake charm : 3m each","Infernal Hammer : 10m each","Ring of Violation : 20m each","Pendant of Serenity : 15m each","Inferno Tome : 100 each","Consume Tome : 120 each","Blizzard Tome : 50 each","Torture Tome : 200-300 each","Lollipop : 1.3m each","Nydarax Teleport Scrool : 1m each","Red Key : 100k each","Blue Key : 20k each","Green Key : 50k each","Mysterious Artifact : 250k each","Key to 'Disdain' : 50k each","Key to 'Rage' : 200k each","Key to 'Torment' : 200k each","Key to 'Corruption' : 200k each","Portal Charge : 400k each","Soul jar : 1.2m-1.3m","Magnetite : 130k-150k each","Ankh key : 400k each",]
    };

    // --- Ores için yönlendirme linkleri ---
    const itemLinks = {
      "Copper Ore": "https://www.curseofaros.wiki/wiki/Copper_Ore",
      "Tin Ore": "https://www.curseofaros.wiki/wiki/Tin_Ore",
      "iron ore": "https://www.curseofaros.wiki/wiki/Iron_Ore",
      "Salt": "https://www.curseofaros.wiki/wiki/Salt",
      "Coal": "https://www.curseofaros.wiki/wiki/Coal",
      "Crimstell Ore": "https://www.curseofaros.wiki/wiki/Crimsteel_Ore",
      "Silver Ore": "https://www.curseofaros.wiki/wiki/Silver_Ore",
      "Gold Ore": "https://www.curseofaros.wiki/wiki/Gold_Ore",
      "Pink Salt": "https://www.curseofaros.wiki/wiki/Pink_Salt",
      "Mythan Ore": "https://www.curseofaros.wiki/wiki/Mythan_Ore",
      "Sandstone": "https://www.curseofaros.wiki/wiki/Sandstone","cobalt ore": "https://www.curseofaros.wiki/wiki/Cobalt_Ore",
      "Varaxium": "https://www.curseofaros.wiki/wiki/Varaxium",
      "Black Salt": "https://www.curseofaros.wiki/wiki/Black_Salt",
      "Magic Ore": "https://www.curseofaros.wiki/wiki/Magic_Ore",
      "Copper Bar": "https://www.curseofaros.wiki/wiki/Bronze_Bar",
      "Iron Bar":"https://www.curseofaros.wiki/wiki/Iron_Bar",
      "Steel Bar":"https://www.curseofaros.wiki/wiki/Steel_Bar",
      "Crimsteel Bar":"https://www.curseofaros.wiki/wiki/Crimsteel_Bar",
      "silver bar":"https://www.curseofaros.wiki/wiki/Silver_Bar",
      "Gold Nugget":"https://www.curseofaros.wiki/wiki/Gold_Nugget",
      "Gold Bar":"https://www.curseofaros.wiki/wiki/Gold_Bar",
      "Mythan Bar":"https://www.curseofaros.wiki/wiki/Mythan_Bar",
      "Cobalt Bar":"https://www.curseofaros.wiki/wiki/Cobalt_Bar",
      "Varax Bar":"https://www.curseofaros.wiki/wiki/Varaxite_Bar",
      "Magic Bar":"https://www.curseofaros.wiki/wiki/Magic_Bar",
      "Pine Logs":"https://www.curseofaros.wiki/wiki/Pine_Logs",
      "Dead Logs":"https://www.curseofaros.wiki/wiki/Dead_Logs",
      "Birch Logs":"https://www.curseofaros.wiki/wiki/Birch_Logs",
      "Applewood":"https://www.curseofaros.wiki/wiki/Applewood",
      "Willow Logs":"https://www.curseofaros.wiki/wiki/Willow_Logs",
      "Oak Logs":"https://www.curseofaros.wiki/wiki/Oak_Logs",
      "Chestnut Logs":"https://www.curseofaros.wiki/wiki/Chestnut_Logs",
      "Maple Logs":"https://www.curseofaros.wiki/wiki/Maple_Logs",
      "Olive Logs":"https://www.curseofaros.wiki/wiki/Olive_Logs",
      "Stinkwood":"https://www.curseofaros.wiki/wiki/Stinkwood",
      "Magic Log":"https://www.curseofaros.wiki/wiki/Magic_Log",
      "Palm Wood":"https://www.curseofaros.wiki/wiki/Palm_Wood",
      "PearWood":"https://www.curseofaros.wiki/wiki/Pearwood",
      "Lime Wood":"https://www.curseofaros.wiki/wiki/Lime_Wood",
      "Relic of Accuarcy":"https://www.curseofaros.wiki/wiki/Relic_of_Accuracy",
      "Relic of Guarding":"https://www.curseofaros.wiki/wiki/Relic_of_Guarding",
      "Relic of Healing":"https://www.curseofaros.wiki/wiki/Relic_of_Healing",
      "Relic of Wealth":"https://www.curseofaros.wiki/wiki/Relic_of_Wealth",
      "Relic of Power":"https://www.curseofaros.wiki/wiki/Relic_of_Power",
      "Relic of Nature":"https://www.curseofaros.wiki/wiki/Relic_of_Nature",
      "Relic of Fire":"https://www.curseofaros.wiki/wiki/Relic_of_Fire",
      "Relic of Damage":"https://www.curseofaros.wiki/wiki/Relic_of_Damage",
      "Relic of Experience":"https://www.curseofaros.wiki/wiki/Relic_of_Experience",
      "Relic of Leeching":"https://www.curseofaros.wiki/wiki/Relic_of_Leeching",
      "Relic of Wisdom":"https://www.curseofaros.wiki/wiki/Relic_of_Wisdom",
      "Ice Relic":"https://www.curseofaros.wiki/wiki/Ice_Relic",
      "Cursed Relic":"https://www.curseofaros.wiki/wiki/Cursed_Relic",
      "Relic of Efficiency":"https://www.curseofaros.wiki/wiki/Relic_of_Efficiency",
      "Relic of Affliction":"https://www.curseofaros.wiki/wiki/Relic_of_Affliction",
      "Anchovies":"https://www.curseofaros.wiki/wiki/Anchovies",
      "Gold Fish":"https://www.curseofaros.wiki/wiki/Goldfish",
      "Mackerel":"https://www.curseofaros.wiki/wiki/Mackerel",
      "Squid":"https://www.curseofaros.wiki/wiki/Squid",
      "Sardine":"https://www.curseofaros.wiki/wiki/Sardine",
      "Eel":"https://www.curseofaros.wiki/wiki/Eel",
      "Anglerfish":"https://www.curseofaros.wiki/wiki/Anglerfish",
      "Trout":"https://www.curseofaros.wiki/wiki/Trout",
      "Jellyfish":"https://www.curseofaros.wiki/wiki/Jellyfish",
      "Bass":"https://www.curseofaros.wiki/wiki/Bass",
      "Herringbone":"https://www.curseofaros.wiki/wiki/Herringbone",
      "Tuna":"https://www.curseofaros.wiki/wiki/Tuna",
      "Lobster":"https://www.curseofaros.wiki/wiki/Lobster",
      "Sea Turtle":"https://www.curseofaros.wiki/wiki/Sea_Turtle",
      "Manta Ray":"https://www.curseofaros.wiki/wiki/Manta_Ray",
      "Shark":"https://www.curseofaros.wiki/wiki/Shark",
      "Orca":"https://www.curseofaros.wiki/wiki/Orca",
      "Giant Squid":"https://www.curseofaros.wiki/wiki/Giant_Squid",
      "Earthworm":"https://www.curseofaros.wiki/wiki/Earthworm",
      "Iceworm":"https://www.curseofaros.wiki/wiki/Iceworm",
      "Corpseworm":"https://www.curseofaros.wiki/wiki/Corpseworm",
      "Toxicworm":"https://www.curseofaros.wiki/wiki/Toxic_Worm",
      "Sandworm":"https://www.curseofaros.wiki/wiki/Sandworm",
      "Beetle":"https://www.curseofaros.wiki/wiki/Beetle",
      "Grasshopper":"https://www.curseofaros.wiki/wiki/Grasshopper",
      "Wasp":"https://www.curseofaros.wiki/wiki/Wasp",
      "Scallop":"https://www.curseofaros.wiki/wiki/Scallop",
      "Book":"https://www.curseofaros.wiki/wiki/Book",
      "Magic Essence":"https://www.curseofaros.wiki/wiki/Magic_Essence",
      "Bat Eye":"https://www.curseofaros.wiki/wiki/Bat_Eye",
      "Pink Gelatin":"https://www.curseofaros.wiki/wiki/Pink_Gelatin",
      "Fishing Spider Eye":"https://www.curseofaros.wiki/wiki/Fishing_Spider_Eye",
      "Brown Mushroom":"https://www.curseofaros.wiki/wiki/Brown_Mushroom",
      "Forest Spider Eye":"https://www.curseofaros.wiki/wiki/Forest_Spider_Eye",
      "Cow Skull":"https://www.curseofaros.wiki/wiki/Cow_Skull",
      "Forest Bat Eye":"https://www.curseofaros.wiki/wiki/Forest_Bat_Eye",
      "Frozen Gelatin":"https://www.curseofaros.wiki/wiki/Frozen_Gelatin",
      "Snow Core":"https://www.curseofaros.wiki/wiki/Snow_Core",
      "Sapling Leaf":"https://www.curseofaros.wiki/wiki/Sapling_Leaf",
      "Ice Spider Eye":"https://www.curseofaros.wiki/wiki/Ice_Spider_Eye",
      "Cave Spider Eye":"https://www.curseofaros.wiki/wiki/Cave_Spider_Eye",
      "Skeletal Bat Eye":"https://www.curseofaros.wiki/wiki/Skeletal_Bat_Eye",
      "Sapphire Scarab Leg":"https://www.curseofaros.wiki/wiki/Sapphire_Scarab_Leg",
      "Cave Bat Eye":"https://www.curseofaros.wiki/wiki/Cave_Bat_Eye",
      "Envenomed Blood":"https://www.curseofaros.wiki/wiki/Envenomed_Blood",
      "Raptor Claw":"https://www.curseofaros.wiki/wiki/Raptor_Claw",
      "Ruby Scarab Leg":"https://www.curseofaros.wiki/wiki/Ruby_Scarab_Leg",
      "Forest Fiend Eye":"https://www.curseofaros.wiki/wiki/Forest_Fiend_Eye",
      "Desert Raptor Claw":"https://www.curseofaros.wiki/wiki/Desert_Raptor_Claw",
      "Rock Fiend Eye":"https://www.curseofaros.wiki/wiki/Rock_Fiend_Eye",
      "Hornet Antena":"https://www.curseofaros.wiki/wiki/Hornet_Antenna",
      "Luminant Gelatin":"https://www.curseofaros.wiki/wiki/Luminant_Gelatin",
      "Juvenile Eye":"https://www.curseofaros.wiki/wiki/Juvenile_Eye",
      "Ancient Bat Eye":"https://www.curseofaros.wiki/wiki/Ancient_Bat_Eye",
      "Ice Raptor Claw":"https://www.curseofaros.wiki/wiki/Ice_Raptor_Claw",
      "Spectral Flintstone":"https://www.curseofaros.wiki/wiki/Spectral_Flintstone",
      "Arocite Scarab Leg":"https://www.curseofaros.wiki/wiki/Arosite_Scarab_Leg",
      "Shadow Flintstone":"https://www.curseofaros.wiki/wiki/Shadow_Flintstone",
      "Phantom Flintstone":"https://www.curseofaros.wiki/wiki/Phantom_Flintstone",
      "Spectral Fiend Eye":"https://www.curseofaros.wiki/wiki/Spectral_Fiend_Eye",
      "Phantom Fiend Eye":"https://www.curseofaros.wiki/wiki/Phantom_Fiend_Eye",
      "Magnetite Scarab Leg":"https://www.curseofaros.wiki/wiki/Magnetite_Scarab_Leg",
      "Corrupted Eye":"https://www.curseofaros.wiki/wiki/Corrupted_Eye",
      "Golemite Bat Eye":"https://www.curseofaros.wiki/wiki/Golemite_Bat_Eye",
      "Golemite Fiend Eye":"https://www.curseofaros.wiki/wiki/Golemite_Fiend_Eye",
      "Tormented Eye":"https://www.curseofaros.wiki/wiki/Tormented_Eye",
      "Disdain Eye":"https://www.curseofaros.wiki/wiki/Disdained_Eye",
      "Baby Dragon Spine":"https://www.curseofaros.wiki/wiki/Baby_Dragon_Spine",
      "Ragefull Eye":"https://www.curseofaros.wiki/wiki/Rageful_Eye",
      "Potion":"https://www.curseofaros.wiki/wiki/Potion",
      "Mining Potion":"https://www.curseofaros.wiki/wiki/Mining_Potion",
      "Woodcutting Potion":"https://www.curseofaros.wiki/wiki/Woodcutting_Potion",
      "Fishing Potion":"https://www.curseofaros.wiki/wiki/Fishing_Potion",
      "Smithing Potion":"https://www.curseofaros.wiki/wiki/Smithing_Potion",
      "Crafting Potion":"https://www.curseofaros.wiki/wiki/Crafting_Potion",
      "Cooking Potion":"https://www.curseofaros.wiki/wiki/Cooking_Potion",
      "Spellbinding Potion":"https://www.curseofaros.wiki/wiki/Spellbinding_Potion",
      "Taskmaster's Brew":"https://www.curseofaros.wiki/wiki/Taskmaster%27s_Brew",
      "Prospector's Brew":"https://www.curseofaros.wiki/wiki/Prospector%27s_Brew",
      "Lumberjacks Ale":"https://www.curseofaros.wiki/wiki/Lumberjack%27s_Ale",
      "Blacksmith's Stout":"https://www.curseofaros.wiki/wiki/Blacksmith%27s_Stout",
      "Artisan's Syrup":"https://www.curseofaros.wiki/wiki/Artisan%27s_Syrup",
      "Angler's Elixir":"https://www.curseofaros.wiki/wiki/Angler%27s_Elixir",
      "Chef's Kiss":"https://www.curseofaros.wiki/wiki/Chef%27s_Kiss",
      "Imbuer's Wine":"https://www.curseofaros.wiki/wiki/Imbuer%27s_Wine",
      "Spellpower Potion":"https://www.curseofaros.wiki/wiki/Spellpower_Potion",
      "Concentrated Elixir":"https://www.curseofaros.wiki/wiki/Concentrated_Elixir",
      "Divine Clarity":"https://www.curseofaros.wiki/wiki/Divine_Clarity",
      "Titan's Strength":"https://www.curseofaros.wiki/wiki/Titan%27s_Strength",
      "Duelist's Draft":"https://www.curseofaros.wiki/wiki/Duelist%27s_Draft",
      "Stonebound Salve":"https://www.curseofaros.wiki/wiki/Stonebound_Salve",
      "Backlash Balm":"https://www.curseofaros.wiki/wiki/Backlash_Balm",
      "Berserker Potion":"https://www.curseofaros.wiki/wiki/Berserker_Potion",
      "Arcanist's Wrath":"https://www.curseofaros.wiki/wiki/Arcanist%27s_Wrath",
      "Forsworn Focus":"https://www.curseofaros.wiki/wiki/Forsworn_Focus",
      "Antidote":"https://www.curseofaros.wiki/wiki/Antidote",
      "Frostskin Potion":"https://www.curseofaros.wiki/wiki/Frostskin_Potion",
      "Arctic Potion":"https://www.curseofaros.wiki/wiki/Arctic_Potion",
      "Scavenger's Balm":"https://www.curseofaros.wiki/wiki/Scavenger%27s_Balm",
      "Vampirism Potion":"https://www.curseofaros.wiki/wiki/Vampirism_Potion",
      "Assassin's Tonic":"https://www.curseofaros.wiki/wiki/Assassin%27s_Tonic",
      "Auric Bloom":"https://www.curseofaros.wiki/wiki/Auric_Bloom",
      "Mirrorback Brew":"https://www.curseofaros.wiki/wiki/Mirrorback_Brew",
      "Golem's Power":"https://www.curseofaros.wiki/wiki/Golem%27s_Power",
      "Guardian's Bulwark":"https://www.curseofaros.wiki/wiki/Guardian%27s_Bulwark",
      "Quietus":"https://www.curseofaros.wiki/wiki/Quietus",
      "Midas Brew":"https://www.curseofaros.wiki/wiki/Midas_Brew",
      "Featherwalk Potion":"https://www.curseofaros.wiki/wiki/Featherwalk_Potion",
      "Sanguiene Oath":"https://www.curseofaros.wiki/wiki/Sanguine_Oath",
      "Dance of the Undead":"https://www.curseofaros.wiki/wiki/Dance_of_the_Undead",
      "Gilded Transmutation":"https://www.curseofaros.wiki/wiki/Gilded_Transmutation",
      "Cloudwalk Potion":"https://www.curseofaros.wiki/wiki/Cloudwalk_Potion",
      "Distilled Extract":"https://www.curseofaros.wiki/wiki/Distilled_Extract",
      "Provocation Potion":"https://www.curseofaros.wiki/wiki/Provocation_Potion",
      "Strigoi's Covenant":"https://www.curseofaros.wiki/wiki/Strigoi%27s_Covenant",
      "Death's Rally":"https://www.curseofaros.wiki/wiki/Death%27s_Rally",
      "Cobalt Armor":"https://www.curseofaros.wiki/wiki/Melee#Headgear",
      "Varax Armor":"https://www.curseofaros.wiki/wiki/Melee#Headgear",
      "Glacial Armor":"https://www.curseofaros.wiki/wiki/Melee#Headgear",
      "Deadrock Armor":"https://www.curseofaros.wiki/wiki/Melee#Headgear",
      "Spectral Armor":"https://www.curseofaros.wiki/wiki/Melee#Headgear",
      "Phantom Armor":"https://www.curseofaros.wiki/wiki/Melee#Headgear",
      "Nightspun Armor":"https://www.curseofaros.wiki/wiki/Magic#Headgear",
      "Sharper Mythan Sword":"https://www.curseofaros.wiki/wiki/Sharper_Mythan_Sword",
      "Cobalt Sword":"https://www.curseofaros.wiki/wiki/Cobalt_Sword",
      "Chaotic Mythan Sword":"https://www.curseofaros.wiki/wiki/Chaotic_Mythan_Sword",
      "Varaxite Sword":"https://www.curseofaros.wiki/wiki/Varaxite_Sword",
      "Glacial Blade":"https://www.curseofaros.wiki/wiki/Glacial_Blade",
      "Nature's Blade":"https://www.curseofaros.wiki/wiki/Nature%27s_Blade",
      "Spectral Sword":"https://www.curseofaros.wiki/wiki/Spectral_Sword",
      "Phantom Sword":"https://www.curseofaros.wiki/wiki/Phantom_Sword",
      "Ancient Scimitar":"https://www.curseofaros.wiki/wiki/Ancient_Scimitar",
      "Fire Staff":"https://www.curseofaros.wiki/wiki/Fire_Staff",
      "Ice Staff":"https://www.curseofaros.wiki/wiki/Ice_Staff",
      "Nature Staff":"https://www.curseofaros.wiki/wiki/Nature_Staff",
      "Cursed Staff":"https://www.curseofaros.wiki/wiki/Cursed_Staff",
      "Elder Fire Staff":"https://www.curseofaros.wiki/wiki/Elder_Fire_Staff",
      "Elder Ice Staff":"https://www.curseofaros.wiki/wiki/Elder_Ice_Staff",
      "Elder Nature Staff":"https://www.curseofaros.wiki/wiki/Elder_Nature_Staff",
      "Elder Cursed Staff":"https://www.curseofaros.wiki/wiki/Elder_Cursed_Staff",
      "Nightspun Staff":"https://www.curseofaros.wiki/wiki/Nightspun_Staff",
      "Mythan Axe":"https://www.curseofaros.wiki/wiki/Mythan_Axe",
      "Mythan Pickaxe":"https://www.curseofaros.wiki/wiki/Mythan_Pickaxe",
      "Mythan Rod":"https://www.curseofaros.wiki/wiki/Mythan_Rod",
      "Mythan Secateurs":"https://www.curseofaros.wiki/wiki/Mythan_Secateurs",
      "Cobalt Axe":"https://www.curseofaros.wiki/wiki/Cobalt_Axe",
      "Cobalt Pickaxe":"https://www.curseofaros.wiki/wiki/Cobalt_Pickaxe",
      "Cobalt Rod":"https://www.curseofaros.wiki/wiki/Cobalt_Rod",
      "Cobalt Secateurs":"https://www.curseofaros.wiki/wiki/Cobalt_Secateurs",
      "Varaxite Axe":"https://www.curseofaros.wiki/wiki/Varaxite_Axe",
      "Varaxite Pickaxe":"https://www.curseofaros.wiki/wiki/Varaxite_Pickaxe",
      "Varaxite Rod":"https://www.curseofaros.wiki/wiki/Varaxite_Rod",
      "Varaxite Secateurs":"https://www.curseofaros.wiki/wiki/Varaxite_Secateurs",
      "Magic Axe":"https://www.curseofaros.wiki/wiki/Magic_Axe",
      "Magic Pickaxe":"https://www.curseofaros.wiki/wiki/Magic_Pickaxe",
      "Magic Rod":"https://www.curseofaros.wiki/wiki/Magic_Rod",
      "Bryomera Secateurs":"https://www.curseofaros.wiki/wiki/Bryomera_Secateurs",
      "Ancient Axe":"https://www.curseofaros.wiki/wiki/Ancient_Axe",
      "Ancient Pickaxe":"https://www.curseofaros.wiki/wiki/Ancient_Pickaxe",
      "Ancient Rod":"https://www.curseofaros.wiki/wiki/Ancient_Rod",
      "Balance Fragment":"https://www.curseofaros.wiki/wiki/Balance_Fragment",
      "Golemite Slab":"https://www.curseofaros.wiki/wiki/Golemite_Slab",
      "Golemite Shard":"https://www.curseofaros.wiki/wiki/Golemite_Shard",
      "Eye of Golemite":"https://www.curseofaros.wiki/wiki/Eye_of_Golemite",
      "Golemite Orb":"https://www.curseofaros.wiki/wiki/Golemite_Orb",
      "Dragon Scale":"https://www.curseofaros.wiki/wiki/Dragon_Scale",
      "Dragon Eye":"https://www.curseofaros.wiki/wiki/Dragon_Eye",
      "Dragon claw":"https://www.curseofaros.wiki/wiki/Dragon_Claw",
      "Dragon Horn":"https://www.curseofaros.wiki/wiki/Dragon_Horn",
      "Slivers of Rage":"https://www.curseofaros.wiki/wiki/Slivers_of_Rage",
      "Slivers of Corruption":"https://www.curseofaros.wiki/wiki/Slivers_of_Corruption",
      "Slivers of Disdain":"https://www.curseofaros.wiki/wiki/Slivers_of_Disdain",
      "Slivers of Torment":"https://www.curseofaros.wiki/wiki/Slivers_of_Torment",
      "Leg of Nydarax":"https://www.curseofaros.wiki/wiki/Leg_of_Nydarax",
      "Eye of Nydarax":"https://www.curseofaros.wiki/wiki/Eye_of_Nydarax",
      "Gold Key":"https://www.curseofaros.wiki/wiki/Gold_Key",
      "Mummy Bandage":"https://www.curseofaros.wiki/wiki/Mummy_Bandage",
      "Mummy soul":"https://www.curseofaros.wiki/wiki/Mummy_Soul",
      "Ancient tablet":"https://www.curseofaros.wiki/wiki/Ancient_Tablet",
      "Sugar Brew":"https://www.curseofaros.wiki/wiki/Sugar_Brew",
      "Party Hat":"https://www.curseofaros.wiki/wiki/Party_Hat_1",
      "Santa Hat":"https://www.curseofaros.wiki/wiki/Santa_Hat",
      "Jingle Top":"https://www.curseofaros.wiki/wiki/Jingle_Top",
      "Jingle Pants":"https://www.curseofaros.wiki/wiki/Jingle_Pants",
      "Candy Cane":"https://www.curseofaros.wiki/wiki/Candy_Cane",
      "Easter Egg":"https://www.curseofaros.wiki/wiki/Easter_Egg",
      "Bag of Tricks":"https://www.curseofaros.wiki/wiki/Bag_of_Tricks",
      "Bag of Sweets":"https://www.curseofaros.wiki/wiki/Bag_of_Sweets",
      "Magic Bag of Treats":"https://www.curseofaros.wiki/wiki/Magic_Bag_of_Treats",
      "Pumpking Helm":"https://www.curseofaros.wiki/wiki/Pumpking_Helm",
      "Pumpking Sword":"https://www.curseofaros.wiki/wiki/Pumpking_Sword",
      "Pumpking Shield":"https://www.curseofaros.wiki/wiki/Pumpking_Shield",
      "Party Hat 2":"https://www.curseofaros.wiki/wiki/Party_Hat_2",
      "Jester Hat":"https://www.curseofaros.wiki/wiki/Jester_Hat",
      "Based Santa Hat":"https://www.curseofaros.wiki/wiki/Based_Santa_Hat",
      "Scrooge Hat":"https://www.curseofaros.wiki/wiki/Scoorage_hat",
      "Scrooge Shirt":"https://www.curseofaros.wiki/wiki/Scoorage_Shirt",
      "Pack of Snow":"https://www.curseofaros.wiki/wiki/Pack_of_Snow",
      "Xmas Tree Sword":"https://www.curseofaros.wiki/wiki/Xmas_Tree_Sword",
      "Candy Cane Staff":"https://www.curseofaros.wiki/wiki/Candy_Cane_Staff",
      "Egg Head":"https://www.curseofaros.wiki/wiki/Egg_Head",
      "Hand of Baphomet":"https://www.curseofaros.wiki/wiki/Hand_of_Baphomet",
      "Head of Baphomet":"https://www.curseofaros.wiki/wiki/Head_of_Baphomet",
      "Pumpkin Zombie Hat":"https://www.curseofaros.wiki/wiki/Pumpkin_Zombie_Head",
      "Party Hat 3":"https://www.curseofaros.wiki/wiki/Party_Hat_3",
      "Classy Jacket":"https://www.curseofaros.wiki/wiki/Classy_Jacket",
      "Classy Pants":"https://www.curseofaros.wiki/wiki/Classy_Pants",
      "Sparkling Grapejuice":"https://www.curseofaros.wiki/wiki/Sparkling_Grapejuice",
      "Antlers":"https://www.curseofaros.wiki/wiki/Antlers",
      "Christmas Tree Hat":"https://www.curseofaros.wiki/wiki/Christmas_Tree_Hat",
      "Jingle Hat":"https://www.curseofaros.wiki/wiki/Jingle_Hat",
      "White Present":"https://www.curseofaros.wiki/wiki/White_Present",
      "Red Present":"https://www.curseofaros.wiki/wiki/Red_Present",
      "Gold Present":"https://www.curseofaros.wiki/wiki/Gold_Present",
      "Carrot Launcher":"https://www.curseofaros.wiki/wiki/Carrot_Launcher",
      "Carrotproof Helmet":"https://www.curseofaros.wiki/wiki/Carrotproof_Helmet",
      "Carrotproof Vest":"https://www.curseofaros.wiki/wiki/Carrotproof_Vest",
      "Egg Ring":"https://www.curseofaros.wiki/wiki/Egg_Ring",
      "Party Hat 4":"https://www.curseofaros.wiki/wiki/Party_Hat_4",
      "Box of Chocolate":"https://www.curseofaros.wiki/wiki/Box_of_Chocolate",
      "Box of Pralines":"https://www.curseofaros.wiki/wiki/Box_of_Pralines",
      "Loveshot":"https://www.curseofaros.wiki/wiki/Loveshot",
      "Arrow Head":"https://www.curseofaros.wiki/wiki/Arrow_Head",
      "Heartseeker":"https://www.curseofaros.wiki/wiki/Heartseeker",
      "Eternal Love":"https://www.curseofaros.wiki/wiki/Eternal_Love",
      "Lootkin":"https://www.curseofaros.wiki/wiki/Lootkin",
      "Bionic Skull":"https://www.curseofaros.wiki/wiki/Bionic_Skull",
      "Bionic Ribcage":"https://www.curseofaros.wiki/wiki/Bionic_Ribcage",
      "Bionic Limbs":"https://www.curseofaros.wiki/wiki/Bionic_Limbs",
      "Scream Mask":"https://www.curseofaros.wiki/wiki/Scream_Mask",
      "Birthday Cake":"https://www.curseofaros.wiki/wiki/Birthday_Cake",
      "Party Hat 5":"https://www.curseofaros.wiki/wiki/Party_Hat_5",
      "Blue Balloon":"https://www.curseofaros.wiki/wiki/Blue_Ballon",
      "Red Balloon":"https://www.curseofaros.wiki/wiki/Red_Ballon",
      "Yellow Balloon":"https://www.curseofaros.wiki/wiki/Yellow_Ballon",
      "Green Balloon":"https://www.curseofaros.wiki/wiki/Green_Ballon",
      "Bunch of Balloins":"https://www.curseofaros.wiki/wiki/Bunch_of_Ballon%27s",
      "Snowball Ammo":"https://www.curseofaros.wiki/wiki/Snowball_Ammo",
      "Ring of Snow":"https://www.curseofaros.wiki/wiki/Ring_of_Snow",
      "Snowball Launcher":"https://www.curseofaros.wiki/wiki/Snowball_Launcher",
      "Black Santa Hat":"https://www.curseofaros.wiki/wiki/Black_Santa_Hat",
      "Lucky Egg":"https://www.curseofaros.wiki/wiki/Lucky_Egg",
      "Carrot Rocket":"https://www.curseofaros.wiki/wiki/Carrot_Rocket",
      "Bonka's Barrier":"https://www.curseofaros.wiki/wiki/Bonka%27s_Barrier",
      "Eggy Bludgeon":"https://www.curseofaros.wiki/wiki/Eggy_Bludgeon",
      "Wabbit Hat":"https://www.curseofaros.wiki/wiki/Wabbit_Hat",
      "Party Hat 6":"https://www.curseofaros.wiki/wiki/Party_Hat_6",
      "Party Crasher":"https://www.curseofaros.wiki/wiki/Party_Crasher",
      "Smelly Key":"https://www.curseofaros.wiki/wiki/Smelly_Key",
      "Leaky Leek":"https://www.curseofaros.wiki/wiki/Leaky_Leek",
      "Evileek Staff":"https://www.curseofaros.wiki/wiki/Evileek_Staff",
      "Evileek Shield":"https://www.curseofaros.wiki/wiki/Evileek_Shield",
      "Evileek Mask":"https://www.curseofaros.wiki/wiki/Evileek_Mask",
      "Sleekest":"https://www.curseofaros.wiki/wiki/Sleekest",
      "Chicken hLHead":"https://www.curseofaros.wiki/wiki/Chicken_Head",
      "Chicken Wings":"https://www.curseofaros.wiki/wiki/Chicken_Wings",
      "Chicken Feathers":"https://www.curseofaros.wiki/wiki/Chicken_Feathers",
      "Ruby":"https://www.curseofaros.wiki/wiki/Ruby",
      "Sapphire":"https://www.curseofaros.wiki/wiki/Sapphire",
      "Emerald":"https://www.curseofaros.wiki/wiki/Emerald",
      "Arosite":"https://www.curseofaros.wiki/wiki/Arosite",
      "Sandstone Shield":"https://www.curseofaros.wiki/wiki/Sandstone_Shield",
      "Scorpion Shield":"https://www.curseofaros.wiki/wiki/Scorpion_Shield",
      "Deadrock Shield":"https://www.curseofaros.wiki/wiki/Deadrock_Shield",
      "Ancient Shield":"https://www.curseofaros.wiki/wiki/Ancient_Shield",
      "Iron Spade":"https://www.curseofaros.wiki/wiki/Iron_Spade",
      "Crimsteel Spade":"https://www.curseofaros.wiki/wiki/Crimsteel_Spade",
      "Mythan Spade":"https://www.curseofaros.wiki/wiki/Mythan_Spade",
      "Golemite Spade":"https://www.curseofaros.wiki/wiki/Golemite_Spade",
      "Ancient Spade":"https://www.curseofaros.wiki/wiki/Ancient_Spade",
      "Saving Grace":"https://www.curseofaros.wiki/wiki/Saving_Grace",
      "Bat Amulet":"https://www.curseofaros.wiki/wiki/Bat_Amulet",
      "Nature Amulet":"https://www.curseofaros.wiki/wiki/Nature_Amulet",
      "Amulet of Focus":"https://www.curseofaros.wiki/wiki/Amulet_of_Focus",
      "Prospector's Necklace":"https://www.curseofaros.wiki/wiki/Prospector%27s_Necklace",
      "Ruby Necklace":"https://www.curseofaros.wiki/wiki/Ruby_Necklace",
      "Sapphire nLNecklace":"https://www.curseofaros.wiki/wiki/Sapphire_Necklace",
      "Emerald Necklace":"https://www.curseofaros.wiki/wiki/Emerald_Necklace",
      "Arosite Necklace":"https://www.curseofaros.wiki/wiki/Arosite_Necklace",
      "Magnetite Necklace":"https://www.curseofaros.wiki/wiki/Magnetite_Necklace",
      "Battle Necklace":"https://www.curseofaros.wiki/wiki/Battle_Necklace",
      "Scorpion Gauntlets":"https://www.curseofaros.wiki/wiki/Scorpion_Gauntlets",
      "Raptor gloves":"https://www.curseofaros.wiki/wiki/Raptor_Gloves",
      "Desert Raptor Gloves":"https://www.curseofaros.wiki/wiki/Desert_Raptor_Gloves",
      "Ice Raptor Gloves":"https://www.curseofaros.wiki/wiki/Ice_Raptor_Gloves",
      "Cactus Gloves":"https://www.curseofaros.wiki/wiki/Cactus_Gloves",
      "Frozen Skull":"https://www.curseofaros.wiki/wiki/Frozen_Skull",
      "Icy Right Half":"https://www.curseofaros.wiki/wiki/Icy_Right_Half",
      "Icy Left Half":"https://www.curseofaros.wiki/wiki/Icy_Left_Half",
      "Ring of Treasure":"https://www.curseofaros.wiki/wiki/Ring_of_Treasure",
      "Nature Ring":"https://www.curseofaros.wiki/wiki/Nature_Ring",
      "Bat Ring":"https://www.curseofaros.wiki/wiki/Bat_Ring",
      "Ring of Might":"https://www.curseofaros.wiki/wiki/Ring_of_Might",
      "Infernal Ring":"https://www.curseofaros.wiki/wiki/Infernal_Ring",
      "Cactus Ring":"https://www.curseofaros.wiki/wiki/Cactus_Ring",
      "Snake Charm":"https://www.curseofaros.wiki/wiki/Snake_Charm",
      "Infernal Hammer":"https://www.curseofaros.wiki/wiki/Infernal_Hammer",
      "Ring of Violation":"https://www.curseofaros.wiki/wiki/Ring_of_Violation",
      "Pendant of Serenity":"https://www.curseofaros.wiki/wiki/Pendant_of_Serenity",
      "Inferno Tome":"https://www.curseofaros.wiki/wiki/Inferno_Tome",
      "Consume Tome":"https://www.curseofaros.wiki/wiki/Consume_Tome",
      "Blizzard Tome":"https://www.curseofaros.wiki/wiki/Blizzard_Tome",
      "Torture Tome":"https://www.curseofaros.wiki/wiki/Torture_Tome",
      "Lollipop":"https://www.curseofaros.wiki/wiki/Lollipop",
      "Nydarax Teleport Scrool":"https://www.curseofaros.wiki/wiki/Nydarax_Teleport_Scrool",
      "Red Key":"https://www.curseofaros.wiki/wiki/Red_Key",
      "Blue Key":"https://www.curseofaros.wiki/wiki/Blue_Key",
      "Green Key":"https://www.curseofaros.wiki/wiki/Green_Key",
      "Mysterious Artifact":"https://www.curseofaros.wiki/wiki/Mysterious_Artifact",
      "Key to 'Disdain'":"https://www.curseofaros.wiki/wiki/Key_to_%27Disdain%27",
      "Key to 'Rage'":"https://www.curseofaros.wiki/wiki/Key_to_%27Rage%27",
      "Key to 'Torment'":"https://www.curseofaros.wiki/wiki/Key_to_%27Torment%27",
      "Key to 'Corruption'":"https://www.curseofaros.wiki/wiki/Key_to_%27Corruption%27",
      "Magnetite":"https://www.curseofaros.wiki/wiki/Magnetite",
      "Ankh Key":"https://www.curseofaros.wiki/wiki/Ankh_Key",
      "Portal Charge ":"https://www.curseofaros.wiki/wiki/Portal_charge",
    };

    // --- yardımcı fonksiyonlar ---
    function normalizeStr(s) {
      // küçük harfe çevir, noktalama kaldır, fazla boşluğu temizle
      return (s || '').toLowerCase().replace(/\s*price.*$/i, '') // fiyat ve sonrası kaldır (ek güvenlik)
                     .replace(/[^a-z0-9\s]/g, '')
                     .replace(/\s+/g, ' ')
                     .trim();
    }

    function splitNameAndPrice(item) {
      // "Pink salt Price : 7k each" => { name: "Pink salt", price: "Price : 7k each" }
      const m = item.match(/(.*?)(\s*price\b.*)$/i);
      if (m) {
        return { name: m[1].trim(), price: m[2].trim() };
      }
      // fiyat belirtisi yoksa tüm satırı isim olarak kullan
      return { name: item.trim(), price: '' };
    }

    function findLinkForItem(item) {
      const { name } = splitNameAndPrice(item);
      const normItem = normalizeStr(name);
      if (!normItem) return null;

      // 1) tam eşleme dene
      for (const key in itemLinks) {
        const nk = normalizeStr(key);
        if (nk === normItem) return itemLinks[key];
      }

      // 2) küçük farklarda içerme ile eşlemeye çalış (yedek)
      for (const key in itemLinks) {
        const nk = normalizeStr(key);
        if (nk.length >= 3 && normItem.length >= 3) {
          if (nk.includes(normItem) || normItem.includes(nk)) return itemLinks[key];
        }
      }

      return null;
    }

    function renderHome() {
      content.innerHTML = `
        <div class="home">
          <h2>Welcome!</h2>
          <h3><span class="red">Disclaimer : We are not responsible for any discrepancies in prices!</span></h3>
          <h4>This server created in 01/09/2025 for help Curse of Aros community</h4>
          <h4>There you are can search prices of items</h4>
          <h4>Note : Search full name of items for get good result, tap item name for get information about item and and we will update prices every month.</h4>
          <h4><span class="eblue">Join my discord server for give suggestions or help me update prices</span> </h4>
          <a class="btn-discord" href="https://discord.gg/QAZEkeYc6w" target="_blank" rel="noopener">Discord</a>
        </div>
      `;
    }

    // Menü aç/kapa
    burger.addEventListener('click', () => {
      menu.style.display = menu.style.display === 'flex' ? 'none' : 'flex';
    });

    // Menü dışında tıklanınca kapanma
    document.addEventListener('click', (e) => {
      if (!menu.contains(e.target) && !burger.contains(e.target)) {
        menu.style.display = 'none';
      }
    });

    // Menüden kategori seçimi
    document.querySelectorAll('.menu a').forEach(link => {
      link.addEventListener('click', (e) => {
        e.preventDefault();
        const section = link.getAttribute('data-section');
        content.innerHTML = "";

        if (section === "home") {
          renderHome();
        } else if (items[section]) {
          items[section].forEach(item => {
            const div = document.createElement('div');
            div.className = 'item';

            // isim / fiyat ayır, link bul
            const { name, price } = splitNameAndPrice(item);
            const linkUrl = findLinkForItem(item);

            if (linkUrl) {
              const a = document.createElement('a');
              a.href = linkUrl;
              a.textContent = name;
              a.target = "_blank";
              a.style.color = "white";
              a.style.textDecoration = "none";
              div.appendChild(a);
              if (price) {
                div.appendChild(document.createTextNode(' ' + price));
              }
            } else {
              // link yoksa tüm satırı aynen yaz
              div.textContent = item;
            }

            content.appendChild(div);
          });
        }

        menu.style.display = 'none';
      });
    });

    // Arama motoru
    search.addEventListener('input', () => {
      const query = search.value.toLowerCase().trim();
      content.innerHTML = "";
      let found = false;

      if (!query) {
        renderHome(); // boşken ana sayfayı göster
        return;
      }

      Object.values(items).forEach(sectionItems => {
        sectionItems.forEach(item => {
          if (item.toLowerCase().includes(query)) {
            const div = document.createElement('div');
            div.className = 'item';

            const { name, price } = splitNameAndPrice(item);
            const linkUrl = findLinkForItem(item);

            if (linkUrl) {
              const a = document.createElement('a');
              a.href = linkUrl;
              a.textContent = name;
              a.target = "_blank";
              a.style.color = "white";
              a.style.textDecoration = "none";
              div.appendChild(a);
              if (price) div.appendChild(document.createTextNode(' ' + price));
            } else {
              div.textContent = item;
            }

            content.appendChild(div);
            found = true;
          }
        });
      });

      if (!found) {
        content.innerHTML = "<p>No items found.</p>";
      }
    });

    // Sayfa açılınca ana sayfayı göster
    renderHome();
  </script>
</body>
</html>
