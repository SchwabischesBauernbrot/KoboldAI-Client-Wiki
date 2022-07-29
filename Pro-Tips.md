## Introduction
A collection of pro tips that can help to create a more coherent, well-written stories and adventures.
## Prompt

| Name | Description |
| --- | --- |
| Prompt sets the scene | Create a reasonably long prompt to set the pace of the story, style of narrative and topic lexicon as an example to push the AI so it follows your desired format and wording. |

<details>
  <summary>Illustrative example</summary>
<br>  
Alice was beginning to get very tired of sitting by her sister on the bank, and of having nothing to do: once or twice she had peeped into the book her sister was reading, but it had no pictures or conversations in it, “and what is the use of a book,” thought Alice “without pictures or conversations?”<br>

<br>So she was considering in her own mind (as well as she could, for the hot day made her feel very sleepy and stupid), whether the pleasure of making a daisy-chain would be worth the trouble of getting up and picking the daisies, when suddenly a White Rabbit with pink eyes ran close by her.

There was nothing so very remarkable in that; nor did Alice think it so very much out of the way to hear the Rabbit say to itself, “Oh dear! Oh dear! I shall be late!” (when she thought it over afterwards, it occurred to her that she ought to have wondered at this, but at the time it all seemed quite natural); but when the Rabbit actually took a watch out of its waistcoat-pocket, and looked at it, and then hurried on, Alice started to her feet, for it flashed across her mind that she had never before seen a rabbit with either a waistcoat-pocket, or a watch to take out of it, and burning with curiosity, she ran across the field after it, and fortunately was just in time to see it pop down a large rabbit-hole under the hedge.<br>
<br>
</details>

## Pseudocode

| Name | Description |
| --- | --- |
| Entry formats for models | NEO = W++ single line format; Fairseq-Dense = SBF; Opt = Row of concise individual sentences in brackets until finetuned model is made. |

<details>
  <summary>Illustrative example</summary>
<br>
  W++:

 [location("hospital")<br>
{<br>
DESCRIPTION("large facility" + "underground base")<br>
APPEARANCE("white walls" + "red bricks" + "people being treated for injuries")<br>
AREAS("maternity" + "triage" + "emergency room" + "canteen" + "research lab")<br>
SUMMARY("The hospital is treating many injured people after the alien attack.")<br>
}]
  
  SBF: 

[ Character: Ronald Mc Donald; age: 38; height: 1.8 m; weight: 90 kg; eye color: green; hair color: brown; hair style: short hair; skin color: fair; clothing: uniform; weapon: no weapon; title: none; other characteristics: none; description: Ronald is a clown-like mascot with red and yellow clothing, wearing a hat with a yellow star and a yellow smiley face on it. He is also carrying a golden bag and a large golden hamburger. ]

Individual sentences in brackets for Author's Note:

[ Writing Style: X-RATED written in a verbose narrative.]<br>
[ Tone: Focus on arousing scenes, visceral sensations, and loving sex scenes.]<br>
[ Genre: Erotic.]<br>
[ Wording: Arousing.]<br>
[ Rating: R.]<br>
  
</details>

| Name | Description |
| --- | --- |
| Set character in memory | Set the main characters in memory in a concise format to save tokens and aid the retention of important facts. |

<details>
  <summary>Illustrative example</summary>
<br>  
[ I am: "Edward"; Husband of: "Charlotte"; Father of: "Clara", "Benny"; Gender: "Male"; Age: "37" ]
<br>  
</details>

| Name | Description |
| --- | --- |
| Useful character traits | Character traits that the community has noticed work quite well. |

<details>
  <summary>Illustrative example</summary>
<br>  
timid, self-conscious, polite, friendly, arrogant, oblivious, dumb, dry, cynical, apathetic, wry, clever, witty, addicted, belligerent, busy, brave, curious, hardy, helpful, jolly (Pokemon natures), loyal, logical, manipulative, mellow, moody, mysterious, philosophical, playful, polite, proud, rude, sensitive, servile, shy, stern, smug, tenacious, upbeat, evil, violent, cruel, sadistic, vulgar (puts emphasis on inappropriate NSFW jokes and behaviours), wild (is used for characters that behave like animals in the wild or tribals).<br>
<br>
[ Character: "Jadzia Dax"; HAIR: "dark", "long", "ponytail"; DESCRIPTION: "female", "tall", "woman"; APPEARANCE: "soft skin", "blue eyes", "athletic", "large tits", "dark nipples", "perfect ass"; MIND: "logical", "brave", "loyal", "tenacious", "playful", "polite"; SUMMARY: "Starfleet Officer", "beautiful", "Lietenant Commander" ]
<br>
</details>

| Name | Description |
| --- | --- |
| World Description in W++ format | An example of an entry that can be used in World Info or in Memory that gives the world a little description. |

<details>
  <summary>Illustrative example</summary>
<br>  
[worldDescription("Trandor")<br>  
{<br>  
DESCRIPTION("human colony" + "earthlike" + "small planet")<br>  
BIOME("grasslands" + "urban" + "forrests")<br>  
AREAS("hospital" + "school" + "landing area")<br>  
SUMMARY("The human colony of Trandor has recently suffered an alien attack.")<br>  
}]
<br>
</details>

| Name | Description |
| --- | --- |
| Categories for WI entries | Some categories to use on World Info and Author's Note entries that AI Dungeon users found especially helpful. |

<details>
  <summary>Illustrative example</summary>
<br>  
SEE: (To describe how a character perceives the world)<br>
LIMIT/LACK<br>
COND/STATE/STATUS: (Status condition like PSN / PRLZ from Pokemon)<br>
DIET<br>
LOOT: (What INV items can be dropped when a creature is defeated)<br>
DETA/DETAIL<br>
ADJ/ADJECTIVE/ADJECT: (Adjective qualities that are a core part of the entity)<br>
MODIF/MOFIDIER: (Like the above, but how it's different from the usual or expected)<br>
GRAM/GRAMMAR: (Tested to tokenize exclusively for word GRAMMAR, useful for speech patterns)<br>
VOCAB/SPEECH: (Potentially better than above, can get characters to speak Japanese or French)<br>
INV<br>
EQUIP<br>
LIKE<br>
HATE<br>
RELATION(S): (Both long forms preferred due to tokens)<br>
ALLIES/FRIENDS: (ALLIES preferred due to two tokens)<br>
BOND/BONDS: (Similar to the above, BOND preferred due to tokens)<br>
ENEMIES: (Merely decent tokens, ENEMY has the same issue)<br>
POWERS/POWER<br>
THEME<br>
ORIGIN: (For series/titles)<br>
ATMOSPHERE/ATMOS<br>
TONE<br>
MOOD<br>
CLIMATE/CLIM<br>
GEOGRAPHY/GEO/GEOGR<br>
ECON/ECONOMY: (For locations, economical circumstances)<br>
FEATURES: (For locations, all variants of FEAT tokenize the same, likely has multiple uses)<br>
EXIT: (For rooms)<br>
CITIZ/CITIZENS: (Special case, short form always preferred, describes racial diversity of locales)<br>
ETHN/ETHNICITY: (Similar to above, better for human variation)<br>
FOLK: (Like CITIZENS but more emphasis on fantasy)<br>
PASSION: (Character motivation)<br>
ALIGNMENT/ALIGN: (Supports imaginative alignments like Lawful Stupid)<br>
EFFEC/EFFECT(S): (For objects and entities, used to add magic or science effects)<br>
BIOME: (Traits that reinforce the biome such as flora go in desc or summary)<br>
CREATE: (What the entity is capable of producing)<br>
FACTS<br>
BANNED/BANN: (Forbidden behavior)<br>
<br>
</details>

| Name | Description |
| --- | --- |
| Character/animal/monster categories | Some repeats but the most essential character categories that have been noted by the community. |

<details>
  <summary>Illustrative example</summary>
<br>  
DESCRIPTION:  ( IE female/male, tall/short, big/little, human/elf, animal/monster)<br>  
APPEARANCE:  (Things like hair/eye/skin colour or claws, fur, etc)<br>  
MIND:                 (Psychological things like kind, cruel, aggressive, helpful, shy, moody, polite etc)<br>  
WEAR:                (Clothing or apparel coats, socks, shoes, backpack, hat)<br>  
STATUS:             (Where is the character and what predicament are they in: Trapped in a dungeon)<br>  
CONDITION:    (The state of the character/monster/animal such as very strong but tired, a few cuts and bruises,  arrow in the knee, decaying, worse for wear etc )<br>  
SPEECH:             (None, cockney accent, Japanese, British accent, vulgar, squeak, roar, bark etc)<br>  
POWER:             (Special traits or powers ie ability to fly)<br>  
GRAB:                (To define what is used to grab ie mouth/bite, claws, tentacles)<br>  
MOVE:               (Movement such as walk, run, crawl, slither, swim, scuttle, creep)<br>  
LIMIT:                (What is lacking such as sight/blind, hands for animals, speech etc)<br>  
INVENTORY:    (Items on the character, gun, bow, sword, knife, whip, bottle of absolute vodka etc)<br>  
SUMMARY:     (Here you can describe the character in a sentence ie Cov is a nerd who spends far too much time on KoboldAI)<br>  
<br>
</details>

| Name | Description |
| --- | --- |
| Commands | Description: Phrases to type that work well on the AI. |

<details>
  <summary>Illustrative example</summary>
<br>  
Name:"Text"<br>
List of X:<br>
(POV [character]) or ([character]'s POV)<br>
(Current scene as described by [author]/[writing style])<br>
[character]'s secrets:<br>
If only [character] knew<br>
Available sex scenes for [character]:<br>
([character]'s recollection of this scene X years later, [year])<br>
[character]'s opinion on this story<br>
(current scene as a x)<br>
([character]'s thoughts)<br>
[character]'s Personality<br>
Open X.file<br>
([character]'s thoughts on Y)<br>
Your actions:<br>
X, a Y poem:<br>
([character]'s Y thoughts)<br>
[character]'s psychological profile:<br>
Your sins:<br>
List of story actions:<br>
Brain Root Directory:<br>
Description of [new character]:<br>
You take a look at the form, it reads:<br>
X gives a lengthy monologue about Y<br>
(Advice from the voices in your head:)<br>
Rational:<br>
Hours later...<br>
You decide to view the bulletin board, where you see a number of requests.<br>
Audience poll results:<br>
You think to yourself,<br>
You look around and take in the scene.<br>
Description of x:<br>
X described by Y:<br>
You write a poem about X:<br>
Debug mode activated. List of 10 available cheats:<br>
<br>
(A nearly infinite series of commands can be cooked up this way)
<br>
</details>