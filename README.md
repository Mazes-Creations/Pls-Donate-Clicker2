# Pls-Donate-Clicker
Let's make a game!
	name:Pls Donate Clicker
	by:Mazes
	desc:Create gamepasses to make robux!<//>Make robux to get exponentially rich - the sky's the limit!
	created:18/4/2025
	updated:18/4/2025
	version:1

Settings
	background:https://i.imgur.com/XtYyVaH_d.webp?maxwidth=760&fidelity=grand
	building cost increase:105%
	building cost refund:75%
	spritesheet:icons, 48 by 48, stuff/bunnyIcons.png
	stylesheet:stuff/bigBlue.css

Layout
	use default
		
Buttons
	*booth
		name:Pls Donate Booth
		desc:People buy gamepasses from your stand and you get robux! Your only current source of income!
		on click:anim icon wobble
		on click:yield 0 robux
		icon:stuff/bunny.png
		Your Stand
		class:bigButton hasFlares
		icon class:shadowed
		tooltip origin:bottom
		tooltip class:red

Resources
	*bunny|bunnies
		name:Bunny|Bunnies
		desc:These are your bunnies. You can use them to purchase things. Your goal is to have as many bunnies as possible!
		icon:icons[0,0]
		class:noBackground
		show earned
		
	*goldenCarrot|goldenCarrots
		name:Golden carrot|Golden carrots
		desc:These shiny carrots are terribly rare, terribly precious and terribly delicious!
		icon:icons[0,1]
		class:noBackground
		hidden when 0
		
Shinies
	*richkid
		on click:log Woop
		movement:onRight moveLeft fade bounce:0.05
		frequency:60
		frequency variation:30
		icon:https://i.imgur.com/ygEvAhR_d.webp?maxwidth=760&fidelity=grand
		class:bigButton
		on click:
			$boost=1
			if (have clover) $boost=4
			if (chance(25%))
				//get at least 7, or between 1 and 3 minutes of our bunny production
				$amount=max(7,random(bunnies:ps*60*1,bunnies:ps*60*3))*$boost
				toast The lucky bunny grants you<//><b>[$amount] bunnies</b>.
				yield $amount bunnies
			else
				$amount=1*$boost
				toast The lucky bunny grants you<//><b>[$amount] golden carrot[s?$amount]</b>!
				yield $amount goldenCarrot
			end
		end

Buildings
	*TEMPLATE
		on click:anim glow
		
	*cage|cages
		name:Rabbit cage|Rabbit cages
		desc:A tiny little cage.<//><b>Effect:</b><.>Produces 1 rabbit every 10 seconds.
		icon:icons[3,0]
		cost:15 bunnies
		on tick:yield 0.1 bunny
		unlocked
	
	*hutch|hutches
		name:Rabbit hutch|Rabbit hutches
		desc:A bit roomier than a cage, with enough space to hop around.<//><b>Effect:</b><.>Produces 1 rabbit every 2 seconds.
		icon:icons[3,1]
		cost:100 bunnies
		on tick:yield 0.5 bunnies
		req:100 bunnies:earned
	
	*coop|coops
		name:Rabbit coop|Rabbit coops
		desc:A much nicer rabbit home where full bunny families can live.<//><b>Effect:</b><.>Produces 5 rabbits per second.
		icon:icons[3,2]
		cost:600 bunnies
		on tick:yield 5 bunnies
		req:600 bunnies:earned
	
	*pen|pens
		name:Rabbit pen|Rabbit pens
		desc:A lovely enclosure with plenty of green space.<//><b>Effect:</b><.>Produces 12 rabbits per second.
		icon:icons[3,3]
		cost:4000 bunnies
		on tick:yield 12 bunnies
		req:4000 bunnies:earned
	
	*meadow|meadows
		name:Rabbit meadow|Rabbit meadows
		desc:A wide open space full of shade and lush grass.<//><b>Effect:</b><.>Produces 90 rabbits per second.
		icon:icons[3,4]
		cost:20000 bunnies
		on tick:yield 90 bunnies
		req:20000 bunnies:earned
	
	*village|villages
		name:Rabbit village|Rabbit villages
		desc:Your bunnies are building their own villages now!<//><b>Effect:</b><.>Produces 300 rabbits per second.
		icon:icons[3,5]
		cost:200000 bunnies, 1 goldenCarrot
		on tick:yield 300 bunnies
		req:200000 bunnies:earned and independenceDay
		
	*city|cities
		name:Rabbit city|Rabbit cities
		desc:A bustling little city, populated with busy rabbits.<//><b>Effect:</b><.>Produces 1000 rabbits per second.
		icon:icons[3,6]
		cost:3000000 bunnies, 4 goldenCarrots
		on tick:yield 1000 bunnies
		req:3000000 bunnies:earned and independenceDay
		
	*citadel|citadels
		name:Moon citadel|Moon citadels
		desc:An ornate palace standing on the moon, ruled by bunny kings and queens and staffed with royal bunny guards.<//><b>Effect:</b><.>Produces 4000 rabbits per second.
		icon:icons[3,7]
		cost:70000000 bunnies, 16 goldenCarrots
		on tick:yield 4000 bunnies
		on tick:if (have moonGardens) yield 0.01 goldenCarrot
		req:70000000 bunnies:earned and independenceDay
		
	*fortress
		name:Freedom fortress
		text:Freedom fortress ([this]%)
		desc:A huge bunny castle. A monument to the adventurous spirit of bunnykind, which will take time and effort to complete.<//><b>The fortress is [this]% complete.</b>
		icon:icons[3,8]
		cost:300000000 bunnies, 100 goldenCarrots
		req:70000000 bunnies:earned and independenceDay
		limit:100
		cost increase:105%
		
Upgrades
	*TEMPLATE
		on click:anim glow

	//starter gamepass upgrades
 
  	*starterGamepass
          cost:0 robux
          passive:increase yield of robuxButton by 0.6
	
	//food upgrades
	//inspiration : http://rabbit.org/suggested-vegetables-and-fruits-for-a-rabbit-diet/
	
	*parsley
		name:Parsley
		desc:A nice little supplement to your bunnies' diet.<//><b>Effect:</b><.>+1 bunny/click
		icon:icons[1,1]
		cost:100 bunnies
		passive:increase bunny yield of bunnyButton by 1
		req:10 bunnies:earned
		
	*spinach
		name:Spinach
		desc:Big tasty leaves, perfect for hungry bunnies.<//><b>Effect:</b><.>+1 bunny/click
		icon:icons[1,2]
		cost:200 bunnies
		passive:increase bunny yield of bunnyButton by 1
		req:50 bunnies:earned
		
	*lettuce
		name:Lettuce
		desc:Frilly greens loved by all bunnies.<//><b>Effect:</b><.>+1 bunny/click
		icon:icons[1,3]
		cost:400 bunnies
		passive:increase bunny yield of bunnyButton by 1
		req:200 bunnies:earned
		
	*broccoli
		name:Broccoli
		desc:Crunchy greens that look like little trees.<//><b>Effect:</b><.>bunnies/click x2<.>bunny production +5%
		icon:icons[1,4]
		cost:3000 bunnies
		passive:multiply bunny yield of bunnyButton by 2
		passive:multiply yield of bunnies by 1.05
		req:1000 bunnies:earned
		
	*apple
		name:Apple
		desc:Nice pieces of juicy red apples.<//><b>Effect:</b><.>bunnies/click x1.5<.>bunny production +5%
		icon:icons[1,5]
		cost:10000 bunnies
		passive:multiply bunny yield of bunnyButton by 1.5
		passive:multiply yield of bunnies by 1.05
		req:1000 bunnies:earned
		
	*radish
		name:Radish
		desc:Purple, crunchy, and strangely spicy.<//><b>Effect:</b><.>bunnies/click x1.5<.>bunny production +5%
		icon:icons[1,6]
		cost:50000 bunnies
		passive:multiply bunny yield of bunnyButton by 1.5
		passive:multiply yield of bunnies by 1.05
		req:10000 bunnies:earned
		
	*mint
		name:Mint
		desc:Tasty, and gives your bunnies a lovely breath.<//><b>Effect:</b><.>bunnies/click x1.5<.>bunny production +5%
		icon:icons[1,7]
		cost:100000 bunnies
		passive:multiply bunny yield of bunnyButton by 1.5
		passive:multiply yield of bunnies by 1.05
		req:50000 bunnies:earned
		
	*chard
		name:Chard
		desc:Broad leaves that make for a tasty salad.<//><b>Effect:</b><.>bunnies/click x1.5<.>bunny production +5%
		icon:icons[1,8]
		cost:500000 bunnies
		passive:multiply bunny yield of bunnyButton by 1.5
		passive:multiply yield of bunnies by 1.05
		req:100000 bunnies:earned
		
	*cherry
		name:Cherry
		desc:Your bunnies look like little vampires when they start munching on these!<//><b>Effect:</b><.>bunnies/click x1.5<.>bunny production +5%
		icon:icons[1,9]
		cost:1000000 bunnies
		passive:multiply bunny yield of bunnyButton by 1.5
		passive:multiply yield of bunnies by 1.05
		req:500000 bunnies:earned
		
	*carrot
		name:Carrot
		desc:The quintessential rabbit food! Crunchy, orange, and perfect.<//><b>Effect:</b><.>bunnies/click x2<.>bunny production +10%
		icon:icons[1,0]
		cost:100000000 bunnies
		passive:multiply bunny yield of bunnyButton by 2
		passive:multiply yield of bunnies by 1.1
		req:1000000 bunnies:earned
	
	//building upgrades
	
	*buildingUpgrade1
		name:Sippy bottles
		desc:Your bunnies can drink their fill!<//><b>Effect:</b><.>rabbit cage production x2<.>rabbit hutch production x2<.>rabbit coop production x2
		icon:icons[2,0] icons[3,0]
		cost:1000 bunnies
		passive:multiply yield of cage by 2
		passive:multiply yield of hutch by 2
		passive:multiply yield of coop by 2
		req:(cages>=10 or hutches>=10 or coops>=10)
		
	*buildingUpgrade2
		name:Prime grade hay
		desc:Not just for horses anymore!<//><b>Effect:</b><.>rabbit cage production x2<.>rabbit hutch production x2<.>rabbit coop production x2
		icon:icons[2,0] icons[3,1]
		cost:100000 bunnies
		passive:multiply yield of cage by 2
		passive:multiply yield of hutch by 2
		passive:multiply yield of coop by 2
		req:(cages>=50 or hutches>=50 or coops>=50)
		
	*buildingUpgrade3
		name:Shredded newspapers
		desc:You'd think they just poop on these, but they really enjoy reading the Sunday comics.<//><b>Effect:</b><.>rabbit cage production x2<.>rabbit hutch production x2<.>rabbit coop production x2
		icon:icons[2,0] icons[3,2]
		cost:5000000 bunnies
		passive:multiply yield of cage by 2
		passive:multiply yield of hutch by 2
		passive:multiply yield of coop by 2
		req:(cages>=100 or hutches>=100 or coops>=100)
		
	*buildingUpgrade4
		name:Pretty fences
		desc:Just the right size so your bunnies can peek through but not hop over!<//><b>Effect:</b><.>rabbit pen production x2<.>rabbit meadow production x2
		icon:icons[2,0] icons[3,3]
		cost:50000 bunnies
		passive:multiply yield of pen by 2
		passive:multiply yield of meadow by 2
		req:(pens>=10 or meadows>=10)
		
	*buildingUpgrade5
		name:Bunny playground
		desc:If your bunnies are outside, they might as well get some exercise!<//><b>Effect:</b><.>rabbit pen production x2<.>rabbit meadow production x2
		icon:icons[2,0] icons[3,4]
		cost:5000000 bunnies
		passive:multiply yield of pen by 2
		passive:multiply yield of meadow by 2
		req:(pens>=50 or meadows>=50)
		
	*buildingUpgrade6
		name:Bunny TVs
		desc:Televisions that broadcast bunny cartoons, bunny sitcoms, and bunny news bulletins.<//><b>Effect:</b><.>rabbit village production x2<.>rabbit city production x2
		icon:icons[2,0] icons[3,5]
		cost:1000000 bunnies
		passive:multiply yield of village by 2
		passive:multiply yield of city by 2
		req:(villages>=10 or cities>=10)
		
	*buildingUpgrade7
		name:Wee little bunny cars
		desc:Your bunnies drive around in these. How nice!<//><b>Effect:</b><.>rabbit village production x2<.>rabbit city production x2
		icon:icons[2,0] icons[3,6]
		cost:500000000 bunnies
		passive:multiply yield of village by 2
		passive:multiply yield of city by 2
		req:(villages>=50 or cities>=50)
		
	*buildingUpgrade8
		name:Soothing moon crystals
		desc:Just really nice to be around.<//><b>Effect:</b><.>moon citadel production x2
		icon:icons[2,0] icons[3,7]
		cost:1000000000 bunnies
		passive:multiply yield of citadel by 2
		req:10 citadels
		
	//golden carrot upgrades
	
	*goldenTouch
		name:Golden touch
		desc:The delicate art of finding vegetables made of precious metals.<//><b>Effect:</b><.>1% chance of gaining 1 golden carrot per bunny click
		icon:icons[2,5]
		cost:1 goldenCarrot
		req:1 goldenCarrot:earned
		
	*rabbitHaste
		name:Rabbit's haste
		desc:I'm late! I'm late! For a very important date!<//><b>Effect:</b><.>lucky bunnies appear 30% more often
		icon:icons[2,6]
		passive:multiply frequency of luckyBunny by 0.7
		cost:5 goldenCarrots
		req:1 goldenCarrot:earned
	
	*independenceDay
		name:Independence day
		desc:Your bunnies are making their first step towards declaring their independence from the oppressive shackles of pens and cages.<//><b>Effect:</b><.>unlocks new buildings
		icon:icons[2,7]
		cost:10 goldenCarrots
		req:5 goldenCarrots:earned
		
	*clover
		name:Clover
		desc:A delicious herb that tastes lucky.<//><b>Effect:</b><.>lucky bunny effects are 4 times more powerful
		icon:icons[2,8]
		cost:100 goldenCarrots
		req:50 goldenCarrots:earned
		
	*moonGardens
		name:Moon gardens
		desc:The royal botanists in your moon citadels have found new ways of cultivating plants in reduced gravity!<//><b>Effect:</b><.>moon citadels now produce 1 golden carrot every 100 seconds
		icon:icons[2,9]
		cost:100 goldenCarrots
		req:50 goldenCarrots:earned
		
Achievements
	*TEMPLATE
		on click:anim glow
		
	*bunnyAchiev1
		name:Run rabbit run
		desc:Have <b>1</b> bunny.
		req:1 bunny
		icon:icons[2,4] icons[0,2] icons[0,6]
	*bunnyAchiev2
		name:Bunniest home videos
		desc:Have <b>1000</b> bunnies.
		req:1000 bunnies
		icon:icons[2,4] icons[0,3] icons[0,6]
	*bunnyAchiev3
		name:You got buns, hun
		desc:Have <b>1000000</b> bunnies.
		req:10000000 bunnies
		icon:icons[2,4] icons[0,4] icons[0,6]
		
	*clickAchiev1
		name:That tickles
		desc:Click the bunny <b>10</b> times.
		req:10 bunnyButton clicks
		icon:icons[2,2] icons[0,2] icons[0,6]
	*clickAchiev2
		name:Don't squeeze me I'll fart
		desc:Click the bunny <b>100</b> times.
		req:100 bunnyButton clicks
		icon:icons[2,2] icons[0,3] icons[0,6]
	*clickAchiev3
		name:You're cruising for a bruising, dude
		desc:Click the bunny <b>2000</b> times.
		req:2000 bunnyButton clicks
		icon:icons[2,2] icons[0,4] icons[0,6]
		
	*bunnyPsAchiev1
		name:Be vewy vewy quiet
		desc:Produce <b>10</b> bunnies per second.
		req:10 bunnies per second
		icon:icons[2,3] icons[0,2] icons[0,6]
	*bunnyPsAchiev2
		name:Hop and a skip
		desc:Produce <b>1000</b> bunnies per second.
		req:1000 bunnies per second
		icon:icons[2,3] icons[0,3] icons[0,6]
	*bunnyPsAchiev3
		name:Go forth and multiply
		desc:Produce <b>100000</b> bunnies per second.
		req:100000 bunnies per second
		icon:icons[2,3] icons[0,4] icons[0,6]
		
	*carrotAchiev1
		name:Isn't it neat
		desc:Have <b>1</b> golden carrot.
		req:1 goldenCarrot
		icon:icons[0,1] icons[0,2]
	*carrotAchiev2
		name:All that glitters
		desc:Have <b>100</b> golden carrots.
		req:100 goldenCarrot
		icon:icons[0,1] icons[0,3]
	*carrotAchiev3
		name:Zero nutritional value
		desc:Have <b>1000</b> golden carrots.
		req:1000 goldenCarrot
		icon:icons[0,1] icons[0,4]
	
	*fortressAchiev
		name:Freedom!
		desc:Complete building the <b>freedom fortress</b>.<//>This is it. You beat the game!
		req:100 fortress
		icon:icons[3,8] icons[0,4]
