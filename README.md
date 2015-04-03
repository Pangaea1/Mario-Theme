{
	"name" : "Mario",
	"author" : "<b><i><span style='color:#8904B1'>Pangaea</span></i></b>",
	"summary" : "Hello there! I'm a Toad! Here in the Mushroom Kingdom, we are being threatened by some old enemies! Bowser wants to take control of our kingdom, and King Boo and his minions want to transform the kingdom into their own underworld! Wario and Waluigi try to drive everyone out of the kingdom, and Fawful is being...well, awful! But all hope isn't lost, as Mario and the gang are here to save the day! As long as Yoshi keeps protecting him and Rosalina keeps giving him some powerful upgrades, then Mario can keep blasting our enemies out of the Mushroom Kingdom!",
	"sides" : [{
			"translation" : "Mushroom Kingdom",
			"side" : "village",
			"winmsg" : "*** Wahoo! Okay ~Players~, to celebrate our victory, let's all grab a big slice of cake!"
		}, {
			"translation" : "Bowser's Kingdom",
			"side" : "maf1",
			"winmsg" : "±Bowser: ROAAAARR! Finally, the Mushroom Kingdom belongs to ~Players~! Hey, Princess, didn't you mention something about cake? Bring it to my minions and me, this instant!"
		}, {
			"translation" : "King Boo's Army",
			"side" : "maf2",
			"winmsg" : "±King Boo: Kekeke! The ghosts have infiltrated the Mushroom Kingdom, which has been turned into an underworld ruled by ~Players~!"
		}, {
			"translation" : "Deadly Duo",
			"side" : "maf3",
			"winmsg" : "Hey, what's that smell? It's the sweet scent of victory, achieved by ~Players~! Oh, and they probably farted, too."
		}, {
			"translation" : "Fawful",
			"side" : "maf4",
			"winmsg" : "±Fawful: Why, isn't that just awful? It appears I was too powerful, and now the Mushroom Kingdom belongs to me, ~Players~!"
		}
	],
	"variables" : {
		"toadHax" : {
			"revealTeam" : 0.1,
			"revealPlayer" : 0.03
		},
		"toadDistractHax" : {
			"revealTeam" : 0.03,
			"revealPlayer" : 0.03
		},
		"marioHax" : {
			"revealRole" : 0.35
		}
	},
	"roles" : [{
			"role" : "villager",
			"translation" : "Toad",
			"side" : "village",
			"help" : "I'm just one out of the many Toads living in the Mushroom Kingdom. I can't do anything at night, but sometimes I'll experience a fight going on from my house at night.",
			"actions" : {
				"hax" : {
					"kill" : "variable:toadHax",
					"distract" : "variable:toadDistractHax"
				}
			}
		}, {
			"role" : "peach",
			"translation" : "Princess Peach",
			"side" : "village",
			"help" : "I'm the princess of the Mushroom Kingdom: Princess Peach! Because I'm a princess, my vote is equivalent to that of 20 Toads, meaning my vote counts as 20. However, I should be wary of King Boo, whose vote counts as negative 20, meaning he can easily make my vote null during the voting phase!",
			"info" : "Vote counts as 20. Sided with the Mushroom Kingdom.",
			"actions" : {
				"vote" : 20
			}
		}, {
			"role" : "yoshi",
			"translation" : "Yoshi",
			"side" : "village",
			"help" : "I am the friendliest dinosaur of the Mushroom Kingdom, Yoshi! I have been protecting Mario for ages, so I can /shield [name] him during the night. If anyone happens to attack him while I am shielding him, I will take the hit and die instead! During the night, Mario might shoot fireballs into the air, and I have a chance of identifying him if he does so! If I happen to find him, I should tell him who I am right away!",
			"info" : "Can shield one person during the night (if anyone attacks his target, Yoshi will die instead). Sided with the Mushroom Kingdom.",
			"actions" : {
				"night" : {
					"shield" : {
						"target" : "AnyButSelf",
						"common" : "Role",
						"priority" : 10
					}
				},
				"hax" : {
					"fire" : "variable:marioHax"
				}
			}
		}, {
			"role" : "daisy",
			"translation" : "Daisy",
			"side" : "village",
			"help" : "I'm Daisy, princess of Salsalan -- I mean Sarasaland, and I have an entire garden dedicated to me! I can /distract [name] someone during the night by giving them a poisonous mushroom, which will make them feel sick and prevent them from acting during the night!",
			"info" : "Can distract one person during the night. Sided with the Mushroom Kingdom.",
			"actions" : {
				"night" : {
					"distract" : {
						"target" : "AnyButSelf",
						"common" : "Self",
						"priority" : 2,
						"distractmsg" : "Ugh...I don't feel so well...Daisy must've given me some kind of poisonous mushroom, and I couldn't do anything last night...",
						"teammsg" : "Uh oh...Daisy must've given my partner a poisonous mushroom, so I couldn't ~Action~ last night since I had to take care of them!"
					}
				}
			}
		}, {
			"role" : "birdo",
			"translation" : "Birdo",
			"side" : "village",
			"help" : "I'm Birdo, a heart-pink-love-elephant-dinosaur-female(?)-thing. I can /poison [name] someone during the night with my...um...'unique' complexion. I should try not to hit my friends, though, because that could be bad.",
			"info" : "Can poison one person during the night. Sided with the Mushroom Kingdom.",
			"actions" : {
				"night" : {
					"poison" : {
						"target" : "AnyButSelf",
						"common" : "Self",
						"priority" : 40,
						"limit" : 1,
						"count" : 2,
						"poisonDeadMessage" : "My eyes couldn't take anymore of Birdo's ugliness!"
					}
				}
			}
		}, {
			"role" : "luigi",
			"side" : "village",
			"translation" : "Luigi",
			"help" : "People always say I'm Mario's sidekick, understudy, shadow, blah blah blah. I got an entire game dedicated to me for crying out loud! I can /stalk [name] someone during the night to see if they visit anyone. I've been hunting for ghosts for years, so if I happen to stalk a Boo, I will react immediately and kill them instead! However, I am a bit of a scaredy cat, so if a Boo tries to distract me by scaring me during the night, I'll die of fear!",
			"info" : "Can stalk someone during the night. Dies if distracted by Boo. Sided with the Mushroom Kingdom.",
			"actions" : {
				"night" : {
					"stalk" : {
						"target" : "AnyButSelf",
						"common" : "Self",
						"priority" : 50,
						"stalkmsg" : "Hmm...it appears that ~Target~ visited ~Visit~ last night.",
						"novisitmsg" : "Well, aren't I paranoid! It appears that ~Target~ didn't visit anyone last night.",
						"command" : ["stalk", "dummy3"]
					}
				},
				"dummy2" : {
					"mode" : "die",
					"msg" : "Waaaah! A Boo tried to scare me last night, and I died of fear!",
					"targetmsg" : "I tried to scare Luigi, but I accidentally scared him to death!"
				}
			}
		}, {
			"role" : "toadsworth",
			"side" : "village",
			"translation" : "Toadsworth",
			"help" : "I am Toadsworth, and growing older I have become much slower and weaker than I was in my days on youth. Any inspectors will see me as a lowly Goomba, an enemy who is slow and weak like me. However, I can still pack a punch, so if I happen to get voted off during the day, I will be able to kill one person before I die!",
			"info" : "Inspects as a Goomba. If voted off, can kill someone before dying. Sided with the Mushroom Kingdom.",
			"actions" : {
				"inspect" : {
					"revealAs" : "goomba"
				},
				"lynch" : {
					"convertTo" : "dtoads",
					"convertmsg" : "~Self~, revealed to be ~Old~, can kill someone before dying!"
				}
			}
		}, {
			"role" : "dtoads",
			"side" : "village",
			"translation" : "Toadsworth",
			"hide" : true,
			"help" : "They voted me off, and that makes me mad! Before dying, I can /kill [name] someone during the night, and I will ignore all distractions and bypass all protections! However, I am still sided with the Mushroom Kingdom, so I should try to hit a bad guy!",
			"actions" : {
				"night" : {
					"kill" : {
						"target" : "AnyButSelf",
						"common" : "Self",
						"pierce" : true,
						"priority" : 0
					}
				}
			}
		}, {
			"role": "srosalina",
			"side": "village",
			"translation": "Rosalina",
			"infoName": "Rosalina (Small)",
			"help": "Adoptive mother of the Lumas and watcher of the cosmos, I am Rosalina. I can see everything in the universe, and thus I have the ability to /inspect [name] someone at night and discover who they truly are.",
			"info": "Can inspect one person during the night. Sided with the Mushroom Kingdom.",
			"actions": {
				"night": {
					"inspect": {
						"target": "AnyButSelf",
						"common": "Self",
						"priority": 35
					}
				}
			}
		}, {
			"role" : "rosalina",
			"side" : "village",
			"translation" : "Rosalina",
			"help" : "Adoptive mother of the Lumas and watcher of the cosmos, I am Rosalina. I can see everything in the universe, and thus, I have the ability to /inspect [name] someone at night and discover who they truly are. I am also magical, and with my wand I can cast different spells on our hero, Mario, allowing me to give him different power-ups with /ice [name], /raccoon [name], /fly [name], /steel [name], or /gold [name] during the night. However, I only have enough magic to cast each of these spells once, and only one per night. Also, these spells can only be used on Mario, so I should only use them on someone if I know that they are Mario. My spells are also known to sometimes go haywire, so I should be aware of the risks when casting a spell on Mario, especially if I try to turn him into his golden form.",
			"info" : "Can inspect one person during the night. Can turn Mario into either Ice Mario, Raccoon Mario, Flying Mario, Steel Mario, or Gold Mario once per night (each command can only be used once per game). Each spell has a slight chance of turning Mario into Baby Mario on accident (/gold has the highest chance of this). Sided with the Mushroom Kingdom.",
			"actions" : {
				"night" : {
					"inspect" : {
						"target" : "AnyButSelf",
						"common" : "Self",
						"priority" : 35
					},
					"ice" : {
						"command" : "convert",
						"target" : "AnyButSelf",
						"common" : "Self",
						"charges" : 1,
						"priority" : 45,
						"restrict" : ["raccoon", "fly", "steel", "gold"],
						"newRole" : {
							"random" : {
								"icemario" : 0.9,
								"babymario" : 0.1
							},
							"canConvert" : "mario",
							"convertmsg" : "Rosalina casts a spell on ~Old~, turning them into ~New~!"
						}
					},
					"raccoon" : {
						"command" : "convert",
						"target" : "AnyButSelf",
						"common" : "Self",
						"charges" : 1,
						"priority" : 45,
						"restrict" : ["ice", "fly", "steel", "gold"],
						"newRole" : {
							"random" : {
								"raccoonmario" : 0.8,
								"babymario" : 0.2
							},
							"canConvert" : "mario",
							"convertmsg" : "Rosalina casts a spell on ~Old~, turning them into ~New~!"
						}
					},
					"fly" : {
						"command" : "convert",
						"target" : "AnyButSelf",
						"common" : "Self",
						"charges" : 1,
						"priority" : 45,
						"restrict" : ["ice", "raccoon", "steel", "gold"],
						"newRole" : {
							"random" : {
								"flymario" : 0.8,
								"babymario" : 0.2
							},
							"canConvert" : "mario",
							"convertmsg" : "Rosalina casts a spell on ~Old~, turning them into ~New~!"
						}
					},
					"steel" : {
						"command" : "convert",
						"target" : "AnyButSelf",
						"common" : "Self",
						"charges" : 1,
						"priority" : 45,
						"restrict" : ["ice", "raccoon", "fly", "gold"],
						"newRole" : {
							"random" : {
								"steelmario" : 0.9,
								"babymario" : 0.1
							},
							"canConvert" : "mario",
							"convertmsg" : "Rosalina casts a spell on ~Old~, turning them into ~New~!"
						}
					},
					"gold" : {
						"command" : "convert",
						"target" : "AnyButSelf",
						"common" : "Self",
						"charges" : 1,
						"priority" : 45,
						"restrict" : ["ice", "raccoon", "fly", "steel"],
						"newRole" : {
							"random" : {
								"goldmario" : 0.7,
								"babymario" : 0.3
							},
							"canConvert" : "mario",
							"convertmsg" : "Rosalina casts a spell on ~Old~, turning them into ~New~!"
						}
					}
				}
			}
		}, {
			"role" : "mario",
			"side" : "village",
			"translation" : "Mario",
			"help" : "Wahoo! It's a-me, Mario! Around the Mushroom Kingdom, I am known as a hero, a plumber, a doctor, a golfer, an active olympic competitor, a basketball player, and, according to The Game Theorists, a sociopath! I am here to save the day, and so I can kill someone during the day, and I won't be revealed! However, it isn't safe to claim, so I should use /fire during the night to shoot fireballs into the air. Yoshi might notice this, and if he does, he may be able to contact me and protect me during the night! Rosalina can also give me some power-ups during the night, but only if she can find me with her inspect.",
			"info" : "Can kill one person during the day (won't be revealed). Can use /fire during the night, a command which can be haxed by Yoshi. Sided with the Mushroom Kingdom.",
			"actions" : {
				"night" : {
					"fire" : {
						"command" : "dummy",
						"target" : "OnlySelf",
						"restrict" : [
							"fire"
						],
						"common" : "Role",
						"priority" : 99
					}
				},
				"standby" : {
					"kill" : {
						"target" : "AnyButSelf",
						"msg" : "Woah, I found a Fire Flower! I can now /kill [name] someone without being revealed!",
						"killmsg" : "Wahoo! Mario grabs a Fire Flower and shoots a powerful fire ball at ~Target~, incinerating them!"
					}
				}
			}
		}, {
			"role" : "steelmario",
			"side" : "village",
			"translation" : "Steel Mario",
			"help" : "Wahoo! Rosalina put a spell on me and turned me into Steel Mario! I can still kill someone during the day without being revealed, and I now evade all night kills! I will turn back into my normal form after 2 days, but I should be wary of Kamek, who can turn me back into my normal form prematurely!",
			"info" : "Can kill one person during the day (won't reveal). Evades all night kills. Converts back to Mario after 2 nights. Sided with the Mushroom Kingdom.",
			"actions" : {
				"standby" : {
					"kill" : {
						"target" : "AnyButSelf",
						"msg" : "My iron fists should be enough to take down my opponents! I can do so with /kill [name], and I won't be revealed.",
						"killmsg" : "With an iron fist, Mario punches ~Target~ and knocks them all the way into outer space and out of the Mushroom Kingdom!"
					}
				},
				"kill" : {
					"mode" : "ignore"
				},
				"initialCondition" : {
					"curse" : {
						"cursedRole" : "mario",
						"curseCount" : 3,
						"curseConvertMessage" : "Rosalina's spell has worn off, and ~Old~ has changed back into ordinary ~New~."
					}
				}
			}
		}, {
			"role" : "icemario",
			"side" : "village",
			"translation" : "Ice Mario",
			"help" : "Brrrr! Rosalina has turned me into an icy form of my self known as Ice Mario! With my ability to conjure ice and snow, I can /distract [name] TWO people during the night! I can still kill someone during the day without being revealed. I will turn back into my normal form after 2 days, but I should be wary of Kamek, who can turn me back into my normal form prematurely!",
			"info" : "Can kill one person during the day (won't reveal). Can distract two people during the night. Converts back to Mario after 2 nights. Sided with the Mushroom Kingdom.",
			"actions" : {
				"night" : {
					"distract" : {
						"target" : "AnyButSelf",
						"common" : "Self",
						"priority" : 1,
						"limit" : 2,
						"msg" : "Huh? Why can't I move? Hey...how did my feet get frozen to the ground?!",
						"teammsg" : "Somehow, my teammate's feet got frozen to the ground, so we weren't able to ~Action~ tonight."
					}
				},
				"standby" : {
					"kill" : {
						"target" : "AnyButSelf",
						"msg" : "With my chilly powers, I can now freeze my opponents with /kill [name]. I won't be revealed!",
						"killmsg" : "Ice Mario shoots a powerful blast of ice and snow at ~Target~, freezing them instantly! He then finishes his target off by jumping on top of the ice, breaking it into a million pieces!"
					}
				},
				"initialCondition" : {
					"curse" : {
						"cursedRole" : "mario",
						"curseCount" : 3,
						"curseConvertMessage" : "Rosalina's spell has worn off, and ~Old~ has changed back into ordinary ~New~."
					}
				}
			}
		}, {
			"role" : "raccoonmario",
			"side" : "village",
			"translation" : "Raccoon Mario",
			"help" : "With some magic from a Super Leaf, Rosalina has transformed me into Raccoon Mario! By wagging my tail around during the day, I can kill someone without being revealed. Rosalina's spell has also given me the ability to protect AND safeguard someone during the night (only one command for this) with /fullbg [name]. I will turn back into my normal form after 2 days, but I should be wary of Kamek, who can turn me back into my normal form prematurely!",
			"info" : "Can kill one person during the day (won't reveal). Can protect AND safeguard someone during the night (only one command for this). Converts back to Mario after 2 nights. Sided with the Mushroom Kingdom.",
			"actions" : {
				"night" : {
					"fullbg" : {
						"target" : "AnyButSelf",
						"common" : "Self",
						"priority" : 5,
						"command" : ["protect", "safeguard"]
					}
				},
				"standby" : {
					"kill" : {
						"target" : "AnyButSelf",
						"msg" : "By wagging my tail around, I can now knock my opponents out of the Mushroom Kingdom with /kill [name]. I won't be revealed!",
						"killmsg" : "With just the wag of his tail, Raccoon Mario slaps ~Target~ out of the Mushroom Kingdom, never to be seen again!"
					}
				},
				"initialCondition" : {
					"curse" : {
						"cursedRole" : "mario",
						"curseCount" : 3,
						"curseConvertMessage" : "Rosalina's spell has worn off, and ~Old~ has changed back into ordinary ~New~."
					}
				}
			}
		}, {
			"role" : "flymario",
			"side" : "village",
			"translation" : "Flying Mario",
			"help" : "I believe I can fly...I believe I can touch the sky...Weee! I can fly now! Rosalina's spell has given me the ability to both inspect AND watch someone during the night (only one command for this) with /inspect [name]. During the day, I can kill someone without being revealed. I will turn back into my normal form after 2 days, but I should be wary of Kamek, who can turn me back into my normal form prematurely!",
			"info" : "Can kill one person during the day (won't reveal). Can inspect AND watch someone during the night (only one command for this). Converts back to Mario after 2 nights. Sided with the Mushroom Kingdom.",
			"actions" : {
				"night" : {
					"inspect" : {
						"target" : "AnyButSelf",
						"common" : "Self",
						"priority" : 50,
						"command" : ["inspect", "watch"]
					}
				},
				"standby" : {
					"kill" : {
						"target" : "AnyButSelf",
						"msg" : "I can now soar through the sky and defeat my opponents with /kill [name]. I won't be revealed!",
						"killmsg" : "It's a bird! It's a plane! Wait, no...It's Flying Mario, dropping ~Target~ from an unbelievable height! Ouch, that's gotta hurt!"
					}
				},
				"initialCondition" : {
					"curse" : {
						"cursedRole" : "mario",
						"curseCount" : 3,
						"curseConvertMessage" : "Rosalina's spell has worn off, and ~Old~ has changed back into ordinary ~New~."
					}
				}
			}
		}, {
			"role" : "goldmario",
			"side" : "village",
			"translation" : "Gold Mario",
			"help" : "Woah! I'm...I'm...I'm golden! This is amazing! Rosalina's spell has given me the ability to kill an extra opponent during the day (with a hight chance of revealing myself)! My non-revealing daykill, however, is still in tact. I will turn back into my normal form after 2 days, but I should be wary of Kamek, who can turn me back into my normal form prematurely!",
			"info" : "Can kill one person during the day (won't reveal). Has a second daykill with a high chance of revealing. Converts back to Mario after 2 nights. Sided with the Mushroom Kingdom.",
			"actions" : {
				"standby" : {
					"kill" : {
						"target": "AnyButSelf",
						"limit": 1,
						"msg": "I can turn my enemies into gold coins now with /kill [name] without being revealed!",
						"killmsg": "Woah! Golden Mario fires a golden fireball at ~Target~, turning them into a golden coin!"
					},
					"kill": {
						"target" : "AnyButSelf",
						"limit" : 2,
						"msg" : "I also have the chance to /kill [name] an additional person, but I have a high chance of being revealed!",
						"killmsg" : "What's this? Golden Mario shoots an even bigger golden fire ball at ~Target~, turning them into a giant bag of gold coins!",
						"revealChance" : 0.7,
						"revealmsg" : "~Self~ collects the large bag of gold coins so he can use them at Toad's item shop!"
					}
				},
				"initialCondition" : {
					"curse" : {
						"cursedRole" : "mario",
						"curseCount" : 3,
						"curseConvertMessage" : "Rosalina's spell has worn off, and ~Old~ has changed back into ordinary ~New~."
					}
				}
			}
		}, {
			"role" : "babymario",
			"side" : "village",
			"translation" : "Baby Mario",
			"help" : "Waaaaah! Waaaaaaah! Rosalina's spell backfired, and she accidentally turned me into a baby! I can still kill someone during the day, but since I'm a baby I'll probably fail. My vote counts as 0, and I have a 50% chance of avoiding Yosh's shield! And to make matters worse, I'll only change back after 2 nights! This stinks!",
			"info" : "Can kill one person during the day (will always fail). Vote counts as 0. Has a 50% chance of ignoring Yoshi's shield command. Converts back to Mario after 2 nights. Sided with the Mushroom Kingdom.",
			"actions" : {
				"standby" : {
					"kill" : {
						"target" : "AnyButSelf",
						"command" : "expose",
						"msg" : "I can try to /kill [name] someone, but I will probably fail since I'm just a baby.",
						"exposemsg" : "Baby Mario tried to kill ~Target~ but failed."
					}
				},
				"shield": {
					"mode": {"evadeChance": 0.5},
					"silent": true
				},
				"initialCondition" : {
					"curse" : {
						"cursedRole" : "mario",
						"curseCount" : 3,
						"curseConvertMessage" : "Rosalina's spell has worn off, and ~Old~ has changed back into ordinary ~New~."
					}
				}
			}
		}, {
			"role" : "goomba",
			"side" : "maf1",
			"translation" : "Goomba",
			"help" : "Bowser has called me in to help him in his conquest to take over Mushroom Kingdom and promises a big reward if I help him succeed! I can /kill [name] someone during the night (shared with my team), but I should be careful because Toad might catch me doing so. If Bowser is alive, I should probably let him do all the killing since he can't be haxed by the Toads. [Use /tt [message] to talk to your teammates.]",
			"info" : "Can kill one person during the night (shared with team). Sided with Bowser's Kingdom.",
			"actions" : {
				"night" : {
					"kill" : {
						"target" : "AnyButTeam",
						"common" : "Team",
						"priority" : 30,
						"broadcast" : "team",
						"broadcastmsg" : "~Player~, the Goomba, thinks we should kill ~Target~!",
						"hide" : true
					}
				},
				"startup" : "team-reveal-with-roles",
				"teamTalk" : true,
				"preventTeamvote" : true
			}
		}, {
			"role" : "bowserjr",
			"side" : "maf1",
			"translation" : "Bowser Jr.",
			"help" : "My dad wants me to grow up just like him, and so he has asked me to fight in this giant war! I can /kill [name] someone during the night (shared with my team), but those darn Toads might catch me doing so, meaning I should probably like Dad kill (he can't be haxed). In addition to that, I can /protect [name] someone during the night to keep them safe from enemy fire. Kamek has also put a spell on me which makes me inspect as a Toad, allowing me to blend in a little better. [Use /tt [message] to talk to your teammates.]",
			"info" : "Can kill one person during the night (shared with team). Can protect one person during the night. Inspects as Toad. Sided with Bowser's Kingdom.",
			"actions" : {
				"night" : {
					"kill" : {
						"target" : "AnyButTeam",
						"common" : "Team",
						"priority" : 25,
						"broadcast" : "team",
						"broadcastmsg" : "~Player~ (Bowser Jr.) thinks we should kill ~Target~!",
						"hide" : true
					},
					"protect" : {
						"target" : "AnyButSelf",
						"common" : "Self",
						"priority" : 11,
						"broadcast" : "team",
						"broadcastmsg" : "~Player~ (Bowser Jr.) is going to protect ~Target~!"
					}
				},
				"inspect" : {
					"revealAs" : "villager"
				},
				"startup" : "team-reveal-with-roles",
				"teamTalk" : true,
				"preventTeamvote" : true
			}
		}, {
			"role" : "bowser",
			"side" : "maf1",
			"translation" : "Bowser",
			"help" : "ROAAAARR! I am Bowser, ruler of my kingdom, ought to take over the Mushroom Kingdom and defeat Mario once and for all! I can /kill [name] someone during the night and one person per game during the day (I won't be revealed). I am also immune to any form of distraction. And since I can't be haxed, I should probably decide who my team is going to kill during the night! [Use /tt [message] to talk to your teammates.]",
			"info" : "Can kill one person during the night (shared with team, can't be haxed). Can kill one person per game during the day (won't be revealed). Ignores distraction. Sided with the Mushroom Kingdom.",
			"actions" : {
				"night" : {
					"kill" : {
						"target" : "AnyButTeam",
						"common" : "Team",
						"priority" : 20,
						"broadcast" : "team",
						"broadcastmsg" : "~Player~ (Bowser) thinks we should kill ~Target~! (Bowser can't be haxed)",
						"hide" : true
					}
				},
				"standby" : {
					"kill" : {
						"target" : "AnyButTeam",
						"msg" : "I can now /kill [name] someone, but I can only do this once per game, so I better use it wisely!",
						"killmsg" : "ROAAAARR! Bowser engulfs ~Target~ in flames, burning them to a crisp!"
					}
				},
				"distract" : {
					"silent" : true,
					"mode" : "ignore"
				},
				"avoidHax" : [
					"kill"
				],
				"startup" : "team-reveal-with-roles",
				"teamTalk" : true,
				"preventTeamvote" : true
			}
		}, {
			"role" : "kamek",
			"side" : "maf1",
			"translation" : "Kamek",
			"help" : "I've been chasing Mario since he was a baby, and now, I've joined forces with Bowser in order to beat him! In order to achieve my goal, I can /kill [name] someone during the night (shared with my team). Rosalina also thinks it's funny to give power-ups to Mario, so I'm here to stop her as well! I can cast a /spell [name] on any of Mario's forms and turn him back into his base form, making it easier to take him down! Use /tt [messge] to talk to your teammates.",
			"info" : "Can kill one person during the night (shared with team). Can convert any of Mario's forms back into his base form. Sided with Bowser's Kingdom.",
			"actions" : {
				"night" : {
					"kill" : {
						"target" : "AnyButTeam",
						"common" : "Team",
						"priority" : 27,
						"broadcast" : "team",
						"broadcastmsg" : "~Player~ (Kamek) thinks we should kill ~Target~!",
						"hide" : true
					},
					"spell" : {
						"target" : "AnyButTeam",
						"common" : "Self",
						"priority" : 46,
						"command" : "convert",
						"newRole" : "mario",
						"canConvert" : [
							"steelmario", "icemario", "raccoonmario", "flymario", "goldmario"
						],
						"convertmsg" : "Oh no! Kamek put a spell on ~Old~ and turned them back into ordinary ~New~!"
					}
				},
				"startup" : "team-reveal-with-roles",
				"teamTalk" : true,
				"preventTeamvote" : true
			}
		}, {
			"role" : "boo",
			"side" : "maf2",
			"translation" : "Boo",
			"help" : "Kekeke! I'm Boo, a minion of King Boo! I can /kill [name] someone during the night (shared with team), and in addition to that, I can /scare [name] someone during the night and prevent them from acting! Luigi is a scaredy cat, so if I scare him, he'll die instantly! However, he has been hunting down Boo for years, so if he happens to stalk me, he'll kill me instead!",
			"info" : "Can kill one person during the night (shared with team). Can distract one person during the night. Dies if stalked by Luigi. Sided with King Boo's Army.",
			"actions" : {
				"night" : {
					"kill" : {
						"target" : "AnyButTeam",
						"common" : "Team",
						"priority" : 28,
						"broadcast" : "team",
						"broadcastmsg" : "~Player~ (Boo) wants to kill ~Target~!",
						"hide" : true
					},
					"scare" : {
						"command" : ["distract", "dummy2"],
						"target" : "AnyButTeam",
						"common" : "Self",
						"priority" : 1,
						"broadcast" : "team",
						"broadcastmsg" : "~Player~ (Boo) is going to scare ~Target~!",
						"distractmsg" : "Ahhhh! Boo scared me last night, and I couldn't do anything!",
						"teammsg" : "My teammate got so spooked up by Boo last night that we weren't able to ~Action~."
					}
				},
				"dummy3" : {
					"mode" : "die",
					"msg" : "Oh no! Luigi sucked me up with his Poltergust after trying to stalk me last night!",
					"targetmsg" : "Ohmigosh, a Boo! Out of instinct, I sucked it up with my Poltergust!"
				},
				"startup" : "team-reveal-with-roles",
				"teamTalk" : true,
				"preventTeamvote" : true
			}
		}, {
			"role" : "kingboo",
			"side" : "maf2",
			"translation" : "King Boo",
			"help" : "Kekeke! I am King Boo, leader of the dead army! With my team, I can /kill [name] someone during the night (this is shared with my team)! During the day, I can scare someone, and their role will be revealed to me only! Also, Princess Peach has a vote of 20, so in order to counter her, my vote counts as negative 20! I can use this to save my teammates during the voting phase! [Use /tt [message] to talk to your teammates.]",
			"info" : "Can kill one person during the night (shared with team). Can inspect one person during the day. Vote counts as -20. Sided with King Boo's Army.",
			"actions" : {
				"night" : {
					"kill" : {
						"target" : "AnyButTeam",
						"common" : "Team",
						"priority" : 21,
						"broadcast" : "team",
						"broadcastmsg" : "~Player~ (King Boo) wants to kill ~Target~!",
						"hide" : true
					}
				},
				"standby" : {
					"scare" : {
						"command" : "expose",
						"target" : "AnyButTeam",
						"msg" : "I can now /scare [name] someone and discover their role! :",
						"exposemsg" : "King Boo pops up behind ~Role~ and scares them! \"Ahhhh!\"",
						"exposedtargetmsg" : "By scaring ~Target~, you were able to identify them as ~Role~!"
					}
				},
				"startup" : "team-reveal-with-roles",
				"teamTalk" : true,
				"preventTeamvote" : true,
				"vote" : -20
			}
		}, {
			"role" : "drybones",
			"side" : "maf2",
			"translation" : "Dry Bones",
			"help" : "Made of dust, dirt, sand, and bones, I am Dry Bones. In order to live in a world of the non-living, I have decided to side with King Boo and his army in order to take control of the Mushroom Kingdom. I have the ability to /kill [name] someone during the night (shared with my team). Since my bones re-assemble when I am defeated, I have the ability to survive one lynch, and if I am voted off, my kill will ignore distractions. [Use /tt [message] to talk to your teammates.]",
			"info" : "Can kill one person during the night (shared with team). If lynched, will survive and will ignore distraction. Sided with King Boo's Army.",
			"actions" : {
				"night" : {
					"kill" : {
						"target" : "AnyButTeam",
						"common" : "Team",
						"priority" : 29,
						"broadcast" : "team",
						"broadcastmsg" : "~Player~ (Dry Bones) wants to kill ~Target~!",
						"hide" : true
					}
				},
				"lynch" : {
					"convertTo" : "dryb",
					"convertmsg" : "Dry Bone's body re-assembled before being voted off and he was able to survive the lynch!"
				},
				"startup" : "team-reveal-with-roles",
				"teamTalk" : true,
				"preventTeamvote" : true
			}
		}, {
			"role" : "dryb",
			"side" : "maf2",
			"translation" : "Dry Bones",
			"hide" : true,
			"help" : "It seems that I was almost voted off, but I was able to re-assemble my body and survive the lynch! However, I won't survive the next one, so I should still be careful. I still have the ability to /kill [name] someone during the night (shared with my team), but I now ignore distraction! [Use /tt [message] to talk to your teammates.]",
			"actions" : {
				"night" : {
					"kill" : {
						"target" : "AnyButTeam",
						"common" : "Team",
						"priority" : 29,
						"broadcast" : "team",
						"broadcastmsg" : "~Player~ (Dry Bones) wants to kill ~Target~!",
						"hide" : true
					}
				},
				"distract" : {
					"silent" : true,
					"mode" : "ignore"
				},
				"startup" : "team-reveal-with-roles",
				"teamTalk" : true,
				"preventTeamvote" : true
			}
		}, {
			"role" : "wario",
			"side" : "maf3",
			"translation" : "Wario",
			"help" : "Wah hah! I am Wario, the evil cousin of Mario! I'm here to drive everyone out of the Mushroom Kingdom with my brother, Waluigi, in order to turn it into Waft City! I can /fart [name] on someone during the night (shared with my brother) and they'll die from the smell. Since nobody ever wants to get near me, I avoid all night kills! And since I smell so bad, inspectors never really want to get near me, so they assume that I'm a Toad. [Use /tt [message] to talk to your teammates.]",
			"info" : "Can kill one person during the night (shared with team). Avoids all night kills. Inspects as a Toad. Sided with the Deadly Duo.",
			"actions" : {
				"night" : {
					"kill" : {
						"target" : "AnyButTeam",
						"command" : "kill",
						"common" : "Team",
						"priority" : 23,
						"broadcast" : "team",
						"broadcastmsg" : "~Player~ (Wario) wants to fart on ~Target~!",
						"hide" : true
					}
				},
				"kill" : {
					"silent" : true,
					"mode" : "ignore"
				},
				"startup" : "team-reveal-with-roles",
				"teamTalk" : true,
				"preventTeamvote" : true
			}
		}, {
			"role" : "waluigi",
			"side" : "maf3",
			"translation" : "Waluigi",
			"help" : "Ahaha! I am Waluigi, Wario's evil brother and arch-enemy of Luigi! Just like my brother, I am here to drive everyone out of the Mushroom Kingdom! I can /kill [name] someone during the night (shared with my brother), and every other night, I can kill an additional person with /kill2 [name] (not shared with my brother)! If anyone happens to distract me, I will be able to identify who they are, and hopefully be able to take them down!",
			"info" : "Can can one person during the night (shared with team). Can kill an additional person every other night with /kill2. Identifies distractors. Sided with the Deadly Duo.",
			"actions" : {
				"night" : {
					"kill" : {
						"target" : "AnyButTeam",
						"common" : "Team",
						"priority" : 23,
						"broadcast" : "team",
						"broadcastmsg" : "~Player~ (Waluigi) wants to kill ~Target~!",
						"hide" : true
					},
					"kill2" : {
						"command" : "kill",
						"target" : "AnyButTeam",
						"common" : "Self",
						"priority" : 17,
						"broadcastmsg" : "~Player~ (Waluigi) wants to use his extra kill on ~Target~!",
						"recharge" : 2
					}
				},
				"distract" : {
					"mode" : "identify",
					"msg" : "Well, would you look at this? It seems as if ~Target~ distracted me last night."
				},
				"startup" : "team-reveal-with-roles",
				"teamTalk" : true,
				"preventTeamvote" : true
			}
		}, {
			"role" : "fawful",
			"side" : "maf4",
			"translation" : "Fawful",
			"help" : "I HAVE FURY!! I am here to defeat Mario and Luigi for what they did to me long ago! I am by myself, but who cares? I can /kill [name] someone during the night, and to keep myself alive, I can /protect [name] myself during the night! I ignore all distraction, and I have a voteshield of -5, meaning I ignore five votes counted towards me! Also, I HAVE FURY!!",
			"info" : "Can kill one person during the night. Can protect himself during the night. Ignores distraction. Voteshield of -5. I HAVE FURY!! Sided with himself.",
			"actions" : {
				"night" : {
					"kill" : {
						"target" : "AnyButSelf",
						"common" : "Self",
						"priority" : 15
					},
					"protect" : {
						"target" : "OnlySelf",
						"common" : "Self",
						"priority" : 4
					}
				},
				"distract" : {
					"mode" : "ignore",
					"msg" : "Someone tried to distract me last, but I simply ignored them because I'm awesome."
				},
				"voteshield" : -5
			}
		}
	],
	"roles1": [
        "mario",
        "boo",
        "villager",
        "villager"
    ],
    "roles2": [
    	"mario",
    	"srosalina",
    	"villager",
    	"villager",
    	"boo",
    	"boo",
    	"yoshi"
    ],
    "roles3": [
    	"mario",
    	"villager",
    	"rosalina",
    	"yoshi",
    	"villager",
    	"toadsworth",
    	"goomba",
    	"goomba",
    	"kamek",
    	"daisy",
    	"villager",
    	"peach",
    	"kingboo",
    	"bowser",
    	"luigi",
    	"villager",
    	"peach",
    	"kingboo",
    	"boo",
    	"boo"
    ],
    "roles4": [
    	"mario",
    	"villager",
    	"rosalina",
    	"yoshi",
    	"villager",
    	"toadsworth",
    	"goomba",
    	"goomba",
    	"kamek",
    	"daisy",
    	"villager",
    	"villager",
    	"bowser",
    	"goomba",
    	"luigi",
    	"peach",
    	"kingboo",
    	"boo",
    	"boo",
    	"villager",
    	"bowserjr",
    	"birdo",
    	"villager",
    	"fawful",
    	"wario",
    	"waluigi",
    	"villager",
    	"villager",
    	"goomba",
    	"boo"
    ],
    "roles5": [
    	"mario",
    	"villager",
    	"rosalina",
    	"yoshi",
    	"villager",
    	"toadsworth",
    	"goomba",
    	"goomba",
    	"kamek",
    	"daisy",
    	"villager",
    	"villager",
    	"bowser",
    	"goomba",
    	"luigi",
    	"peach",
    	"kingboo",
    	"drybones",
    	"boo",
    	"villager",
    	"fawful",
    	"wario",
    	"waluigi",
    	"boo",
    	"villager",
    	"goomba",
    	"boo",
    	"villager",
    	"villager",
    	"villager",
    	"goomba",
    	"boo",
    	"boo",
    	"goomba",
    	"villager",
    	"villager",
    	"goomba",
    	"villager",
    	"villager",
    	"villager",
    	"villager",
    	"boo",
    	"goomba",
    	"villager",
    	"boo",
    	"villager"
    ],
	"killmsg" : "~Player~ (~Role~) ran out of lives!",
	"killusermsg" : "*** Game Over! Restart / Quit",
	"lynchmsg" : "~Player~ (~Role~) was kicked out of the Mushroom Kingdom!",
	"tips" : {
		"Mario" : "It isn't safe to claim! Doing so can result in the death of Yoshi, and Bowser can kill during the day.",
		"Yoshi" : "Remember, if someone targets the person you shield, you will die instead! Also, make sure to PM Mario ASAP if you happen to hax his /fire command!",
		"Rosalina" : "You can only use each of your spells once, so make sure you use them on someone you know for sure is Mario!",
		"Main Threats": "Bowser (one time daykill, ignores PL and hax), King Boo (day inspect and -20 vote), Fawful (fastest kill, self-bg, ignores PL).",
		"Bowser's Kingdom" : "If Bowser is alive, let him do the killing; he can't be haxed.",
		"King Boo's Army" : "Remember that Boo will die if he is stalked by Luigi! King Boo has a vote of -20 in order to counter Peach, but be careful when voting for yourself!",
		"Deadly Duo" : "Waluigi's /kill2 should be used carefully! Wario inspects as Toad and Waluigi identifies his distractors.",
		"Fawful" : "You're alone, but you have the fastest kill in the game, you have a self-protect, and you ignore any distractions."
	},
	"changelog": {
		"4.3.15": "Theme completed. (Special thanks to RiceKirby, Miki Sayaka, and obey to kyubey for helping me out with lots of the coding)."
	},
	"minplayers" : 3,
	"villageCantLoseRoles" : [
		"mario",
		"peach",
		"steelmario",
		"icemario",
		"raccoonmario",
		"flymario",
		"goldmario"
	]
}
