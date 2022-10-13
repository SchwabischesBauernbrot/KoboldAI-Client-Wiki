## Introduction
Welcome to the KoboldAI wiki!<br>
This Wiki is maintained by KoboldAI's community based on their experience with the software.<br>

Nevertheless, the table below lists the users who have contributed the most to this Wiki.
| Nickname | Role | Pages |
| --- | --- | --- |
| ebolam | Wiki creator, Author | [KoboldAI vs AI Dungeon](https://github.com/KoboldAI/KoboldAI-Client/wiki/KoboldAI-vs-AI-Dungeon), [Memory, Author's Note and World Info](https://github.com/KoboldAI/KoboldAI-Client/wiki/Memory,-Author's-Note-and-World-Info) |
| LightSaveUs | Wiki editor, Author | [Home](https://github.com/KoboldAI/KoboldAI-Client/wiki), [F.A.Q](https://github.com/KoboldAI/KoboldAI-Client/wiki/F.A.Q), [Models](https://github.com/KoboldAI/KoboldAI-Client/wiki/Models), [Pro Tips](https://github.com/KoboldAI/KoboldAI-Client/wiki/Pro-Tips), [Settings Presets](https://github.com/KoboldAI/KoboldAI-Client/wiki/Settings-Presets) |
| VE FORBRYDERNE | Author | [Settings](https://github.com/KoboldAI/KoboldAI-Client/wiki/Settings), [Soft Prompts](https://github.com/KoboldAI/KoboldAI-Client/wiki/Soft-Prompts) |

## Your gateway to GPT writing

KoboldAI is a browser-based front-end for AI-assisted writing with multiple local and remote AI models. It offers the standard array of tools, including Memory, Author's Note, World Info, Save and Load, adjustable AI settings, formatting options, and the ability to import existing AI Dungeon adventures. You can also turn on Adventure mode and play the game like AI Dungeon Unleashed.
## Multiple ways to play
Stories can be played like a Novel, a text adventure game or used as a chatbot with an easy toggles to change between the multiple gameplay styles. This makes KoboldAI both a writing assistant, a game and a platform for so much more. The way you play and how good the AI will be depends on the model or service you decide to use. No matter if you want to use the free, fast power of Google Colab, your own high end graphics card, an online service you have an API key for (Like OpenAI or Inferkit) or if you rather just run it slower on your CPU you will be able to find a way to use KoboldAI that works for you.

### Adventure mode

By default KoboldAI will run in a generic mode optimized for writing, but with the right model you can play this like AI Dungeon without any issues. You can enable this in the settings and bring your own prompt, try generating a random prompt or download one of the prompts available at [/aids/ Prompts](https://aetherroom.club/).

The gameplay will be slightly different than the gameplay in AI Dungeon because we adopted the Type of the Unleashed fork, giving you full control over all the characters because we do not automatically adapt your sentences behind the scenes. This means you can more reliably control characters that are not you.

As a result of this what you need to type is slightly different, in AI Dungeon you would type take the sword while in KoboldAI you would type it like a sentence such as You take the sword and this is best done with the word You instead of I.

To speak simply type: *You say "We should probably gather some supplies first"*<br>
Just typing the quote might work, but the AI is at its best when you specify who does what in your commands.

If you want to do this with your friends we advise using the main character as You and using the other characters by their name if you are playing on a model trained for Adventures. These models assume there is a You in the story. This mode does usually not perform well on Novel models because they do not know how to handle the input those are best used with regular story writing where you take turns with the AI.

### Story mode

If you want to use KoboldAI as a writing assistant this is best done in the regular mode with a model optimized for Novels. These models do not make the assumption that there is a You character and focus on Novel like writing. For writing these will often give you better results than Adventure or Generic models. That said, if you give it a good introduction to the story large generic models like 13B can be used if a more specific model is not available for what you wish to write. You can also try to use models that are not specific to what you wish to do, for example a NSFW Novel model for a SFW story if a SFW model is unavailable. This will mean you will have to correct the model more often because of its bias, but can still produce good enough results if it is familiar enough with your topic.

### Chatbot mode

In chatbot mode you can use a suitable model as a chatbot, this mode automatically adds your name to the beginning of the sentences and prevents the AI from talking as you. To use it properly you must write your story opening as both characters in the following format (You can use your own text) :

```plaintext
Bot : Hey!
You : Hey Boyname, how have you been?
Bot : Been good! How about you?
You : Been great to, excited to try out KoboldAI
Bot : KoboldAI is really fun!
You : For sure! What is your favorite game?
```

Its recommended to have your own input be the last input, especially in the beginning its possible that the AI mixes up the names. In that case either retry or manually correct the name. This behavior improves as the chat progresses. Some models may swap names if they are more familiar with a different name that is similar to the name you defined for the bot. In that case you can either do the occasional manual correction or choose a name for your chatbot that the AI likes better.

This mode works the best on either a Generic model or a chatbot model specifically designed for it, some models like the AvrilAI model are instead designed to be used in Adventure mode and do not conform to the format above. These models typically ship with adventure mode enabled by default and should not be switched over to chatbot mode.

Novel or Adventure models are not recommended for this feature but might still work but can derail away from the conversation format quickly.

## Play KoboldAI online on Google Colab

If you would like to play KoboldAI online for free on a powerful computer you can use Google Colaboraty. We provide two editions, a TPU and a GPU edition with a variety of models available. These run entirely on Google's Servers and will automatically upload saves to your Google Drive if you choose to save a story (Alternatively, you can choose to download your save instead so that it never gets stored on Google Drive). Detailed instructions on how to use them are at the bottom of the Colab's.

Each edition features different models and requires different hardware to run, this means that if you are unable to obtain a TPU or a GPU you might still be able to use the other version. The models you can use are listed underneath the edition. To open a Colab click the big link featuring the editions name.

**[Click here for the TPU Edition Colab](https://colab.research.google.com/github/KoboldAI/KoboldAI-Client/blob/main/colab/TPU.ipynb)**<br>
**[Click here for the GPU Edition Colab](https://colab.research.google.com/github/KoboldAI/KoboldAI-Client/blob/main/colab/GPU.ipynb)**

## Install KoboldAI on your own computer
### Installing KoboldAI offline bundle on Windows 7 or higher
1. [Download the latest offline installer from here](https://sourceforge.net/projects/koboldai/files/latest/download)
2. Run the installer to place KoboldAI on a location of choice, KoboldAI is portable software and is not bound to a specific harddrive. (Because of long paths inside our dependencies you may not be able to extract it many folders deep).
3. Update KoboldAI to the latest version with update-koboldai.bat if desired.
4. Use KoboldAI offline using play.bat or remotely with remote-play.bat

### Installing KoboldAI Github release on Windows 10 or higher
1. Extract the .zip to a location you wish to install KoboldAI, you will need roughly 20GB of free space for the installation (this does not include the models).
2. Open install_requirements.bat as administrator.
3. Choose the regular version of Transformers (Option 1), finetuneanon is depreciated and no longer recommended.
4. You will now be asked to choose the installation mode, we strongly recommend the Temporary B: drive option. This option eliminates most installation issues and also makes KoboldAI portable. The B: drive will be gone after a reboot and will automatically be recreated each time you play KoboldAI.
5. The installation will now automatically install its requirements, some stages may appear to freeze do not close the installer until it asks you to press a key. Before pressing a key to exit the installer please check if errors occurred. Most problems with the game crashing are related to installation/download errors. Disabling your antivirus can help if you get errors.
6. Use play.bat to start KoboldAI.

### Installing KoboldAI on Linux
1. Clone the URL of this Github repository (For example git clone https://github.com/koboldai/koboldai-client )
2. AMD user? Make sure ROCm is installed if you want GPU support. Is yours not compatible with ROCm? Follow the usual instructions.
3. Run play.sh or if your AMD GPU supports ROCm use play-rocm.sh

KoboldAI will now automatically configure its dependencies and start up, everything is contained in its own conda runtime so we will not clutter your system. The files will be located in the runtime subfolder. If at any point you wish to force a reinstallation of the runtime you can do so with the install_requirements.sh file. While you can run this manually it is not neccesary.

### Manual installation / Mac

We can not provide a step by step guide for manual installation due to the vast differences between the existing software configuration and the systems of our users.

If you would like to manually install KoboldAI you will need some python/conda package management knowledge to manually do one of the following steps :

1. Use our bundled environments files to install your own conda environment, this should also automatically install CUDA (Recommended, you can get Miniconda from https://docs.conda.io/en/latest/miniconda.html#latest-miniconda-installer-links). The recommended configuration is huggingface.yml for CUDA users and rocm.yml for ROCm users.
2. If conda is proving difficult you could also look inside requirements.txt for the required dependencies and try to install them yourself. This will likely be a mixture of pip and your native package manager, just installing our requirements.txt is not recommended since we assume local users will run conda to get all dependencies. For local installations definitely prioritize conda as that is a better way for us to enforce that you have the compatible versions.
3. Clone our Github or download the zip file.
4. Now start KoboldAI with aiserver.py and not with our play.bat or play.sh files.

### AMD GPU's (Linux only)

AMD GPU's have terrible compute support, this will currently not work on Windows and will only work for a select few Linux GPU's. [You can find a list of the compatible GPU's here](https://github.com/RadeonOpenCompute/ROCm#Hardware-and-Software-Support). Any GPU that is not listed is guaranteed not to work with KoboldAI and we will not be able to provide proper support on GPU's that are not compatible with the versions of ROCm we require. Make sure to first install ROCm on your Linux system using a guide for your distribution, after that you can follow the usual linux instructions above.

## License

KoboldAI is licensed with a AGPL license, in short this means that it can be used by anyone for any purpose. However, if you decide to make a publicly available instance your users are entitled to a copy of the source code including all modifications that you have made (which needs to be available trough an interface such as a button on your website), you may also not distribute this project in a form that does not contain the source code (Such as compiling / encrypting the code and distributing this version without also distributing the source code that includes the changes that you made. You are allowed to distribute this in a closed form if you also provide a separate archive with the source code.).

umamba.exe is bundled for convenience because we observed that many of our users had trouble with command line download methods, it is not part of our project and does not fall under the AGPL license. It is licensed under the BSD-3-Clause license. Other files with differing licenses will have a reference or embedded version of this license within the file.