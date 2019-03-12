# Locococo37.github.io



<html>
<head>
	<link type="text/css" rel="stylesheet" href="https://simplycoding.org/projects.css" />
	<script src="https://simplycoding.org/files/javascript.js"></script>
	<script src="https://simplycoding.org/files/run-the-code.js"></script>
	<script src="https://simplycoding.org/files/simplyjs/simply.js"> </script>
	<title>Python Text Adventure</title>
	<style type="text/css">
		.run-the-code-output {
			height:200px;
			overflow: scroll;
		}

	</style>


</head>


<body>	


<div style="float:right;width:60%"> 
	
<textarea class="run-the-code" data-mode="python" data-height="300" data-output="120px">

 import random
import time
def win():
    print "Victory Royale:You Saved the Village! They thank you and give you a cow as a reward!" 
def gameOver():
    print "Ooof!! Too Bad!"
    retry = raw_input("\n\nPlay again? (yes or no)\n\n").lower() 
    if retry == "yes":
       game()
    else:
       quit()


def game(): 

  gold = 50 
  character_hp = 125 
  weapon_damage = 15 
  monster_damage = 25 
  monster_payout = 80 
  weapons = ["fists"]
  
  MONSTERS = {
  "goblin":55,
  "zombie":80, 
  "wolf":105, 
  "dragon":150
    } 
  name = raw_input("\nWhat is your name?\n\n").title() 

  while name == "": 
    name = raw_input("\nWhat is your name?\n\n").title()

  print "\nWelcome", name, "Enjoy, Your Adventure!\n" 

  while character_hp > 0: 

    WEAPONS_STORE = { 
      "sword":140, 
      "axe":120,   
      "club":75,   
      "bat":45 
    } 

    store = raw_input("\nDo you want to buy weapons? (yes or no)\n\n").lower() 

    if store == "yes": 
      print "\nWEAPON\t\tCOST\n" 

      for items in WEAPONS_STORE:   
        print items, "\t\t", WEAPONS_STORE[items], "\n" 

      print "\nYou have", gold, "gold\n\n" 
      weapon_purchase = raw_input("Which weapon would you like to buy?\n\n").lower() 

      while weapon_purchase not in WEAPONS_STORE or weapon_purchase in weapons: 
        weapon_purchase = raw_input("Which weapon would you like to buy?\n\n").lower() 

      if weapon_purchase in WEAPONS_STORE and weapon_purchase not in weapons: 

        if gold >= WEAPONS_STORE[weapon_purchase]: 
          print "you bought a(n)", weapon_purchase, "\n" 
          gold -= WEAPONS_STORE[weapon_purchase] 
          weapons.append(weapon_purchase) 
          print "\nyou have", gold, "gold\n" 
          print "\nWeapons(s) you own\n" 
          for items in weapons: 
            print items   

        elif gold <= WEAPONS_STORE[weapon_purchase]: 
          print "not enough gold"   
    elif store == "no":
       print "\nTime to destroy a monster from the village!\n"
       print "\nMONSTERS\tHEALTH\t\n"
       for monster in MONSTERS:
          print monster, "\t\t", MONSTERS[monster], "\n"
       monchoice = raw_input("Which Monster do you want to Destroy from the Village\n\n").lower()
       if monchoice in MONSTERS:


          print "\n Good Luck! Destroy the", monchoice, "from the village"
       else:

          print "That monster is not in the village" 

          while monchoice not in MONSTERS:
              
             monchoice = raw_input("Which Monster do you want to Destroy from the Village\n\n").lower()

             print "\nWEAPONS YOU OWN\n"
             for weapon in weapons:


                print weapon, "\n"
          
       weapuse = raw_input("Which weapon do you choose\n\n").lower()

       if weapuse in weapons: 

          print "\nNice choice", name, "You will use the", weapuse, "against the", monchoice
          if weapuse == "fists" or weapuse == "bat":
             while character_hp > 0 and MONSTERS[monchoice] > 0:
                rand = random.randint(3, 7)
                pdmg = weapon_damage + rand
                mdmg = monster_damage

                print monchoice, "has", MONSTERS[monchoice], "health left\n\n"
                time.sleep(1.5)
                print "The", monchoice, "attacked YOU by", mdmg
                character_hp -= mdmg
                if character_hp <= 0:
                   gameOver()

                print name,", your health is now", character_hp
                time.sleep(1.5)

                print "\nYou attacked the", monchoice, "with the", weapuse, "for", pdmg, "damage!"
                MONSTERS[monchoice] -= pdmg
                time.sleep(1.5)

          elif weapuse == "club" or weapuse == "axe":
             while character_hp > 0 and MONSTERS[monchoice] > 0:
                rand = random.randint(5, 20)
                pdmg = weapon_damage + rand
                mdmg = monster_damage
                print monchoice, "has", MONSTERS[monchoice], "health left\n\n"
                time.sleep(1.5)
                print "The", monchoice, "attacked YOU by", mdmg
                character_hp -= mdmg
                if character_hp <= 0:
                   gameOver()

                print name,", your health is now", character_hp
                time.sleep(1.5)

                print "\nYou attacked the", monchoice, "with the", weapuse, "for", pdmg, "damage!"
                MONSTERS[monchoice] -= pdmg
                time.sleep(1.5)









       else: 

          print name, "\nYou don't own the", weapuse,"!"
          while weapuse not in weapons:

             weapuse = raw_input("\nWhat weapon will you use?\n\n").lower()

          print "\nWise choice", name, "You will use the", weapuse, "against the", monchoice
       if MONSTERS[monchoice] <= 0:
          print "\nThe", monchoice, "Has been destroyed, good work", name,"!"
          character_hp = 125
          gold += monster_payout
          print "\nYou Have", gold, "gold\n" 
          if monchoice == "dragon":
             win()
          del MONSTERS[monchoice] 










  




game()



</textarea>

</div>
<div style="float:left;width:35%">
        <h1 style="text-align:center">PTYHON TEXT ADVENTURE</h1>
    <h2 style="text-align:center;color:blue;">Click 'Run The Code!', bottom right of the editor, to start the game!</h2>
    <h2 style="text-align:center;color:green;">Enter Answers in box below the console (after click on 'Run The Code!')</h3>
</div>
<div class="cfloat"></div>
	
	</body>
</html>
