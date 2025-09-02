<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>CoA Price List</title>
  <style>
  h1, .project-name, .header {
  display: none !important;
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
      logs: ["Pine Log","Dead log","Birch log","Applewood","Willow log","Oak log","Chestnut log","Maple log","Olive log","Stinkwood","Magic log","Palmwood","Pearwood","Limewood"],
      relics: ["Accuracy relic","Guarding Relic","Healing relic","Wealth relic","Power relic","Nature relic","Fire relic","Damage relic","Leeching relic","Experience relic","Wisdom relic","Ice relic","Cursed relic","Efficiency relic","Affliction relic"],
      fishes: ["Anchovies","Gold Fish","Mackerel","Squid","Sardine","Eel","Anglerfish","Trout","Jellyfish","Bass","Herringbone","Tuna","Lobster","Sea turtle","Manta ray","Shark","Orca","Giant squid","Earthworm","Iceworm","Corpseworm","Toxicworm","Sandworm","Beetle","Grasshopper","Wasp","Scallop"],
      spellbinding: ["Book Price: 2k each","Magic essence Price: 600 each"],
      alchemy: ["Bat eye","Pink gelatin","Fishing spider eye","Brown mushroom","Forest spider eye","Cow skull","Forest bat eye","Frozen gelatin","Snow core","Sapling leaf","Ice spider eye","Cave spider eye","Skeletal bat eye","Sapphire scarab leg","Cave bat eye","Envenomed blood","Raptor claw","Ruby scarab leg","Forest fiend eye","Desert raptor claw","Rock fiend eye","Hornet antena","Luminant gelatin","Juvenile eye","Ancient bat eye","Ice raptor claw","Spectral flintstone","Arocite scarab leg","Shadow flintstone","Phantom flintstone","Spectral fiend eye","Phantom fiend eye","Magnetite scarab leg","Corrupted eye","Golemite bat eye","Golemite fiend eye","Tormented eye","Disdain Eye","Baby dragon spine","Ragefull eye"],
      potions:["Potion","Mining potion","Woodcutting potion","Fishing potion","Smithing potion","Crafting potion","Cooking potion","Spellbinding potion","Taskmaster's brew","Prospector's brew","Lumberjacks ale","Blacksmith's stout","Artisan's syrup","Angler's elixir","Chef's kiss","Imbuer's wine","Spellpower potion","Concentrated elixir","Divine clarity","Titan's strength","Duelist's draft","Stonebound salve","Backlash balm","Berserker potion","Arcanist's wrath","Forsworn focus","Antidote","Frostskin potion","Arctic potion","Scavenger's balm","Vampirism potion","Assasin's tonic","Auric bloom","Mirrorback brew","Golem's power","Guardian's bulwark","Quietus","Midas brew","Featherwalk potion","Sanguiene oath","Dance of the Undead","Gilded transmutation","Cloudwalk potion","Distilled extract","Provacation potion","Stigoi's convenant","Death's rally"],
      armors: ["Cobalt armor","Varax armor","Glacial armor","Deadrock armor","Spectral armor","Phantom armor","Nightspoon armor"],
      weapons: ["Sharper mythan sword","Cobalt sword","Chaotic mythan sword","Varaxite sword","Glacial blade","Nature's blade","Spectral sword","Phantom sword","Ancient scimitar","Fire staff","Ice staff","Nature staff","Cursed staff","Elder fire staff","Elder ice staff","Elder nature staff","Elder cursed staff","Nightspoon staff"],
      tools: ["Mythan axe","Mythan pickaxe","Mythan rod","Mythan secateurs","Cobalt axe","Cobalt pickaxe","Cobalt rod","Cobalt secateurs","Varax axe","Varax pickaxe","Varax rod","Varax secateurs","Magic axe","Magic pickaxe","Magic rod","Byromera secateurs","Ancient axe","Ancient pickaxe","Ancient rod"],
      bossparts: ["Balance fragment","Golemite slab","Golemite shard","Golemite eye","Golemite orb","Dragon scale","Dragon eye","Dragon claw","Sliver of rage","Sliver of corrpution","Sliver of disdain","Sliver of torment","Nydarax leg","Nydarax eye","Gold key","Mummy bandage","Mummy soul","Ancient tablet"],
      eventitems: ["Sugar brew","Egg ring","Party hat 1","Santa hat","Jingle top","Jingle pants","Candy cane","Easter egg","Bag of tricks","Bag of sweets","Magic bag of treats","Pumpking helm","Pumpking sword","Pumpking shield","Party hat 2","Jester hat","Based santa hat","Scoorage hat","Scoorage shirt","Pack of snow","Xmas tree sword","Candy cane staff","Egg head","Hand of baphomet","Head of baphomet","Pumpkin zombie hat","Party hat 3","Callsy jacket","Classy pants","Sparkling grapejuice","Antlers","Christmas tree hat","Jingle hat","White present","Red present","Gold present","Carrot launcher","Carrotproof helmet","Carrotproof vest","Egg ring","Party hat 4","Box of chocolate","Box of pralines","Loveshot","Arrow head","Heartseeker","Eternal love","Lootkin","Bionic skull","Bionic ribcage","Bionic limbs","Scream mask","Birthday cake","Party hat 5","Blue ballon","Red ballon","Yellow ballon","Green ballon","Bunch of ballons","Snowball ammo","Ring of snow","Snowball launcher","Black santa hat","Lucky egg","Carrot rocket","Bonka's barrier","Eggy bludgeon","Wabbit hat","Party hat 6","Party crasher","Smelly key","Leaky leek","Evileek staff","Evileek shield","Evileek mask","Sleekest","Chicken head","Chicken wings","Chicken feathers"
    ],
      others: ["Ruby","Sapphire","Emerald","Arosite","Sandstone shield","Scorpion shield","Deadrock shield","Ancient shield","Iron spade","Crimsteel spade","Mythan spade","Golemite spade","Ancient spade","Saving grace","Bat amulet","Nature amulet","Amulet of focus","Porspector's necklace","Ruby necklace","Sapphire necklace","Emerald necklace","Arosite necklace","Magnetite necklace","Battle necklace","Scorpion gauntlets","Raptor gloves","Desert raptor gloves","Ice raptor gloves","Cactus gloves","Frozen skull","Icy right half","Icy left half","Ring of treasure","Nature ring","Bat ring","Ring of might","Infernal ring","Cactus ring","Snake charm","Infernal hammer","Ring of violation","Pendant of serenity","Inferno tome","Consume tome","Blizzard tome","Torture tome","Lolipop","Nydarax teleport scrool"]
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
      "cobalt ore": "https://www.curseofaros.wiki/wiki/Cobalt_Ore",
      "varaxium": "https://www.curseofaros.wiki/wiki/Varaxium",
      "black salt": "https://www.curseofaros.wiki/wiki/Black_Salt",
      "magic ore": "https://www.curseofaros.wiki/wiki/Magic_Ore",
      "copper bar": "https://www.curseofaros.wiki/wiki/Bronze_Bar",
      "iron bar":"https://www.curseofaros.wiki/wiki/Iron_Bar",
      "steel bar":"https://www.curseofaros.wiki/wiki/Steel_Bar",
      "crimsteel bar":"https://www.curseofaros.wiki/wiki/Crimsteel_Bar",
      "silver bar":"https://www.curseofaros.wiki/wiki/Silver_Bar",
      "gold nugget":"hh",
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
      "wisdom relic":"https://www.curseofaros.wiki/wiki/Wisdom_Relic",
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
      "sapphire scarab leg":"https://www.curseofaros.wiki/wiki/Saphire_Scarab_Leg",
      "cave bat eye":"https://www.curseofaros.wiki/wiki/Cave_Bat_Eye",
      "envenomed blood":"https://www.curseofaros.wiki/wiki/Envenomed_Blood",
      "raptor claw":"https://www.curseofaros.wiki/wiki/Raptor_Claw",
      "ruby scarab leg":"https://www.curseofaros.wiki/wiki/Ruby_Scarab_Leg",
      "forest fiend eye":"https://www.curseofaros.wiki/wiki/Forest_Fiend_Eye",
      "desert raptor claw":"https://www.curseofaros.wiki/wiki/Desert_Raptor_Claw",
      "rock fiend eye":"https://www.curseofaros.wiki/wiki/Rock_Fiend_Eye",
      "hornet antena":"https://www.curseofaros.wiki/wiki/Hornet_Antena",
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
      "disdain Eye":"https://www.curseofaros.wiki/wiki/Disdain_Eye",
      "baby dragon spine":"https://www.curseofaros.wiki/wiki/Baby_Dragon_Spine",
      "ragefull eye":"https://www.curseofaros.wiki/wiki/Ragefull_Eye",
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
      "assasin's tonic":"https://www.curseofaros.wiki/wiki/Assasin%27s_Tonic",
      "auric bloom":"https://www.curseofaros.wiki/wiki/Auric_Bloom",
      "mirrorback brew":"https://www.curseofaros.wiki/wiki/Mirrorback_Brew",
      "golem's power":"https://www.curseofaros.wiki/wiki/Golem%27s_Power",
      "guardian's bulwark":"https://www.curseofaros.wiki/wiki/Guardian%27s_Bulwark",
      "quietus":"https://www.curseofaros.wiki/wiki/Quietus",
      "midas brew":"https://www.curseofaros.wiki/wiki/Midas_Brew",
      "featherwalk potion":"https://www.curseofaros.wiki/wiki/Featherwalk_Potion",
      "sanguiene oath":"https://www.curseofaros.wiki/wiki/Sanguiene_Oath",
      "dance of the Undead":"https://www.curseofaros.wiki/wiki/Dance_of_the_Undead",
      "gilded transmutation":"https://www.curseofaros.wiki/wiki/Gilded_Transmutation",
      "cloudwalk potion":"https://www.curseofaros.wiki/wiki/Cloudwalk_Potion",
      "distilled extract":"https://www.curseofaros.wiki/wiki/Distilled_Extract",
      "provacation potion":"https://www.curseofaros.wiki/wiki/Provacation_Potion",
      "stigoi's convenant":"https://www.curseofaros.wiki/wiki/Stigoi%27s_Convenant",
      "death's rally":"https://www.curseofaros.wiki/wiki/Death%27s_Rally",
      "Cobalt armor":"hh",
      "Varax armor":"hh",
      "Glacial armor":"hh",
      "Deadrock armor":"hh",
      "Spectral armor":"hh",
      "Phantom armor":"hh",
      "Nightspoon armor":"hh"
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
          <h3>Disclaimer:We are not responsible for any discrepancies in prices.</h3>
          <h4>Little information about this server: This server created in 01/09/2025 for help Curse of Aros community</h4>
          <h4>There you are can search prices of items</h4>
          <h4 class="note">Note: Search full name of items for get good result and tap item name for get information about item</h4>
          <h4>Funny informations about CoA:</h4>
          <h4>First 120 base normal player
 is Saketas</h4>
          <h4>First 120 base Lone Wolf player
 is Devotion</h4>
          <h4>Most expensive CoA item is Jester hat</h4>
          <a href="https://imgbb.com/"><img src="https://i.ibb.co/v6zrJQrz/Jester-Hat-m.png" alt="Jester-Hat-m" border="0"></a>
          <h4>Most useless CoA Item is Hammer</h4>
          <a href="https://imgbb.com/"><img src="https://i.ibb.co/m5v6S2LK/Hammer-m.png" alt="Hammer-m" border="0"></a>
          <h4>First pet in CoA is Bat pet</h4>
          <a href="https://imgbb.com/"><img src="https://i.ibb.co/qLY4gby3/Pet-bat-sm.gif" alt="Pet-bat-sm" border="0"></a>
          <h4>First item in CoA is Potion
 (I posted first potion design)</h4>
          <a href="https://imgbb.com/"><img src="https://i.ibb.co/ym2qbwkV/20200713113545-Potion-m.png" alt="20200713113545-Potion-m" border="0"></a>
          <h4>Join my discord server for give suggestions or help me update prices </h4>
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
