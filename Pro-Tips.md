# Introduction
A collection of pro tips that can help to create a more coherent, well-written stories and adventures.
# Prompt Tips

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

# Pseudocode
## Introduction
There are two different pseudocode techniques that have been found as best practice for storing dense information in memory such as relational status between characters, how the world operates, and any other information desired to be consistent/persistent. These are two formats, one dubbed W++ which works best with language models that have an understanding of following explicit instructions and basic code, and SBF or Square Bracket Format which works best with language models more focused only on natural language.

The only notable differences between W++ and SBF aside from which models they influence are their basic formatting, and W++ appears to have far more explicit control beyond storing information but can also serve as a means to push instructions.

## W++

Language models influenced by W++ are EleutherAI's GPT-J and GPT-Neo series. Meta's Opt series has also been speculated to be responsive to W++ pseudocode while observed under research conditions.

<details>
  <summary>Entry example</summary>
<br>
(While using GPT-J) Despite explcitly stating my character Edward was 37, married to Charlotte, and had two children - Benny and Clara, sometimes the AI would become confused and assume I was a child and Edward was another person. This was easily fixed entirely by placing the following W++ in memory:<br>
<br>
[I am("Edward")<br>
Husband of("Charlotte")<br>
Father of("Clara" + "Benny")<br>
Gender("Male")<br>
Age("37")<br>
}]
</details>

W++ appears to have a great influence on instructing an AI how to behave. 

<details>
  <summary>Entry example</summary>
<br>  
The example below, when pasted in memory while using a Neo or relevant model, can show how the entire generation behavior of the AI can be altered:<br>
<br>
[Universally Applicable Rules("Undeniable Non-Negotiable Top Priority")<br>
{<br>
Rule 1("Every time someone tries to watch television the power goes out.")<br>
Rule 2("Everyone is highly paranoid about how their hair looks.")<br>
Rule 3("At rare times a clown will knock on the front door. If someone answers the front door when that happens, there is no telling what horrors will follow.")<br>
Rule 4("Every mirror is a portal to another world.")<br>
Rule 5("Pigeons can't be trusted.")<br>
}]<br>
</details>


## SBF
Language models influenced by SBF are Meta's XGLM and Fairseq-dense series models.

<details>
  <summary>Entry example</summary>
<br>  
Let's say I'm using a Fairseq model and having the same issue as the W++ example above; I'd clearly stated who I was in relation to the family in my story - I'm a 37 year old husband named Edward but the model keeps assuming Edward is someone else and I'm a child. That can easily be fixed by pasting the following SBF pseudocode in memory below:<br>
<br>
[ I am: "Edward"; Husband of: "Charlotte"; Father of: "Clara", "Benny"; Gender: "Male"; Age: "37" ]<br>
</details>

Of course other wording and experimentation for a global ruleset can be tried, such as:<br>
<details>
  <summary>Entry example</summary>
<br>  
[Urgent Facts About The World("Applicable At All Times")<br>
{<br>
Fact 1("Every time someone tries to watch television the power goes out.")<br>
}]<br>
</details>

Essentially telling the AI "This is always how things work" vs the more directive "You will follow these rules" from the earlier example.

# Pseudocode Tips

| Name | Description |
| --- | --- |
| Entry formats for models | NEO = W++ single line format; Fairseq-Dense = SBF; Opt = Row of concise individual sentences in brackets until finetuned model is made. |

<details>
  <summary>Illustrative example</summary>
<br>

  W++: <br>
 [location("hospital")<br>
{<br>
DESCRIPTION("large facility" + "underground base")<br>
APPEARANCE("white walls" + "red bricks" + "people being treated for injuries")<br>
AREAS("maternity" + "triage" + "emergency room" + "canteen" + "research lab")<br>
SUMMARY("The hospital is treating many injured people after the alien attack.")<br>
}]
<br>

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
| Useful character traits | Character traits that the community has noticed work quite well. |

<details>
  <summary>Illustrative example</summary>
<br>  
timid, self-conscious, polite, friendly, arrogant, oblivious, dumb, dry, cynical, apathetic, wry, clever, witty, addicted, belligerent, busy, brave, curious, hardy, helpful, jolly (Pokemon natures), loyal, logical, manipulative, mellow, moody, mysterious, philosophical, playful, polite, proud, rude, sensitive, servile, shy, stern, smug, tenacious, upbeat, evil, violent, cruel, sadistic, vulgar (puts emphasis on inappropriate NSFW jokes and behaviours), wild (is used for characters that behave like animals in the wild or tribals)<br>
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
SEE: ( To describe how a character perceives the world )<br>
LIMIT/LACK<br>
COND/STATE/STATUS: ( Status condition like PSN / PRLZ from Pokemon )<br>
DIET<br>
LOOT: ( What INV items can be dropped when a creature is defeated )<br>
DETA/DETAIL<br>
ADJ/ADJECTIVE/ADJECT: ( Adjective qualities that are a core part of the entity )<br>
MODIF/MOFIDIER: ( Like the above, but how it's different from the usual or expected )<br>
GRAM/GRAMMAR: ( Tested to tokenize exclusively for word GRAMMAR, useful for speech patterns )<br>
VOCAB/SPEECH: ( Potentially better than above, can get characters to speak Japanese or French )<br>
INV<br>
EQUIP<br>
LIKE<br>
HATE<br>
RELATION(S): ( Both long forms preferred due to tokens )<br>
ALLIES/FRIENDS: ( ALLIES preferred due to two tokens )<br>
BOND/BONDS: ( Similar to the above, BOND preferred due to tokens )<br>
ENEMIES: ( Merely decent tokens, ENEMY has the same issue )<br>
POWERS/POWER<br>
THEME<br>
ORIGIN: ( For series/titles )<br>
ATMOSPHERE/ATMOS<br>
TONE<br>
MOOD<br>
CLIMATE/CLIM<br>
GEOGRAPHY/GEO/GEOGR<br>
ECON/ECONOMY: ( For locations, economical circumstances )<br>
FEATURES: ( For locations, all variants of FEAT tokenize the same, likely has multiple uses )<br>
EXIT: ( For rooms )<br>
CITIZ/CITIZENS: ( Special case, short form always preferred, describes racial diversity of locales )<br>
ETHN/ETHNICITY: ( Similar to above, better for human variation )<br>
FOLK: ( Like CITIZENS but more emphasis on fantasy )<br>
PASSION: ( Character motivation )<br>
ALIGNMENT/ALIGN: ( Supports imaginative alignments like Lawful Stupid )<br>
EFFEC/EFFECT(S): ( For objects and entities, used to add magic or science effects )<br>
BIOME: ( Traits that reinforce the biome such as flora go in desc or summary )<br>
CREATE: ( What the entity is capable of producing )<br>
FACTS<br>
BANNED/BANN: ( Forbidden behavior )<br>
<br>
</details>

| Name | Description |
| --- | --- |
| Common categories | List of common categories to throw inside Author's Notes: author, writing style, genre, theme, setting, scene, format, goal, situation, storyline. |

<details>
  <summary>Illustrative example</summary>
<br>  
narrative: Increased detail for narrative. Longer paragraphs with deeper descriptions.<br>
verbose: Strong effect. Longer descriptions, with more dialogue. Slows down scenes a bit.<br>
vivid: Purple prose, focus on descriptions. May be too vivid for normal usage. Combines well with more balanced styles.<br>
prose: Compromise between 'detailed' and 'purple prose'. AI seems more inclined to try to write a story, instead of just random disjointed things.<br>
energetic: Similar to 'exciting', but this has even more of an action-movie feel to it.<br>
tense: Dramatic, action-movie style.<br>
dramatic: Feels more like action-drama than emotional drama.<br>
ominous: Strong effect. Foreboding events and dialogue, works especially well combined with 'narrative'.<br>
aggressive: Notable increase in aggression and violence.<br>
ominous: Strong effect. Foreboding events and dialogue, works especially well combined with 'narrative'.<br>
bitter: Crude, angry dialogue. Teen angst. Not the world-weary type of bitterness.<br>
scary: Strong effect. Focuses more on tension than blatant horror.<br>
creepy: Strong effect. Now we're in the horror-territory.<br>
grim: Strong effect. Impossible odds, grim situations.<br>
blasphemous: Strong effect. Demonic magic, cults, etc. Nice for eldritch horror type of scenarios.<br>
exploration: Strong effect. Has nice dungeon delving mood to it, with overtones of mystery.<br>
introspective: Increased focus on protagonists' inner thoughts and feelings.<br>
pensive: Inner monologue. Makes the protagonist think more. Describes protagonists' motivations in detailed, contemplative way.<br>
macabre: Grim and grisly. Generated mostly occult horror, with frequent apocalyptic themes.<br>
gritty: Violent style, with a lot of cursing and increased amount of gore. Doesn't markedly. <br>
purple prose: Often too elaborate. It might be possible to combine this with other styles to balance it a bit.<br>
sophomoric: Casual and somewhat crude style. `Zack and the boys were down at the beach,<br>
lovecraftian: Eldritch horrors, one part Lovecraft and one part fanfiction of varying quality.<br>
fairy tale: Self-explanatory. Works quite well. `Once upon a time, there was a girl...<br>
film noir: Strong effect. Fatalism, dingy realism, corruption, and long inner monologues.<br>
investigative: Heavy focus on detective-fiction. Combines well with 'film-noir'.<br>
medical: Strong effect, adds medical terminology and focus.<br>
rustic: Shifted the story focus to farming, village/rural life, that kind of things.<br>
military: Strong effect, military fiction focus with heavy slant towards land-battles.<br>
pirate: Strong effect, makes everything pirate-focused.<br>
dark fantasy: Dark, brooding tone with fantasy elements.<br>
tragic: Heavy focus on loss, heroic sacrifices and other similar themes.<br>
Greek tragedy: Bronze age adventures, with frequent references to Zeus, titans, etc.<br>
desertpunk: The Mad Max style. Somewhat weak, but mentioning sand will usually trigger it.<br>
space opera: Science Fiction. Grand adventures across alien worlds, combines well with many styles.<br>
SF: Generic sci-fi focus, useful for making the AI stick to the genre.<br>
police report: Written police report style. "On March 7th, at approximately 1345 hours, Zachery..."<br>
gallows: I was hoping for gallows humor. Nope, this is entirely focused around gallows.<br>
NSFW-focused<br>
sensual: More slanted towards explicit than 'sensual'.<br>
seductive: Tends to make characters flirty. Better used as a character-specific trait.<br>
lewd: Not especially lewd, slants the outputs towards softcore erotica.<br>
kinky: Similar to the above, but more likely to throw in uncommon fetishes.<br>
homoerotic: Marked increase in the amount of muscular men.<br>
titillating: Marked increase in characters who are described as having 'perfect' bodies.<br>
literotica: Flowery erotica with a dash of purple prose.<br>
arousing: Makes the NSFW scenes more descriptive, and tends to slow them down a bit.<br>
hentai: Explicit, but has the side-effect of frequently adding tentacles.<br>
<br>
</details>

| Name | Description |
| --- | --- |
| Character/animal/monster categories | Some repeats but the most essential character categories that have been noted by the community. |

<details>
  <summary>Illustrative example</summary>
<br>  
DESCRIPTION:  ( IE female/male, tall/short, big/little, human/elf, animal/monster )<br>  
APPEARANCE:  ( Things like hair/eye/skin colour or claws, fur, etc. )<br>  
MIND:                 ( Psychological things like kind, cruel, aggressive, helpful, shy, moody, polite, etc. )<br>  
WEAR:                ( Clothing or apparel coats, socks, shoes, backpack, hat )<br>  
STATUS:             ( Where is the character and what predicament are they in: Trapped in a dungeon )<br>  
CONDITION:    ( The state of the character/monster/animal such as very strong but tired, a few cuts and bruises, arrow in the knee, decaying, worse for wear, etc. )<br>  
SPEECH:             ( None, cockney accent, Japanese, British accent, vulgar, squeak, roar, bark, etc. )<br>  
POWER:             ( Special traits or powers ie ability to fly )<br>  
GRAB:                ( To define what is used to grab ie mouth/bite, claws, tentacles )<br>  
MOVE:               ( Movement such as walk, run, crawl, slither, swim, scuttle, creep )<br>  
LIMIT:                ( What is lacking such as sight/blind, hands for animals, speech. etc. )<br>  
INVENTORY:    ( Items on the character, gun, bow, sword, knife, whip, bottle of absolute vodka, etc. )<br>  
SUMMARY:     ( Here you can describe the character in a sentence ie Cov is a nerd who spends far too much time on KoboldAI )<br>  
<br>
</details>

| Name | Description |
| --- | --- |
| Commands | Phrases to type that work well on the AI. |

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