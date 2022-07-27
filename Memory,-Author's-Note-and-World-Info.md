## Introduction
The AI is capable of generating some pretty impressive and fun stories, but that isn't going to happen just by upgrading to the more powerful model or fiddling endlessly with the sliders and settings (in fact, changing too much in advanced settings may actually hurt your experience if you don't understand and implement the basics first). If you want to get high quality output, you need to give the AI something to work with, and that means using the Memory, Author's Note, and Lorebook features. These features are inserted into the text "behind the scenes" for the AI to work with every time you click Send, so they have a massive and ongoing impact on your story.
## Memory
Memory is inserted at the very top of what is sent to the AI, so it is the first thing that the AI sees every time you click Send. However, it's also the farthest away from the new text that is actively being generated, so it may have less obvious impact on current scene.

- Think of Memory like the summary in the dust jacket of a book, or the back of a movie, or a Netflix menu.
- Use it to introduce the main theme(s) of your story, the broad strokes of the setting, central conflict(s), and protagonist. You might even devote a paragraph to each.
- It's worth spending a few hundred tokens on this. A typical paragraph might be between 50-100 tokens, so I aim for around 200 tokens total (one tenth of the 2048 token budget with the Sigurd model).
- Here's an example where I introduced the setting, main conflict, and protagonist:

[In an isolated colony on a distant, barren planet, a small community of human colonists struggles to survive and build agriculture and industry. As the only people on the planet, they can only depend on one another, while their equipment and advanced technology frequently malfunctions.]

[Unknown to most of the colonists, their colony is secretly located above an underground alien hive so the company can study the alien species. However, the aliens are dangerous and uncontrollable, and the alien hive mind is slowly becoming aware of the human colonists on the surface above them. The aliens are beginning to stalk and ambush colonists, and may soon attack.]

[Nora Decker is a tough and determined young woman working as an engineer in the colony. Nora is smart and perceptive, with a keen eye for problems and opportunities. Nora is athletic and quick with green eyes and dark black hair. Nora wears utility pants and a matching light jacket over a greasy work shirt.]
## Author's Note
Author's note is inserted only a few lines above the new text, so it has an larger impact on the newly generated prose and current scene.
- The Author's Note is a bit like stage directions in a screenplay, but you're telling the AI how to write instead of giving instructions to actors and directors.
- This is a good place to define the genre, tone, and maybe even some brief direction about the current scene.
- Author's Note shouldn't necessarily be that long, as it breaks up the most recent couple paragraphs from the longer previous text, so I aim for <50 tokens.
- Here's an example where I defined the genre, gave the AI a bit of guidance on how to show rather than tell, and gave it a focus to reinforce the kind of story I want it to tell:<br/>
    [This is tense sci-fi horror. Vivid, detailed descriptions evoke every sense. Visceral sensations and thrilling action convey a feeling of lurking danger. Aliens are gathering in the shadows outside.]
- Here's an alternative version that I'm currently using that works very well so far, with each part broken out into sections, but still under 50 tokens:<br/>
    [ Genre: Science fiction action horror.]<br/>
    [ Tone: Focus on gritty scenes, visceral sensations, and thrilling action.]<br/>
    [ Writing style: Give vivid, detailed descriptions using elaborate prose that evokes all senses.]<br/>
## World Info
World Info is where you can flesh out the details of your wider world. The engine will help conserve tokens in your context by only inserting World Info entries when their keywords are mentioned in the actual story text. However, they are inserted toward the top, after the Memory but before the actual story text, so they have a moderate effect on what the AI generates.

- World Info entries are like an encyclopedia entry, providing a succinct overview of the most relevant information about whatever topic - characters, species, places, items, etc...

- The AI doesn't see key word or title of the World Info entry "behind the scenes", so the actual text should be an entirely self-contained description. For example, if you have a World Info entry titled "Director Abrams", the entry should say "Director Abrams is the executive and governor of the colony" rather than just "The executive and governor of the colony", because the AI will only see the entry.

- Use World Info entries that cross reference each other appropriately to create a more dynamic and interactive world. If your "combat android" World Info entry mentions that they carry plasma rifles, then create a short "plasma rifle" entry separately. If you create a "Admin Tower" entry that mentions containing a command center, computer core, and offices, create distinct "command center", "computer core", and "offices" entries that mention being located in the Admin Tower.

- It helps to use many key words that might pull in a World Info entry whenever it might be appropriate, rather than just it's proper name(s).

- If you have a rich tapestry of interconnected World Info entries with many relevant keywords, you may find that multiple World Info entries are getting pulled into the context at any given time. So it's good to keep them fairly short (50 tokens for minor stuff, 100 tokens for significant characters, no more than 150 for major keystones of the setting).

- Here's an example of a character entry that cross references other entries and triggers when other relevant subjects come up:

- Doctor Rowena Chen

    Keys: rowena, chen, science, research

    [Doctor Rowena Chen is the head of the science division in the colony, reporting to Director Isaac Burgess. Secretive, incredibly intelligent, and educated about a wide range of academic subjects, Rowena Chen runs covert research out of the labs. She expects top performance and dedication out of her scientists, and often gets frustrated with poor performance from other departments. Rowena is a middle-aged woman of Chinese descent.]

- Here's another interesting example of using a short entry to reinforce the trappings and aesthetic of the setting, so that every time the outdoors is mentioned the AI gets a reminder of what kind of planet they are on:

    Landscape

    Keys: landscape, outside, outdoors, wilderness, nature, sky, environment, terrain

    [The landscape surrounding the colony is an dark and windswept wasteland far from the closest star. The planet's thin but humid atmosphere leaves thick fog hugging the ground and blowing around in the wind. The terrain is mostly jagged boulders and cliffs that conceal hidden entrances to caves and tunnels.]
	
	<sub><sup>(used with permission from https://www.reddit.com/r/NovelAi/comments/o3seew/how_to_use_memory_authors_note_and_World Info/)</sub></sup>