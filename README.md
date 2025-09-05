<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>CoA Price List</title>
  <style>
  .yellow {
  color: yellow;
  font-weight: bold;
}
.tblue {
  color: lightblue;
  font-weight: bold;
}
.lightblue {
  color: #00bfff;
  font-weight: bold;
}
.red {
  color: red;
  font-weight: bold;
}
.blue {
  color: blue;
  font-weight: bold;
}
.gray {
  color: gray;
  font-weight: bold;
}
.eblue {
  color: #5865F2;
  font-weight: bold;
}
.lime {
  color: lime;
  font-weight: bold;
}
.orange {
  color: orange;
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
      padding: 10px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      position: relative;
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
      margin-top: 10px;
    }

    .search-container input {
      width: 80%;
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
      Ores: ["Copper Ore","Tin Ore","Iron Ore","Salt Price : 4k each","Coal Price : 3.5k each","Crimstell Ore","Silver Ore","Gold Ore","Pink Salt Price : 7k each","Mythan Ore Price : 6k each","Sandstone Price : 10k each","Cobalt Ore Price : 10k each","Varaxium Price : 12k each","Black Salt Price : 9k each","Magic Ore Price : 4k each"],
      Bars: ["Copper Bar","Iron Bar","Steel Bar","Crimsteel Bar","Silver Bar","Gold Nugget","Gold Bar Price : 700k each","Mythan Bar Price : 110k each","Cobalt Bar Price : 130k each","Varax Bar Price : 160k each ","Magic Bar Price : 55k each"],
      Logs: ["Pine Logs Price : 1k each","Dead Logs Price : 2.5k each","Birch Logs Price : 3k each","Applewood Price : 2.5k each","Willow Logs Price : 5k each","Oak Logs Price : 4-5k each","Chestnut Logs Price : 7-8k each","Maple Logs Price : 6-8k each","Olive Logs Price : 10.5k each","Stinkwood Price : 8-9k each","Magic Log Price : 2.3k each","Palm Wood Price : 4k each","PearWood Price : 6-7k each","Lime Wood Price : 5k each"],
      Relics: ["Relic of Accuracy Price : 3k each","Relic of Guarding Price : 3.5k each","Relic of Healing Price : 4k each","Relic of Wealth Price : 4k each","Relic of Power Price : 6k each","Relic of Nature Price : 5.5k each","Relic of Fire Price : 8k each","Relic of Damage Price : 7k each","Relic of Leeching Price : 6k each","Relic of Experience Price : 11k each","Relic of Wisdom ","Ice relic Price : 7k each","Cursed relic Price : 3k each","Relic of Efficiency Price : 5k each","Relic of Affliction Price : 5k each"],
      Fishes: ["Anchovies","Gold Fish","Mackerel","Squid","Sardine","Eel","Anglerfish","Trout","Jellyfish","Bass","Herringbone","Tuna","Lobster","Sea Turtle","Manta Ray","Shark","Orca","Giant Squid","Earthworm","Iceworm","Corpseworm","Toxicworm","Sandworm","Beetle","Grasshopper","Wasp","Scallop"],
      SpellBinding: ["Book Price: 2k each","Magic Essence Price: 600 each"],
      Alchemy: ["Bat Eye","Pink Gelatin","Fishing Spider Eye","Brown Mushroom","Forest Spider Eye","Cow Skull","Forest Bat Eye","Frozen Gelatin","Snow Core","Sapling Leaf","Ice Spider Eye","Cave Spider Eye","Skeletal Bat Eye","Sapphire Scarab Leg","Cave Bat Eye","Envenomed Blood","Raptor Claw","Ruby Scarab Leg","Forest Fiend Eye","Desert Raptor Claw","Rock Fiend Eye","Hornet Antena","Luminant Gelatin","Juvenile Eye","Ancient Bat Eye","Ice Raptor Claw","Spectral Flintstone","Arocite Scarab Leg","Shadow Flintstone","Phantom Flintstone","Spectral Fiend Eye","Phantom Fiend Eye","Magnetite Scarab Leg","Corrupted Eye","Golemite Bat Eye","Golemite Fiend Eye","Tormented Eye","Disdain Eye","Baby Dragon Spine","Ragefull Eye"],
      Potions:["Potion","Mining Potion","Woodcutting Potion","Fishing Potion","Smithing Potion","Crafting Potion","Cooking Potion","Spellbinding Potion","Taskmaster's Brew","Prospector's Brew","Lumberjack's Ale","Blacksmith's Stout","Artisan's Syrup","Angler's Elixir","Chef's Kiss","Imbuer's Wine","Spellpower Potion","Concentrated Elixir","Divine Clarity","Titan's Strength","Duelist's Draft","Stonebound Salve","Backlash Balm","Berserker Potion","Arcanist's Wrath","Forsworn Focus","Antidote","Frostskin Potion","Arctic Potion","Scavenger's Balm","Vampirism Potion","Assassin's Tonic","Auric Bloom","Mirrorback Brew","Golem's Power","Guardian's Bulwark","Quietus","Midas Brew","Featherwalk Potion","Sanguiene Oath","Dance of the Undead","Gilded Transmutation","Cloudwalk Potion","Distilled Extract","Provocation Potion","Strigoi's Covenant","Death's Rally"],
      Armors: ["Cobalt Armor","Varax Armor","Glacial Armor","Deadrock Armor","Spectral Armor","Phantom Armor","Nightspun Armor"],
      Weapons: ["Sharper Mythan Sword","Cobalt Sword","Chaotic Mythan Sword","Varaxite Sword","Glacial Blade","Nature's Blade","Spectral Sword","Phantom Sword","Ancient Scimitar","Fire Staff","Ice Staff","Nature Staff","Cursed Staff","Elder Fire Staff","Elder Ice Staff","Elder Nature Staff","Elder Cursed Staff","Nightspun Staff"],
      Tools: ["Mythan Axe","Mythan Pickaxe","Mythan Rod","Mythan Secateurs","Cobalt Axe","Cobalt Pickaxe","Cobalt Rod","Cobalt Secateurs","Varaxite Axe","Varaxite Pickaxe","Varaxite Rod","Varaxite Secateurs","Magic Axe","Magic Pickaxe","Magic Rod","Bryomera Secateurs","Ancient Axe","Ancient Pickaxe","Ancient Rod"],
      BossParts: ["Balance fragment","Golemite Slab Price : 3m each","Golemite Shard Price : 4m each","Eye of Golemite Price : 2m each","Golemite Orb Price : 3m each","Golemite Artifact Price : 1.5m each","Dragon Scale Price : 15k each","Dragon Eye Price : 11m each","Dragon Claw Price : 16m each","Dragon Horn Price : 2m each","Slivers of Rage Price : 6m/100 each","Slivers of Corruption Price : 8.5m/100 each","Slivers of Disdain Price : 8m/100 each","Slivers of Torment Price : 8m/100 each","Leg of Nydarax Price : 48m each","Eye of Nydarax Price : 2m each","Gold Key","Mummy Bandage","Mummy Soul","Ancient Tablet Price : 5k each"],
      EventItems: ["Sugar Brew","Party Hat","Santa Hat","Jingle Top","Jingle Pants","Candy Cane","Easter Egg","Bag of Tricks","Bag of Sweets","Magic Bag of Treats","Pumpking Helm","Pumpking Sword","Pumpking Shield","Party Hat 2","Jester Hat","Based Santa Hat","Scrooge Hat","Scrooge Shirt","Pack of Snow","Xmas Tree Sword","Candy Cane Staff","Egg Head","Hand of Baphomet","Head of Baphomet","Pumpkin Zombie Hat","Party Hat 3","Classy Jacket","Classy Pants","Sparkling Grapejuice","Antlers","Christmas Tree Hat","Jingle Hat","White Present","Red Present","Gold Present","Carrot Launcher","Carrotproof Helmet","Carrotproof Vest","Egg Ring","Party Hat 4","Box of Chocolate","Box of Pralines","Loveshot","Arrow Head","Heartseeker","Eternal Love","Lootkin","Bionic Skull","Bionic Ribcage","Bionic Limbs","Scream Mask","Birthday Cake","Party Hat 5","Blue Balloon","Red Balloon","Yellow Balloon","Green Balloon","Bunch of Balloons","Snowball Ammo","Ring of Snow","Snowball Launcher","Black Santa Hat","Lucky Egg","Carrot Rocket","Bonka's Barrier","Eggy Bludgeon","Wabbit Hat","Party Hat 6","Party-Crasher","Smelly Key","Leaky Leek","Evileek Staff","Evileek Shield","Evileek Mask","Sleekest","Chicken Head","Chicken Wings","Chicken Feathers"
    ],
      Others: ["Ruby","Sapphire","Emerald","Arosite","Sandstone Shield","Scorpion Shield","Deadrock Shield","Ancient Shield","Iron Spade","Crimsteel Spade","Mythan Spade","Golemite Spade","Ancient Spade","Saving Grace","Bat Amulet","Nature Amulet","Amulet of Focus","Porspector's Necklace","Ruby Necklace","Sapphire Necklace","Emerald Necklace","Arosite Necklace","Magnetite Necklace","Battle Necklace","Scorpion Gauntlets","Raptor Gloves","Desert Raptor Gloves","Ice Raptor Gloves","Cactus Gloves","Frozen Skull","Icy Right Half","Icy Left Half","Ring of Treasure","Nature Ring","Bat Ring","Ring of Might","Infernal Ring","Cactus Ring","Snake charm","Infernal Hammer","Ring of Violation","Pendant of Serenity","Inferno Tome","Consume Tome","Blizzard Tome","Torture Tome","Lolipop","Nydarax Teleport Scrool","Red Key","Blue Key","Green Key","Mysterious Artifact","Key to 'Disdain'","Key to 'Rage'","Key to 'Torment' ","Key to 'Corruption'",]
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
      "Ancient Spade":"https://www.curseofaros.wiki/wiki/Ancient_spade",
      "Saving Grace":"https://www.curseofaros.wiki/wiki/Saving_Grace",
      "Bat Amulet":"https://www.curseofaros.wiki/wiki/Bat_Amulet",
      "Nature Amulet":"https://www.curseofaros.wiki/wiki/Nature_Amulet",
      "Amulet of Focus":"https://www.curseofaros.wiki/wiki/Amulet_of_Focus",
      "Porspector's Necklace":"https://www.curseofaros.wiki/wiki/Porspector%27s_Necklace",
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
      "Lolipop":"https://www.curseofaros.wiki/wiki/Lolipop",
      "Nydarax Teleport Scrool":"https://www.curseofaros.wiki/wiki/Nydarax_Teleport_Scrool",
      "Red Key":"https://www.curseofaros.wiki/wiki/Red_Key",
      "Blue Key":"https://www.curseofaros.wiki/wiki/Blue_Key",
      "Green Key":"https://www.curseofaros.wiki/wiki/Green_Key",
      "Mysterious Artifact":"https://www.curseofaros.wiki/wiki/Mysterious_Artifact",
      "Key to 'Disdain'":"https://www.curseofaros.wiki/wiki/Key_to_%27Disdain%27",
      "Key to 'Rage'":"https://www.curseofaros.wiki/wiki/Key_to_%27Rage%27",
      "Key to 'Torment'":"https://www.curseofaros.wiki/wiki/Key_to_%27Torment%27",
      "Key to 'Corruption'":"https://www.curseofaros.wiki/wiki/Key_to_%27Corruption%27",
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
          <h3><span class="red">Disclaimer : </span><span class="red">We are not responsible for any discrepancies in prices.</span></h3>
          <h4>This server created in <span class="tblue">01/09/2025</span>for help Curse of Aros community</h4>
          <h4>There you are can search prices of items</h4>
          <h4 class="note"><span class="red">Note</span>: Search full name of items for get good result and tap item name for get information about item</h4>
          <h4><span class="lime">Funny informations about CoA:</span></h4>
          <h4>First <span class="yellow">120 base</span> normal player
 is <span class="lightblue">Saketas</span></h4>
          <h4>First <span class="yellow">120 base</span> <span class="gray">Lone Wolf</span> player
 is <span class="gray">Devotion</span></h4>
          <h4>Most expensive CoA item is Jester hat</h4>
          <a href="https://imgbb.com/"><img src="https://i.ibb.co/v6zrJQrz/Jester-Hat-m.png" alt="Jester-Hat-m" border="0"></a>
          <h4>Most useless CoA Item is Hammer</h4>
          <a href="https://imgbb.com/"><img src="https://i.ibb.co/m5v6S2LK/Hammer-m.png" alt="Hammer-m" border="0"></a>
          <h4>First pet in CoA is Bat pet</h4>
          <a href="https://imgbb.com/"><img src="https://i.ibb.co/qLY4gby3/Pet-bat-sm.gif" alt="Pet-bat-sm" border="0"></a>
          <h4>First item in CoA is Potion
 (I posted first potion design)</h4>
          <a href="https://imgbb.com/"><img src="https://i.ibb.co/ym2qbwkV/20200713113545-Potion-m.png" alt="20200713113545-Potion-m" border="0"></a>
          <h4><span class="eblue">Join my discord server for give suggestions or help me update prices </span></h4>
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
