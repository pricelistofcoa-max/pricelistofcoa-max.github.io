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
  </style>
</head>
<body>
  <header>
    <div>COA PRICE LIST</div>
    <button class="burger">☰</button>
    <div class="menu" id="burgerMenu">
      <a href="#" data-section="home">Home</a>
      <a href="#" data-section="ores">Ores</a>
      <a href="#" data-section="bars">Bars</a>
      <a href="#" data-section="logs">Logs</a>
      <a href="#" data-section="relics">Relics</a>
      <a href="#" data-section="fishes">Fishes</a>
      <a href="#" data-section="spellbinding">Spellbinding</a>
      <a href="#" data-section="alchemy">Alchemy</a>
      <a href="#" data-section="potions">Potions</a>
      <a href="#" data-section="armors">Armors</a>
      <a href="#" data-section="weapons">Weapons</a>
      <a href="#" data-section="tools">Tools</a>
      <a href="#" data-section="bossparts">Boss Parts</a>
      <a href="#" data-section="eventitems">Event Items</a>
      <a href="#" data-section="others">Others</a>
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
      ores: ["Copper Ore","Tin ore","Iron ore","Salt Price : 4k each","Coal Price : 3.5k each","Crimstell ore","Silver ore","Gold ore","Pink salt Price : 7k each","Mythan ore Price : 6k each","Sandstone Price : 10k each","Cobalt ore Price : 10k each","Varaxium Price : 12k each","Black salt Price : 9k each","Magic ore Price : 4k each"],
      bars: ["Copper Bar","Iron bar","Steel bar","Crimsteel bar","Silver bar","Gold nugget","Gold bar Price : 700k each","Mythan bar Price : 110k each","Cobalt bar Price : 130k each","Varax bar Price : 160k each ","Magic bar Price : 55k each"],
      logs: ["Pine Log Price : 1k each","Dead log Price : 2.5k each","Birch log Price : 3k each","Applewood Price : 2.5k each","Willow log Price : 5k each","Oak log Price : 4-5k each","Chestnut log Price : 7-8k each","Maple log Price : 6-8k each","Olive log Price : 10.5k each","Stinkwood Price : 8-9k each","Magic log Price : 2.3k each","Palmwood Price : 4k each","Pearwood Price : 6-7k each","Limewood Price : 5k each"],
      relics: ["Accuracy relic Price : 3k each","Guarding Relic Price : 3.5k each","Healing relic Price : 4k each","Wealth relic Price : 4k each","Power relic Price : 6k each","Nature relic Price : 5.5k each","Fire relic Price : 8k each","Damage relic Price : 7k each","Leeching relic Price : 6k each","Experience relic Price : 11k each","Wisdom relic","Ice relic Price : 7k each","Cursed relic Price : 3k each","Efficiency relic Price : 5k each","Affliction relic Price : 5k each"],
      fishes: ["Anchovies","Gold Fish","Mackerel","Squid","Sardine","Eel","Anglerfish","Trout","Jellyfish","Bass","Herringbone","Tuna","Lobster","Sea turtle","Manta ray","Shark","Orca","Giant squid","Earthworm","Iceworm","Corpseworm","Toxicworm","Sandworm","Beetle","Grasshopper","Wasp","Scallop"],
      spellbinding: ["Book Price: 2k each","Magic essence Price: 600 each"],
      alchemy: ["Bat eye","Pink gelatin","Fishing spider eye","Brown mushroom","Forest spider eye","Cow skull","Forest bat eye","Frozen gelatin","Snow core","Sapling leaf","Ice spider eye","Cave spider eye","Skeletal bat eye","Sapphire scarab leg","Cave bat eye","Envenomed blood","Raptor claw","Ruby scarab leg","Forest fiend eye","Desert raptor claw","Rock fiend eye","Hornet antena","Luminant gelatin","Juvenile eye","Ancient bat eye","Ice raptor claw","Spectral flintstone","Arocite scarab leg","Shadow flintstone","Phantom flintstone","Spectral fiend eye","Phantom fiend eye","Magnetite scarab leg","Corrupted eye","Golemite bat eye","Golemite fiend eye","Tormented eye","Disdain Eye","Baby dragon spine","Ragefull eye"],
      potions:["Potion","Mining potion","Woodcutting potion","Fishing potion","Smithing potion","Crafting potion","Cooking potion","Spellbinding potion","Taskmaster's brew","Prospector's brew","Lumberjacks ale","Blacksmith's stout","Artisan's syrup","Angler's elixir","Chef's kiss","Imbuer's wine","Spellpower potion","Concentrated elixir","Divine clarity","Titan's strength","Duelist's draft","Stonebound salve","Backlash balm","Berserker potion","Arcanist's wrath","Forsworn focus","Antidote","Frostskin potion","Arctic potion","Scavenger's balm","Vampirism potion","Assassin's tonic","Auric bloom","Mirrorback brew","Golem's power","Guardian's bulwark","Quietus","Midas brew","Featherwalk potion","Sanguiene oath","Dance of the Undead","Gilded transmutation","Cloudwalk potion","Distilled extract","Provocation potion","Strigoi's convenant","Death's rally"],
      armors: ["Cobalt armor","Varax armor","Glacial armor","Deadrock armor","Spectral armor","Phantom armor","Nightspoon armor"],
      weapons: ["Sharper mythan sword","Cobalt sword","Chaotic mythan sword","Varaxite sword","Glacial blade","Nature's blade","Spectral sword","Phantom sword","Ancient scimitar","Fire staff","Ice staff","Nature staff","Cursed staff","Elder fire staff","Elder ice staff","Elder nature staff","Elder cursed staff","Nightspoon staff"],
      tools: ["Mythan axe","Mythan pickaxe","Mythan rod","Mythan secateurs","Cobalt axe","Cobalt pickaxe","Cobalt rod","Cobalt secateurs","Varaxite axe","Varaxite pickaxe","Varaxite rod","Varaxite secateurs","Magic axe","Magic pickaxe","Magic rod","Byromera secateurs","Ancient axe","Ancient pickaxe","Ancient rod"],
      bossparts: ["Balance fragment","Golemite slab Price : 3m each","Golemite shard Price : 4m each","Golemite eye Price : 2m each","Golemite orb Price : 3m each","Golemite artifact Price : 1.5m each","Dragon scale Price : 15k each","Dragon eye Price : 11m each","Dragon claw Price : 16m each","Dragon horn Price : 2m each","Slivers of rage Price : 6m/100 each","Slivers of corruption Price : 8.5m/100 each","Slivers of disdain Price : 8m/100 each","Slivers of torment Price : 8m/100 each","Nydarax leg Price : 48m each","Nydarax eye Price : 2m each","Gold key","Mummy bandage","Mummy soul","Ancient tablet Price : 5k each"],
      eventitems: ["Sugar brew","Party hat 1","Santa hat","Jingle top","Jingle pants","Candy cane","Easter egg","Bag of tricks","Bag of sweets","Magic bag of treats","Pumpking helm","Pumpking sword","Pumpking shield","Party hat 2","Jester hat","Based santa hat","Scoorage hat","Scoorage shirt","Pack of snow","Xmas tree sword","Candy cane staff","Egg head","Hand of baphomet","Head of baphomet","Pumpkin zombie hat","Party hat 3","Callsy jacket","Classy pants","Sparkling grapejuice","Antlers","Christmas tree hat","Jingle hat","White present","Red present","Gold present","Carrot launcher","Carrotproof helmet","Carrotproof vest","Egg ring","Party hat 4","Box of chocolate","Box of pralines","Loveshot","Arrow head","Heartseeker","Eternal love","Lootkin","Bionic skull","Bionic ribcage","Bionic limbs","Scream mask","Birthday cake","Party hat 5","Blue ballon","Red ballon","Yellow ballon","Green ballon","Bunch of ballons","Snowball ammo","Ring of snow","Snowball launcher","Black santa hat","Lucky egg","Carrot rocket","Bonka's barrier","Eggy bludgeon","Wabbit hat","Party hat 6","Party crasher","Smelly key","Leaky leek","Evileek staff","Evileek shield","Evileek mask","Sleekest","Chicken head","Chicken wings","Chicken feathers"
    ],
      others: ["Ruby","Sapphire","Emerald","Arosite","Sandstone shield","Scorpion shield","Deadrock shield","Ancient shield","Iron spade","Crimsteel spade","Mythan spade","Golemite spade","Ancient spade","Saving grace","Bat amulet","Nature amulet","Amulet of focus","Porspector's necklace","Ruby necklace","Sapphire necklace","Emerald necklace","Arosite necklace","Magnetite necklace","Battle necklace","Scorpion gauntlets","Raptor gloves","Desert raptor gloves","Ice raptor gloves","Cactus gloves","Frozen skull","Icy right half","Icy left half","Ring of treasure","Nature ring","Bat ring","Ring of might","Infernal ring","Cactus ring","Snake charm","Infernal hammer","Ring of violation","Pendant of serenity","Inferno tome","Consume tome","Blizzard tome","Torture tome","Lolipop","Nydarax teleport scrool","Red key","Blue key","Green key","Mysterious artifact","Disdain key","Ragefull key","Tormented key","Corrupted key",]
    };

    // --- Ores için yönlendirme linkleri ---
    const itemLinks = {
      "copper ore": "https://www.curseofaros.wiki/wiki/Copper_Ore",
      "tin ore": "https://www.curseofaros.wiki/wiki/Tin_Ore",
      "iron ore": "https://www.curseofaros.wiki/wiki/Iron_Ore",
      "salt": "https://www.curseofaros.wiki/wiki/Salt",
      "coal": "https://www.curseofaros.wiki/wiki/Coal",
      "crimstell ore": "https://www.curseofaros.wiki/wiki/Crimsteel_Ore",
      "silver ore": "https://www.curseofaros.wiki/wiki/Silver_Ore",
      "gold ore": "https://www.curseofaros.wiki/wiki/Gold_Ore",
      "pink salt": "https://www.curseofaros.wiki/wiki/Pink_Salt",
      "mythan ore": "https://www.curseofaros.wiki/wiki/Mythan_Ore",
      "sandstone": "https://www.curseofaros.wiki/wiki/Sandstone","cobalt ore": "https://www.curseofaros.wiki/wiki/Cobalt_Ore",
      "varaxium": "https://www.curseofaros.wiki/wiki/Varaxium",
      "black salt": "https://www.curseofaros.wiki/wiki/Black_Salt",
      "magic ore": "https://www.curseofaros.wiki/wiki/Magic_Ore",
      "copper bar": "https://www.curseofaros.wiki/wiki/Bronze_Bar",
      "iron bar":"https://www.curseofaros.wiki/wiki/Iron_Bar",
      "steel bar":"https://www.curseofaros.wiki/wiki/Steel_Bar",
      "crimsteel bar":"https://www.curseofaros.wiki/wiki/Crimsteel_Bar",
      "silver bar":"https://www.curseofaros.wiki/wiki/Silver_Bar",
      "gold nugget":"https://www.curseofaros.wiki/wiki/Gold_Nugget",
      "gold bar":"https://www.curseofaros.wiki/wiki/Gold_Bar",
      "mythan bar":"https://www.curseofaros.wiki/wiki/Mythan_Bar",
      "cobalt bar":"https://www.curseofaros.wiki/wiki/Cobalt_Bar",
      "varax bar":"https://www.curseofaros.wiki/wiki/Varaxite_Bar",
      "magic bar":"https://www.curseofaros.wiki/wiki/Magic_Bar",
      "pine log":"https://www.curseofaros.wiki/wiki/Pine_Logs",
      "dead log":"https://www.curseofaros.wiki/wiki/Dead_Logs",
      "birch log":"https://www.curseofaros.wiki/wiki/Birch_Logs",
      "applewood":"https://www.curseofaros.wiki/wiki/Applewood",
      "willow log":"https://www.curseofaros.wiki/wiki/Willow_Logs",
      "oak log":"https://www.curseofaros.wiki/wiki/Oak_Logs",
      "chestnut log":"https://www.curseofaros.wiki/wiki/Chestnut_Logs",
      "maple log":"https://www.curseofaros.wiki/wiki/Maple_Logs",
      "olive log":"https://www.curseofaros.wiki/wiki/Olive_Logs",
      "stinkwood":"https://www.curseofaros.wiki/wiki/Stinkwood",
      "magic log":"https://www.curseofaros.wiki/wiki/Magic_Log",
      "palmwood":"https://www.curseofaros.wiki/wiki/Palm_Wood",
      "pearwood":"https://www.curseofaros.wiki/wiki/Pearwood",
      "limewood":"https://www.curseofaros.wiki/wiki/Lime_Wood",
      "accuracy relic":"https://www.curseofaros.wiki/wiki/Relic_of_Accuracy",
      "guarding relic":"https://www.curseofaros.wiki/wiki/Relic_of_Guarding",
      "healing relic":"https://www.curseofaros.wiki/wiki/Relic_of_Healing",
      "wealth relic":"https://www.curseofaros.wiki/wiki/Relic_of_Wealth",
      "power relic":"https://www.curseofaros.wiki/wiki/Relic_of_Power",
      "nature relic":"https://www.curseofaros.wiki/wiki/Relic_of_Nature",
      "fire relic":"https://www.curseofaros.wiki/wiki/Relic_of_Fire",
      "damage relic":"https://www.curseofaros.wiki/wiki/Relic_of_Damage",
      "experience relic":"https://www.curseofaros.wiki/wiki/Relic_of_Experience",
      "leeching relic":"https://www.curseofaros.wiki/wiki/Relic_of_Leeching",
      "wisdom relic":"https://www.curseofaros.wiki/wiki/Relic_of_Wisdom",
      "ice relic":"https://www.curseofaros.wiki/wiki/Ice_Relic",
      "cursed relic":"https://www.curseofaros.wiki/wiki/Cursed_Relic",
      "efficiency relic":"https://www.curseofaros.wiki/wiki/Relic_of_Efficiency",
      "affliction relic":"https://www.curseofaros.wiki/wiki/Relic_of_Affliction",
      "anchovies":"https://www.curseofaros.wiki/wiki/Anchovies",
      "gold fish":"https://www.curseofaros.wiki/wiki/Goldfish",
      "mackerel":"https://www.curseofaros.wiki/wiki/Mackerel",
      "squid":"https://www.curseofaros.wiki/wiki/Squid",
      "sardine":"https://www.curseofaros.wiki/wiki/Sardine",
      "eel":"https://www.curseofaros.wiki/wiki/Eel",
      "anglerfish":"https://www.curseofaros.wiki/wiki/Anglerfish",
      "trout":"https://www.curseofaros.wiki/wiki/Trout",
      "jellyfish":"https://www.curseofaros.wiki/wiki/Jellyfish",
      "bass":"https://www.curseofaros.wiki/wiki/Bass",
      "herringbone":"https://www.curseofaros.wiki/wiki/Herringbone",
      "tuna":"https://www.curseofaros.wiki/wiki/Tuna",
      "lobster":"https://www.curseofaros.wiki/wiki/Lobster",
      "sea turtle":"https://www.curseofaros.wiki/wiki/Sea_Turtle",
      "manta ray":"https://www.curseofaros.wiki/wiki/Manta_Ray",
      "shark":"https://www.curseofaros.wiki/wiki/Shark",
      "orca":"https://www.curseofaros.wiki/wiki/Orca",
      "giant squid":"https://www.curseofaros.wiki/wiki/Giant_Squid",
      "earthworm":"https://www.curseofaros.wiki/wiki/Earthworm",
      "iceworm":"https://www.curseofaros.wiki/wiki/Iceworm",
      "corpseworm":"https://www.curseofaros.wiki/wiki/Corpseworm",
      "toxicworm":"https://www.curseofaros.wiki/wiki/Toxic_Worm",
      "sandworm":"https://www.curseofaros.wiki/wiki/Sandworm",
      "beetle":"https://www.curseofaros.wiki/wiki/Beetle",
      "grasshopper":"https://www.curseofaros.wiki/wiki/Grasshopper",
      "wasp":"https://www.curseofaros.wiki/wiki/Wasp",
      "scallop":"https://www.curseofaros.wiki/wiki/Scallop",
      "book":"https://www.curseofaros.wiki/wiki/Book",
      "magic essence":"https://www.curseofaros.wiki/wiki/Magic_Essence",
      "bat eye":"https://www.curseofaros.wiki/wiki/Bat_Eye",
      "pink gelatin":"https://www.curseofaros.wiki/wiki/Pink_Gelatin",
      "fishing spider eye":"https://www.curseofaros.wiki/wiki/Fishing_Spider_Eye",
      "brown mushroom":"https://www.curseofaros.wiki/wiki/Brown_Mushroom",
      "forest spider eye":"https://www.curseofaros.wiki/wiki/Forest_Spider_Eye",
      "cow skull":"https://www.curseofaros.wiki/wiki/Cow_Skull",
      "forest bat eye":"https://www.curseofaros.wiki/wiki/Forest_Bat_Eye",
      "frozen gelatin":"https://www.curseofaros.wiki/wiki/Frozen_Gelatin",
      "snow core":"https://www.curseofaros.wiki/wiki/Snow_Core",
      "sapling leaf":"https://www.curseofaros.wiki/wiki/Sapling_Leaf",
      "ice spider eye":"https://www.curseofaros.wiki/wiki/Ice_Spider_Eye",
      "cave spider eye":"https://www.curseofaros.wiki/wiki/Cave_Spider_Eye",
      "skeletal bat eye":"https://www.curseofaros.wiki/wiki/Skeletal_Bat_Eye",
      "sapphire scarab leg":"https://www.curseofaros.wiki/wiki/Sapphire_Scarab_Leg",
      "cave bat eye":"https://www.curseofaros.wiki/wiki/Cave_Bat_Eye",
      "envenomed blood":"https://www.curseofaros.wiki/wiki/Envenomed_Blood",
      "raptor claw":"https://www.curseofaros.wiki/wiki/Raptor_Claw",
      "ruby scarab leg":"https://www.curseofaros.wiki/wiki/Ruby_Scarab_Leg",
      "forest fiend eye":"https://www.curseofaros.wiki/wiki/Forest_Fiend_Eye",
      "desert raptor claw":"https://www.curseofaros.wiki/wiki/Desert_Raptor_Claw",
      "rock fiend eye":"https://www.curseofaros.wiki/wiki/Rock_Fiend_Eye",
      "hornet antena":"https://www.curseofaros.wiki/wiki/Hornet_Antenna",
      "luminant gelatin":"https://www.curseofaros.wiki/wiki/Luminant_Gelatin",
      "juvenile eye":"https://www.curseofaros.wiki/wiki/Juvenile_Eye",
      "ancient bat eye":"https://www.curseofaros.wiki/wiki/Ancient_Bat_Eye",
      "ice raptor claw":"https://www.curseofaros.wiki/wiki/Ice_Raptor_Claw",
      "spectral flintstone":"https://www.curseofaros.wiki/wiki/Spectral_Flintstone",
      "arocite scarab leg":"https://www.curseofaros.wiki/wiki/Arosite_Scarab_Leg",
      "shadow flintstone":"https://www.curseofaros.wiki/wiki/Shadow_Flintstone",
      "phantom flintstone":"https://www.curseofaros.wiki/wiki/Phantom_Flintstone",
      "spectral fiend eye":"https://www.curseofaros.wiki/wiki/Spectral_Fiend_Eye",
      "phantom fiend eye":"https://www.curseofaros.wiki/wiki/Phantom_Fiend_Eye",
      "magnetite scarab leg":"https://www.curseofaros.wiki/wiki/Magnetite_Scarab_Leg",
      "corrupted eye":"https://www.curseofaros.wiki/wiki/Corrupted_Eye",
      "golemite bat eye":"https://www.curseofaros.wiki/wiki/Golemite_Bat_Eye",
      "golemite fiend eye":"https://www.curseofaros.wiki/wiki/Golemite_Fiend_Eye",
      "tormented eye":"https://www.curseofaros.wiki/wiki/Tormented_Eye",
      "disdain Eye":"https://www.curseofaros.wiki/wiki/Disdained_Eye",
      "baby dragon spine":"https://www.curseofaros.wiki/wiki/Baby_Dragon_Spine",
      "ragefull eye":"https://www.curseofaros.wiki/wiki/Rageful_Eye",
      "potion":"https://www.curseofaros.wiki/wiki/Potion",
      "mining potion":"https://www.curseofaros.wiki/wiki/Mining_Potion",
      "woodcutting potion":"https://www.curseofaros.wiki/wiki/Woodcutting_Potion",
      "fishing potion":"https://www.curseofaros.wiki/wiki/Fishing_Potion",
      "smithing potion":"https://www.curseofaros.wiki/wiki/Smithing_Potion",
      "crafting potion":"https://www.curseofaros.wiki/wiki/Crafting_Potion",
      "cooking potion":"https://www.curseofaros.wiki/wiki/Cooking_Potion",
      "spellbinding potion":"https://www.curseofaros.wiki/wiki/Spellbinding_Potion",
      "taskmaster's brew":"https://www.curseofaros.wiki/wiki/Taskmaster%27s_Brew",
      "prospector's brew":"https://www.curseofaros.wiki/wiki/Prospector%27s_Brew",
      "lumberjacks ale":"https://www.curseofaros.wiki/wiki/Lumberjack%27s_Ale",
      "blacksmith's stout":"https://www.curseofaros.wiki/wiki/Blacksmith%27s_Stout",
      "artisan's syrup":"https://www.curseofaros.wiki/wiki/Artisan%27s_Syrup",
      "angler's elixir":"https://www.curseofaros.wiki/wiki/Angler%27s_Elixir",
      "chef's kiss":"https://www.curseofaros.wiki/wiki/Chef%27s_Kiss",
      "imbuer's wine":"https://www.curseofaros.wiki/wiki/Imbuer%27s_Wine",
      "spellpower potion":"https://www.curseofaros.wiki/wiki/Spellpower_Potion",
      "concentrated elixir":"https://www.curseofaros.wiki/wiki/Concentrated_Elixir",
      "divine clarity":"https://www.curseofaros.wiki/wiki/Divine_Clarity",
      "titan's strength":"https://www.curseofaros.wiki/wiki/Titan%27s_Strength",
      "duelist's draft":"https://www.curseofaros.wiki/wiki/Duelist%27s_Draft",
      "stonebound salve":"https://www.curseofaros.wiki/wiki/Stonebound_Salve",
      "backlash balm":"https://www.curseofaros.wiki/wiki/Backlash_Balm",
      "berserker potion":"https://www.curseofaros.wiki/wiki/Berserker_Potion",
      "arcanist's wrath":"https://www.curseofaros.wiki/wiki/Arcanist%27s_Wrath",
      "forsworn focus":"https://www.curseofaros.wiki/wiki/Forsworn_Focus",
      "antidote":"https://www.curseofaros.wiki/wiki/Antidote",
      "frostskin potion":"https://www.curseofaros.wiki/wiki/Frostskin_Potion",
      "arctic potion":"https://www.curseofaros.wiki/wiki/Arctic_Potion",
      "scavenger's balm":"https://www.curseofaros.wiki/wiki/Scavenger%27s_Balm",
      "vampirism potion":"https://www.curseofaros.wiki/wiki/Vampirism_Potion",
      "assassin's tonic":"https://www.curseofaros.wiki/wiki/Assassin%27s_Tonic",
      "auric bloom":"https://www.curseofaros.wiki/wiki/Auric_Bloom",
      "mirrorback brew":"https://www.curseofaros.wiki/wiki/Mirrorback_Brew",
      "golem's power":"https://www.curseofaros.wiki/wiki/Golem%27s_Power",
      "guardian's bulwark":"https://www.curseofaros.wiki/wiki/Guardian%27s_Bulwark",
      "quietus":"https://www.curseofaros.wiki/wiki/Quietus",
      "midas brew":"https://www.curseofaros.wiki/wiki/Midas_Brew",
      "featherwalk potion":"https://www.curseofaros.wiki/wiki/Featherwalk_Potion",
      "sanguiene oath":"https://www.curseofaros.wiki/wiki/Sanguine_Oath",
      "dance of the Undead":"https://www.curseofaros.wiki/wiki/Dance_of_the_Undead",
      "gilded transmutation":"https://www.curseofaros.wiki/wiki/Gilded_Transmutation",
      "cloudwalk potion":"https://www.curseofaros.wiki/wiki/Cloudwalk_Potion",
      "distilled extract":"https://www.curseofaros.wiki/wiki/Distilled_Extract",
      "provocation potion":"https://www.curseofaros.wiki/wiki/Provocation_Potion",
      "strigoi's convenant":"https://www.curseofaros.wiki/wiki/Strigoi%27s_Convenant",
      "death's rally":"https://www.curseofaros.wiki/wiki/Death%27s_Rally",
      "Cobalt armor":"https://www.curseofaros.wiki/wiki/Melee#Headgear",
      "Varax armor":"https://www.curseofaros.wiki/wiki/Melee#Headgear",
      "Glacial armor":"https://www.curseofaros.wiki/wiki/Melee#Headgear",
      "Deadrock armor":"https://www.curseofaros.wiki/wiki/Melee#Headgear",
      "Spectral armor":"https://www.curseofaros.wiki/wiki/Melee#Headgear",
      "Phantom armor":"https://www.curseofaros.wiki/wiki/Melee#Headgear",
      "Nightspoon armor":"https://www.curseofaros.wiki/wiki/Magic#Headgear",
      "Sharper mythan sword":"https://www.curseofaros.wiki/wiki/Sharper_Mythan_Sword",
      "Cobalt sword":"https://www.curseofaros.wiki/wiki/Cobalt_Sword",
      "Chaotic mythan sword":"https://www.curseofaros.wiki/wiki/Chaotic_Mythan_Sword",
      "Varaxite sword":"https://www.curseofaros.wiki/wiki/Varaxite_Sword",
      "Glacial blade":"https://www.curseofaros.wiki/wiki/Glacial_Blade",
      "Nature's blade":"https://www.curseofaros.wiki/wiki/Nature%27s_Blade",
      "Spectral sword":"https://www.curseofaros.wiki/wiki/Spectral_Sword",
      "Phantom sword":"https://www.curseofaros.wiki/wiki/Phantom_Sword",
      "Ancient scimitar":"https://www.curseofaros.wiki/wiki/Ancient_Scimitar",
      "Fire staff":"https://www.curseofaros.wiki/wiki/Fire_Staff",
      "Ice staff":"https://www.curseofaros.wiki/wiki/Ice_Staff",
      "Nature staff":"https://www.curseofaros.wiki/wiki/Nature_Staff",
      "Cursed staff":"https://www.curseofaros.wiki/wiki/Cursed_Staff",
      "Elder fire staff":"https://www.curseofaros.wiki/wiki/Elder_Fire_Staff",
      "Elder ice staff":"https://www.curseofaros.wiki/wiki/Elder_Ice_Staff",
      "Elder nature staff":"https://www.curseofaros.wiki/wiki/Elder_Nature_Staff",
      "Elder cursed staff":"https://www.curseofaros.wiki/wiki/Elder_Cursed_Staff",
      "Nightspoon staff":"https://www.curseofaros.wiki/wiki/Nightspoon_Staff",
      "Mythan axe":"https://www.curseofaros.wiki/wiki/Mythan_Axe",
      "Mythan pickaxe":"https://www.curseofaros.wiki/wiki/Mythan_Pickaxe",
      "Mythan rod":"https://www.curseofaros.wiki/wiki/Mythan_Rod",
      "Mythan secateurs":"https://www.curseofaros.wiki/wiki/Mythan_Secateurs",
      "Cobalt axe":"https://www.curseofaros.wiki/wiki/Cobalt_Axe",
      "Cobalt pickaxe":"https://www.curseofaros.wiki/wiki/Cobalt_Pickaxe",
      "Cobalt rod":"https://www.curseofaros.wiki/wiki/Cobalt_Rod",
      "Cobalt secateurs":"https://www.curseofaros.wiki/wiki/Cobalt_Secateurs",
      "Varaxite axe":"https://www.curseofaros.wiki/wiki/Varaxite_Axe",
      "Varaxite pickaxe":"https://www.curseofaros.wiki/wiki/Varaxite_Pickaxe",
      "Varaxite rod":"https://www.curseofaros.wiki/wiki/Varaxite_Rod",
      "Varaxite secateurs":"https://www.curseofaros.wiki/wiki/Varaxite_Secateurs",
      "Magic axe":"https://www.curseofaros.wiki/wiki/Magic_Axe",
      "Magic pickaxe":"https://www.curseofaros.wiki/wiki/Magic_Pickaxe",
      "Magic rod":"https://www.curseofaros.wiki/wiki/Magic_Rod",
      "Bryomera secateurs":"https://www.curseofaros.wiki/wiki/Bryomera_Secateurs",
      "Ancient axe":"https://www.curseofaros.wiki/wiki/Ancient_Axe",
      "Ancient pickaxe":"https://www.curseofaros.wiki/wiki/Ancient_Pickaxe",
      "Ancient rod":"https://www.curseofaros.wiki/wiki/Ancient_Rod",
      "Balance fragment":"https://www.curseofaros.wiki/wiki/Balance_Fragment",
      "Golemite slab":"https://www.curseofaros.wiki/wiki/Golemite_Slab",
      "Golemite shard":"https://www.curseofaros.wiki/wiki/Golemite_Shard",
      "Golemite eye":"https://www.curseofaros.wiki/wiki/Golemite_Eye",
      "Golemite orb":"https://www.curseofaros.wiki/wiki/Golemite_Orb",
      "Dragon scale":"https://www.curseofaros.wiki/wiki/Dragon_Scale",
      "Dragon eye":"https://www.curseofaros.wiki/wiki/Dragon_Eye",
      "Dragon claw":"https://www.curseofaros.wiki/wiki/Dragon_Claw",
      "Slivers of rage":"https://www.curseofaros.wiki/wiki/Slivers_of_Rage",
      "Slivers of corruption":"https://www.curseofaros.wiki/wiki/Slivers_of_Corruption",
      "Slivers of disdain":"https://www.curseofaros.wiki/wiki/Slivers_of_Disdain",
      "Slivers of torment":"https://www.curseofaros.wiki/wiki/Slivers_of_Torment",
      "Nydarax leg":"https://www.curseofaros.wiki/wiki/Leg_of_Nydarax",
      "Nydarax eye":"https://www.curseofaros.wiki/wiki/Eye_of_Nydarax",
      "Gold key":"https://www.curseofaros.wiki/wiki/Gold_Key",
      "Mummy bandage":"https://www.curseofaros.wiki/wiki/Mummy_Bandage",
      "Mummy soul":"https://www.curseofaros.wiki/wiki/Mummy_Soul",
      "Ancient tablet":"https://www.curseofaros.wiki/wiki/Ancient_Tablet",
      "Sugar brew":"https://www.curseofaros.wiki/wiki/Sugar_Brew",
      "Party hat 1":"https://www.curseofaros.wiki/wiki/Party_Hat_1",
      "Santa hat":"https://www.curseofaros.wiki/wiki/Santa_Hat",
      "Jingle top":"https://www.curseofaros.wiki/wiki/Jingle_Top",
      "Jingle pants":"https://www.curseofaros.wiki/wiki/Jingle_Pants",
      "Candy cane":"https://www.curseofaros.wiki/wiki/Candy_Cane",
      "Easter egg":"https://www.curseofaros.wiki/wiki/Easter_Egg",
      "Bag of tricks":"https://www.curseofaros.wiki/wiki/Bag_of_Tricks",
      "Bag of sweets":"https://www.curseofaros.wiki/wiki/Bag_of_Sweets",
      "Magic bag of treats":"https://www.curseofaros.wiki/wiki/Magic_Bag_of_Treats",
      "Pumpking helm":"https://www.curseofaros.wiki/wiki/Pumpking_Helm",
      "Pumpking sword":"https://www.curseofaros.wiki/wiki/Pumpking_Sword",
      "Pumpking shield":"https://www.curseofaros.wiki/wiki/Pumpking_Shield",
      "Party hat 2":"https://www.curseofaros.wiki/wiki/Party_Hat_2",
      "Jester hat":"https://www.curseofaros.wiki/wiki/Jester_Hat",
      "Based santa hat":"https://www.curseofaros.wiki/wiki/Based_Santa_Hat",
      "Scoorage hat":"https://www.curseofaros.wiki/wiki/Scoorage_hat",
      "Scoorage shirt":"https://www.curseofaros.wiki/wiki/Scoorage_Shirt",
      "Pack of snow":"https://www.curseofaros.wiki/wiki/Pack_of_Snow",
      "Xmas tree sword":"https://www.curseofaros.wiki/wiki/Xmas_Tree_Sword",
      "Candy cane staff":"https://www.curseofaros.wiki/wiki/Candy_Cane_Staff",
      "Egg head":"https://www.curseofaros.wiki/wiki/Egg_Head",
      "Hand of baphomet":"https://www.curseofaros.wiki/wiki/Hand_of_Baphomet",
      "Head of baphomet":"https://www.curseofaros.wiki/wiki/Head_of_Baphomet",
      "Pumpkin zombie hat":"https://www.curseofaros.wiki/wiki/Pumpkin_Zombie_Head",
      "Party hat 3":"https://www.curseofaros.wiki/wiki/Party_Hat_3",
      "Classy jacket":"https://www.curseofaros.wiki/wiki/Classy_Jacket",
      "Classy pants":"https://www.curseofaros.wiki/wiki/Classy_Pants",
      "Sparkling grapejuice":"https://www.curseofaros.wiki/wiki/Sparkling_Grapejuice",
      "Antlers":"https://www.curseofaros.wiki/wiki/Antlers",
      "Christmas tree hat":"https://www.curseofaros.wiki/wiki/Christmas_Tree_Hat",
      "Jingle hat":"https://www.curseofaros.wiki/wiki/Jingle_Hat",
      "White present":"https://www.curseofaros.wiki/wiki/White_Present",
      "Red present":"https://www.curseofaros.wiki/wiki/Red_Present",
      "Gold present":"https://www.curseofaros.wiki/wiki/Gold_Present",
      "Carrot launcher":"https://www.curseofaros.wiki/wiki/Carrot_Launcher",
      "Carrotproof helmet":"https://www.curseofaros.wiki/wiki/Carrotproof_Helmet",
      "Carrotproof vest":"https://www.curseofaros.wiki/wiki/Carrotproof_Vest",
      "Egg ring":"https://www.curseofaros.wiki/wiki/Egg_Ring",
      "Party hat 4":"https://www.curseofaros.wiki/wiki/Party_Hat_4",
      "Box of chocolate":"https://www.curseofaros.wiki/wiki/Box_of_Chocolate",
      "Box of pralines":"https://www.curseofaros.wiki/wiki/Box_of_Pralines",
      "Loveshot":"https://www.curseofaros.wiki/wiki/Loveshot",
      "Arrow head":"https://www.curseofaros.wiki/wiki/Arrow_Head",
      "Heartseeker":"https://www.curseofaros.wiki/wiki/Heartseeker",
      "Eternal love":"https://www.curseofaros.wiki/wiki/Eternal_Love",
      "Lootkin":"https://www.curseofaros.wiki/wiki/Lootkin",
      "Bionic skull":"https://www.curseofaros.wiki/wiki/Bionic_Skull",
      "Bionic ribcage":"https://www.curseofaros.wiki/wiki/Bionic_Ribcage",
      "Bionic limbs":"https://www.curseofaros.wiki/wiki/Bionic_Limbs",
      "Scream mask":"https://www.curseofaros.wiki/wiki/Scream_Mask",
      "Birthday cake":"https://www.curseofaros.wiki/wiki/Birthday_Cake",
      "Party hat 5":"https://www.curseofaros.wiki/wiki/Party_Hat_5",
      "Blue ballon":"https://www.curseofaros.wiki/wiki/Blue_Ballon",
      "Red ballon":"https://www.curseofaros.wiki/wiki/Red_Ballon",
      "Yellow ballon":"https://www.curseofaros.wiki/wiki/Yellow_Ballon",
      "Green ballon":"https://www.curseofaros.wiki/wiki/Green_Ballon",
      "Bunch of ballons":"https://www.curseofaros.wiki/wiki/Bunch_of_Ballon%27s",
      "Snowball ammo":"https://www.curseofaros.wiki/wiki/Snowball_Ammo",
      "Ring of snow":"https://www.curseofaros.wiki/wiki/Ring_of_Snow",
      "Snowball launcher":"https://www.curseofaros.wiki/wiki/Snowball_Launcher",
      "Black santa hat":"https://www.curseofaros.wiki/wiki/Black_Santa_Hat",
      "Lucky egg":"https://www.curseofaros.wiki/wiki/Lucky_Egg",
      "Carrot rocket":"https://www.curseofaros.wiki/wiki/Carrot_Rocket",
      "Bonka's barrier":"https://www.curseofaros.wiki/wiki/Bonka%27s_Barrier",
      "Eggy bludgeon":"https://www.curseofaros.wiki/wiki/Eggy_Bludgeon",
      "Wabbit hat":"https://www.curseofaros.wiki/wiki/Wabbit_Hat",
      "Party hat 6":"https://www.curseofaros.wiki/wiki/Party_Hat_6",
      "Party crasher":"https://www.curseofaros.wiki/wiki/Party_Crasher",
      "Smelly key":"https://www.curseofaros.wiki/wiki/Smelly_Key",
      "Leaky leek":"https://www.curseofaros.wiki/wiki/Leaky_Leek",
      "Evileek staff":"https://www.curseofaros.wiki/wiki/Evileek_Staff",
      "Evileek shield":"https://www.curseofaros.wiki/wiki/Evileek_Shield",
      "Evileek mask":"https://www.curseofaros.wiki/wiki/Evileek_Mask",
      "Sleekest":"https://www.curseofaros.wiki/wiki/Sleekest",
      "Chicken head":"https://www.curseofaros.wiki/wiki/Chicken_Head",
      "Chicken wings":"https://www.curseofaros.wiki/wiki/Chicken_Wings",
      "Chicken feathers":"https://www.curseofaros.wiki/wiki/Chicken_Feathers",
      "Ruby":"https://www.curseofaros.wiki/wiki/Ruby",
      "Sapphire":"https://www.curseofaros.wiki/wiki/Sapphire",
      "Emerald":"https://www.curseofaros.wiki/wiki/Emerald",
      "Arosite":"https://www.curseofaros.wiki/wiki/Arosite",
      "Sandstone shield":"https://www.curseofaros.wiki/wiki/Sandstone_Shield",
      "Scorpion shield":"https://www.curseofaros.wiki/wiki/Scorpion_Shield",
      "Deadrock shield":"https://www.curseofaros.wiki/wiki/Deadrock_Shield",
      "Ancient shield":"https://www.curseofaros.wiki/wiki/Ancient_Shield",
      "Iron spade":"https://www.curseofaros.wiki/wiki/Iron_Spade",
      "Crimsteel spade":"https://www.curseofaros.wiki/wiki/Crimsteel_Spade",
      "Mythan spade":"https://www.curseofaros.wiki/wiki/Mythan_Spade",
      "Golemite spade":"https://www.curseofaros.wiki/wiki/Golemite_Spade",
      "Ancient spade":"https://www.curseofaros.wiki/wiki/Ancient_spade",
      "Saving grace":"https://www.curseofaros.wiki/wiki/Saving_Grace",
      "Bat amulet":"https://www.curseofaros.wiki/wiki/Bat_Amulet",
      "Nature amulet":"https://www.curseofaros.wiki/wiki/Nature_Amulet",
      "Amulet of focus":"https://www.curseofaros.wiki/wiki/Amulet_of_Focus",
      "Porspector's necklace":"https://www.curseofaros.wiki/wiki/Porspector%27s_Necklace",
      "Ruby necklace":"https://www.curseofaros.wiki/wiki/Ruby_Necklace",
      "Sapphire necklace":"https://www.curseofaros.wiki/wiki/Sapphire_Necklace",
      "Emerald necklace":"https://www.curseofaros.wiki/wiki/Emerald_Necklace",
      "Arosite necklace":"https://www.curseofaros.wiki/wiki/Arosite_Necklace",
      "Magnetite necklace":"https://www.curseofaros.wiki/wiki/Magnetite_Necklace",
      "Battle necklace":"https://www.curseofaros.wiki/wiki/Battle_Necklace",
      "Scorpion gauntlets":"https://www.curseofaros.wiki/wiki/Scorpion_Gauntlets",
      "Raptor gloves":"https://www.curseofaros.wiki/wiki/Raptor_Gloves",
      "Desert raptor gloves":"https://www.curseofaros.wiki/wiki/Desert_Raptor_Gloves",
      "Ice raptor gloves":"https://www.curseofaros.wiki/wiki/Ice_Raptor_Gloves",
      "Cactus gloves":"https://www.curseofaros.wiki/wiki/Cactus_Gloves",
      "Frozen skull":"https://www.curseofaros.wiki/wiki/Frozen_Skull",
      "Icy right half":"https://www.curseofaros.wiki/wiki/Icy_Right_Half",
      "Icy left half":"https://www.curseofaros.wiki/wiki/Icy_Left_Half",
      "Ring of treasure":"https://www.curseofaros.wiki/wiki/Ring_of_Treasure",
      "Nature ring":"https://www.curseofaros.wiki/wiki/Nature_Ring",
      "Bat ring":"https://www.curseofaros.wiki/wiki/Bat_Ring",
      "Ring of might":"https://www.curseofaros.wiki/wiki/Ring_of_Might",
      "Infernal ring":"https://www.curseofaros.wiki/wiki/Infernal_Ring",
      "Cactus ring":"https://www.curseofaros.wiki/wiki/Cactus_Ring",
      "Snake charm":"https://www.curseofaros.wiki/wiki/Snake_Charm",
      "Infernal hammer":"https://www.curseofaros.wiki/wiki/Infernal_Hammer",
      "Ring of violation":"https://www.curseofaros.wiki/wiki/Ring_of_Violation",
      "Pendant of serenity":"https://www.curseofaros.wiki/wiki/Pendant_of_Serenity",
      "Inferno tome":"https://www.curseofaros.wiki/wiki/Inferno_Tome",
      "Consume tome":"https://www.curseofaros.wiki/wiki/Consume_Tome",
      "Blizzard tome":"https://www.curseofaros.wiki/wiki/Blizzard_Tome",
      "Torture tome":"https://www.curseofaros.wiki/wiki/Torture_Tome",
      "Lolipop":"https://www.curseofaros.wiki/wiki/Lolipop",
      "Nydarax teleport scrool":"https://www.curseofaros.wiki/wiki/Nydarax_Teleport_Scrool",
      "Red key":"https://www.curseofaros.wiki/wiki/Red_Key",
      "Blue key":"https://www.curseofaros.wiki/wiki/Blue_Key",
      "Green key":"https://www.curseofaros.wiki/wiki/Green_Key",
      "Mysterious artifact":"https://www.curseofaros.wiki/wiki/Mysterious_Artifact",
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
          <h4>This server created in <span class="tblue">01/09/2025</span> by <span class="orange">WnR Hacker</span> for help Curse of Aros community</h4>
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
