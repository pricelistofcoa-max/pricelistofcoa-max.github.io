<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>CoA Price List</title>
  <style>
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

    h1 {
      text-align: center;
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
      ores: ["Copper Ore","Tin ore","Iron ore","Salt","Coal","Crimstell ore","Silver ore","Gold ore","Pink salt","Mythan ore","Cobalt ore","Varaxium","Black salt","Magic ore"],
      bars: ["Copper Bar","Iron bar","Steel bar","Crimsteel bar","silver bar","Gold nugget","Gold bar","Mythan bar","Cobalt bar","Varax bar","Magic bar"],
      logs: ["Pine Log","Dead log","Birch log","Applewood","Willow log","Oak log","Chestnut log","Maple log","Olive log","Stinkwood","Magic log","Palmwood","Pearwood","Lime wood"],
      relics: ["Accuracy relic","Guarding Relic","Healing relic","Wealth relic","Power relic","Nature relic","Fire relic","Damage relic","Leeching relic","Experience relic","Wisdom relic","Ice relic","Cursed relic","Efficiency relic","Affliction relic"],
      fishes: ["Anchovies","Gold Fish","Mackerel","Squid","Sardine","Eel","Anglerfish","Trout","Jellyfish","Bass","Herringbone","Tuna","Lobster","Sea turtle","Manta ray","Shark","Orca","Giant squid","Earthworm","Iceworm","Corpseworm","Toxicworm","Sandworm","Beetle","Grasshopper","Wasp","Scallop"],
      spellbinding: ["Book","Magic essence"],
      alchemy: ["Bat eye","Pink gelatin","Fishing spider eye","Brown mushroom","Forest spider eye","Cow skull","Forestbat eye","Frozen gelatin","Snow core","Sapling leaf","Ice spider eye","Cave spider eye","Skeletal bat eye","Sapphire scarab leg","Cave bat eye","Envenomed blood","Raptor claw","Ruby scarab leg","Forest fiend eye","Desert raptor claw","Rock fiend eye","Hornet antena","Luminant gelatin","Juvenile eye","Ancient bat eye","Ice raptor claw","Spectral flintstone","Arocite scarab leg","Shadow flintstone","Phantom flintstone","Spectral fiend eye","Phantom fiend eye","Magnetite scarab leg","Corrupted eye","Golemite bat eye","Golemite fiend eye","Tormented eye","Disdain Eye","Baby dragon spine","Ragefull eye","Potion","Mining potion","Woodcutting potion","Fishing potion","Smithing potion","Crafting potion","Cooking potion","Spellbinding potion","Taskmaster's brew","Prospector's brew","Lumberjacks ale","Blacksmith's stout","Artisan's syrup","Angler's elixir","Chef's kiss","Imbuer's wine","Spellpower potion","Concentrated elixir","Divine clarity","Titan's strength","Duelist's draft","Stonebound salve","Backlash balm","Berserker potion","Arcanist's wrath","Forsworn focus","Antidote","Frostskin potion","Arctic potion","Scavenger's balm","Vampirism potion","Assasin's tonic","Auric bloom","Mirrorback brew","Golem's power","Guardian's bulwark","Quietus","Midas brew","Featherwalk potion","Sanguiene oath","Dance of the Undead","Gilded transmutation","Cloudwalk potion","Distilled extract","Provacation potion","Stigoi's convenant","Death's rally"],
      armors: ["Cobalt armor","Varax armor","Glacial armor","Deadrock armor","Spectral armor","Phantom armor","Nightspoon armor"],
      weapons: ["Sharper mythan sword","Cobalt sword","Chaotic mythan sword","Varaxite sword","Glacial blade","Nature's blade","Spectral sword","Phantom sword","Ancient scimitar","Fire staff","Ice staff","Nature staff","Cursed staff","Elder fire staff","Elder ice staff","Elder nature staff","Elder cursed staff","Nightspoon staff"],
      tools: ["Mythan axe","Mythan pickaxe","Mythan rod","Mythan secateurs","Cobalt axe","Cobalt pickaxe","Cobalt rod","Cobalt secateurs","Varax axe","Varax pickaxe","Varax rod","Varax secateurs","Magic axe","Magic pickaxe","Magic rod","Byromera secateurs","Ancient axe","Ancient pickaxe","Ancient rod"],
      bossparts: ["Balance fragment","Golemite slab","Golemite shard","Golemite eye","Golemite orb","Dragon scale","Dragon eye","Dragon claw","Sliver of rage","Sliver of corrpution","Sliver of disdain","Sliver of torment","Nydarax leg","Nydarax eye","Gold key","Mummy bandage","Mummy soul","Ancient tablet"],
      eventitems: ["Sugar brew","Egg ring","Party hat 1","Santa hat","Jingle top","Jingle pants","Candy cane","Easter egg","Bag of tricks","Bag of sweets","Magic bag of treats","Pumpking helm","Pumpking sword","Pumpking shield","Party hat 2","Jester hat","Based santa hat","Scoorage hat","Scoorage shirt","Pack of snow","Xmas tree sword","Candy cane staff","Egg head","Hand of baphomet","Head of baphomet","Pumpkin zombie hat","Party hat 3","Callsy jacket","Classy pants","Sparkling grapejuice","Antlers","Christmas tree hat","Jingle hat","White present","Red present","Gold present","Carrot launcher","Carrotproof helmet","Carrotproof vest","Egg ring","Party hat 4","Box of chocolate","Box of pralines","Loveshot","Arrow head","Heartseeker","Eternal love","Lootkin","Bionic skull","Bionic ribcage","Bionic limbs","Scream mask","Birthday cake","Party hat 5","Blue ballon","Red ballon","Yellow ballon","Green ballon","Bunch of ballons","Snowball ammo","Ring of snow","Snowball launcher","Black santa hat","Lucky egg","Carrot rocket","Bonka's barrier","Eggy bludgeon","Wabbit hat","Party hat 6","Party crasher","Smelly key","Leaky leek","Evileek staff","Evileek shield","Evileek mask","Sleekest","Chicken head","Chicken wings","Chicken feathers"
],
      others: ["Ruby","Sapphire","Emerald","Arosite","Sandstone shield","Scorpion shield","Deadrock shield","Ancient shield","Iron spade","Crimsteel spade","Mythan spade","Golemite spade","Ancient spade","Saving grace","Bat amulet","Nature amulet","Amulet of focus","Porspector's necklace","Ruby necklace","Sapphire necklace","Emerald necklace","Arosite necklace","Magnetite necklace","Battle necklace","Scorpion gauntlets","Raptor gloves","Desert raptor gloves","Ice raptor gloves","Cactus gloves","Frozen skull","Icy right half","Icy left half","Ring of treasure","Nature ring","Bat ring","Ring of might","Infernal ring","Cactus ring","Snake charm","Infernal hammer","Ring of violation","Pendant of serenity","Inferno tome","Consume tome","Blizzard tome","Torture tome"]
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
      "iron bar":"hh",
      "steel bar":"hh",
      "crimsteel bar":"hh",
      "silver bar":"hh",
      "gold nugget":"hh",
      "gold bar":"hh",
      "mythan bar":"hh",
      "cobalt bar":"hh",
      "varax bar":"hh",
      "magic bar":"hh",
      "pine log":"hh",
      "dead log":"hh",
      "birch log":"hh",
      "applewood":"hh",
      "willow log":"hh",
      "oak log":"hh",
      "chestnut log":"hh",
      "maple log":"hh",
      "olive log":"hh",
      "stinkwood":"hh",
      "magic log":"hh",
      "palmwood":"hh",
      "pearwood":"hh",
      "limewood log":"hh",
      "accuracy relic":"hh",
      "guarding relic":"hh",
      "healing relic":"hh",
      "wealth relic":"hh",
      "power relic":"hh",
      "nature relic":"hh",
      "fire relic":"hh",
      "damage relic":"hh",
      "experience relic":"hh",
      "leeching relic":"hh",
      "experience relic":"hh",
      "wisdom relic":"hh",
      "ice relic":"hh",
      "cursed relic":"hh",
      "efficiency relic":"hh",
      "affliction relic":"hh",
      "anchovies":"hh",
      "gold fish":"hh",
      "mackerel":"hh",
      "squid":"hh",
      "sardine":"hh",
      "eel":"hh",
      "anglerfish":"hh",
      "trout":"hh",
      "jellyfish":"hh",
      "bass":"hh",
      "herringbone":"hh",
      "tuna":"hh",
      "lobster":"hh",
      "sea turtle":"hh",
      "manta ray":"hh",
      "shark":"hh",
      "orca":"hh",
      "giant squid":"hh",
      "earthworm":"hh",
      "iceworm":"hh",
      "corpseworm":"hh",
      "toxicworm":"hh",
      "sandworm":"hh",
      "beetle":"hh",
      "grasshopper":"hh",
      "wasp":"hh",
      "scallop":"hh",
      "book":"hh",
      "magic essence":"hh",
      "bat eye":"hh",
      "pink gelatin":"hh",
      "fishing spider eye":"hh",
      "brown mushroom":"hh",
      "forest spider eye":"hh",
      "cow skull":"hh",
      "forestbat eye":"hh",
      "frozen gelatin":"hh",
      "snow core":"hh",
      "sapling leaf":"hh",
      "ice spider eye":"hh",
      "cave spider eye":"hh",
      "skeletal bat eye":"hh",
      "sapphire scarab leg":"hh",
      "cave bat eye":"hh",
      "envenomed blood":"hh",
      "raptor claw":"hh",
      "ruby scarab leg":"hh",
      "forest fiend eye":"hh",
      "desert raptor claw":"hh",
      "rock fiend eye":"hh",
      "hornet antena":"hh",
      "luminant gelatin":"hh",
      "juvenile eye":"hh",
      "ancient bat eye":"hh",
      "ice raptor claw":"hh",
      "spectral flintstone":"hh",
      "arocite scarab leg":"hh",
      "shadow flintstone":"hh",
      "phantom flintstone":"hh",
      "spectral fiend eye":"hh",
      "phantom fiend eye":"hh",
      "magnetite scarab leg":"hh",
      "corrupted eye":"hh",
      "golemite bat eye":"hh",
      "golemite fiend eye":"hh",
      "tormented eye":"hh",
      "disdain Eye":"hh",
      "baby dragon spine":"hh",
      "ragefull eye":"hh",
      "potion":"hh",
      "mining potion":"hh",
      "woodcutting potion":"hh",
      "fishing potion":"hh",
      "smithing potion":"hh",
      "crafting potion":"hh",
      "cooking potion":"hh",
      "spellbinding potion":"hh",
      "taskmaster's brew":"hh",
      "prospector's brew":"hh",
      "lumberjacks ale":"hh",
      "blacksmith's stout":"hh",
      "artisan's syrup":"hh",
      "angler's elixir":"hh",
      "chef's kiss":"hh",
      "imbuer's wine":"hh",
      "spellpower potion":"hh",
      "concentrated elixir":"hh",
      "divine clarity":"hh",
      "titan's strength":"hh",
      "duelist's draft":"hh",
      "stonebound salve":"hh",
      "backlash balm":"hh",
      "berserker potion":"hh",
      "arcanist's wrath":"hh",
      "forsworn focus":"hh",
      "antidote":"hh",
      "frostskin potion":"hh",
      "arctic potion":"hh",
      "scavenger's balm":"hh",
      "vampirism potion":"hh",
      "assasin's tonic":"hh",
      "auric bloom":"hh",
      "mirrorback brew":"hh",
      "golem's power":"hh",
      "guardian's bulwark":"hh",
      "quietus":"hh",
      "midas brew":"hh",
      "featherwalk potion":"hh",
      "sanguiene oath":"hh",
      "dance of the Undead":"hh",
      "gilded transmutation":"hh",
      "cloudwalk potion":"hh",
      "distilled extract":"hh",
      "provacation potion":"hh",
      "stigoi's convenant":"hh",
      "death's rally":"hh",
      "Cobalt armor":"hh",
      "Varax armor":"hh",
      "Glacial armor":"hh",
      "Deadrock armor":"hh",
      "Spectral armor":"hh",
      "Phantom armor":"hh",
      "Nightspoon armor":"hh",
      "Sharper mythan sword":"hh",
      "Cobalt sword":"hh",
      "Chaotic mythan sword":"hh",
      "Varaxite sword":"hh",
      "Glacial blade":"hh",
      "Nature's blade":"hh",
      "Spectral sword":"hh",
      "Phantom sword":"hh",
      "Ancient scimitar":"hh",
      "Fire staff":"hh",
      "Ice staff":"hh",
      "Nature staff":"hh",
      "Cursed staff":"hh",
      "Elder fire staff":"hh",
      "Elder ice staff":"hh",
      "Elder nature staff":"hh",
      "Elder cursed staff":"hh",
      "Nightspoon staff":"hh",
      "Mythan axe":"hh",
      "Mythan pickaxe":"hh",
      "Mythan rod":"hh",
      "Mythan secateurs":"hh",
      "Cobalt axe":"hh",
      "Cobalt pickaxe":"hh",
      "Cobalt rod":"hh",
      "Cobalt secateurs":"hh",
      "Varax axe":"hh",
      "Varax pickaxe":"hh",
      "Varax rod":"hh",
      "Varax secateurs":"hh",
      "Magic axe":"hh",
      "Magic pickaxe":"hh",
      "Magic rod":"hh",
      "Byromera secateurs":"hh",
      "Ancient axe":"hh",
      "Ancient pickaxe":"hh",
      "Ancient rod":"hh",
      "Balance fragment":"hh",
      "Golemite slab":"hh",
      "Golemite shard":"hh",
      "Golemite eye":"hh",
      "Golemite orb":"hh",
      "Dragon scale":"hh",
      "Dragon eye":"hh",
      "Dragon claw":"hh",
      "Sliver of rage":"hh",
      "Sliver of corrpution":"hh",
      "Sliver of disdain":"hh",
      "Sliver of torment":"hh",
      "Nydarax leg":"hh",
      "Nydarax eye":"hh",
      "Gold key":"hh",
      "Mummy bandage":"hh",
      "Mummy soul":"hh",
      "Ancient tablet":"hh",
     
    };

    function renderHome() {
      content.innerHTML = `
        <div class="home">
          <h1>Welcome!</h1>
          <h3>Little information about this server: This server created for help Curse of Aros community</h3>
          <p>There you are can search prices of items</p>
          <p class="note">Note: Search full name of items for get good result and tap item name for get information about item</p>
          <p>Join my discord server for give suggestions or help me update prices </p>
          <a class="btn-discord" href="https://discord.gg/NPn8wfQa" target="_blank" rel="noopener">Join my Discord</a>
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

            const lower = item.toLowerCase();
            if (itemLinks[lower]) {
              const a = document.createElement('a');
              a.href = itemLinks[lower];
              a.textContent = item;
              a.target = "_blank";
              a.style.color = "white";
              a.style.textDecoration = "none";
              div.appendChild(a);
            } else {
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
      const query = search.value.toLowerCase();
      content.innerHTML = "";
      let found = false;

      Object.values(items).forEach(sectionItems => {
        sectionItems.forEach(item => {
          if (item.toLowerCase().includes(query)) {
            const div = document.createElement('div');
            div.className = 'item';

            const lower = item.toLowerCase();
            if (itemLinks[lower]) {
              const a = document.createElement('a');
              a.href = itemLinks[lower];
              a.textContent = item;
              a.target = "_blank";
              a.style.color = "white";
              a.style.textDecoration = "none";
              div.appendChild(a);
            } else {
              div.textContent = item;
            }

            content.appendChild(div);
            found = true;
          }
        });
      });

      if (!found && query) {
        content.innerHTML = "<p>No items found.</p>";
      }

      if (!query) {
        renderHome(); // boşken ana sayfayı göster
      }
    });

    // Sayfa açılınca ana sayfayı göster
    renderHome();
  </script>
</body>
</html>
