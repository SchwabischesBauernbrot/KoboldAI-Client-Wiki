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