## Introduction
A collection of frequently asked questions and answers to them. The answers are based on other users' experiences with KoboldAI, so they may not always be completely accurate.
## KoboldAI
Q: What is a token?<br>
A: Token is a piece of word (about 3-4 characters) or a whole word. Tokens are essentially the number of words that go into the AI pool to create the response.

Q: What are the models?<br>
A: Models are differently trained and finetuned AI units capable of generating text output.

Q: What are 2.7B, 6B, 13B, 20B?<br>
A: These are the sizes of AI models, measured in billions of parameters. Accordingly, 2.7B = 2.7 billion-parameter, 6B = 6 billion-parameter, 13B = 13 billion-parameter, 20B = 20 billion-parameter.

Q: What are the differences between 2.7B, 6B, 13B, 20B models?<br>
A: In short, the coherence of the output. Its basically how big the AI's brain is. Example: Imagine the brain off a child versus the brain of an adult. You can teach them the exact same thing and they can do the exact same thing. However, the adult brain will learn it better. So the bigger the models size (the number of billion-paramater), the better the model's understanding of your input.

Q: How long do models take to load?<br>
A: It depends on the size of the model. The bigger the model, the longer the loading time. On average, 2.7B models take 5 minutes to load, 6B models take 10 minutes, and 13B models take 15 minutes.

Q: What are the official and united versions? What are the differences between them?<br>
A: The official version is a more or less stable version of KoboldAI. The united version is an experimental version of KoboldAI, less stable, but with a number of features that will then sooner or later be ported to the official version.

Q: What is the prompt?<br>
A: The prompt is the first paragraph or two you give the AI in the action box to allow it to get the story started and allow it to generate the first response.

Q: The enter text here thing is the initial prompt, right?<br>
A: Yes, that text box at the bottom of the screen is for you to type your initial prompt and later for you to type your input.

Q: Does KoboldAI save my story/adventure?<br>
A: Yes, it saves anytime to the story folder when you click "save" from the top menu.

Q: Are my settings always saved?<br>
A: Yes, the changes are saved automatically every time you change the settings values.

Q: Where are my stories and settings stored? How can I load my own userscripts or softprompts?<br>
A: KoboldAI uses your Google Drive to store your files and settings. You can find your stories files in the KoboldAI -> stories folder and the .settings files containing your settings values in the KoboldAI -> settings folder. If you wish to upload a softprompt or userscript this can be done directly on the Google Drive website. You can also use this to download backups of your KoboldAI related files.

Q: What is the amount of tokens?<br>
A: The amount of tokens is the context of the story. The more tokens, the more consistency and memory used. But some models can't handle the full 2048 and break (act weird until you reduce the tokens).

Q: Does "gens per action" make it so multiple possible continuations are generated and I pick one?<br>
A: It does make multiple generations of the number you set it to, but takes that number of times longer to produce the results. Set it to 3 gens per action and it will take roughly 3 times as long as 1 gen.

Q: Can I change from story mode to adventure mode and vice versa after a story has already started?<br>
A: Yes. If you want story mode, then write the prompt and all new actions in third person. If you want adventure mode, then write the prompt and new actions in first person. But you can swap during play, although how well the model picks up on that is dependent on many factors.

Q: Is it normal for a box next to the action text box to say "Mode: Story" while in adventure mode in the settings?<br>
A: Adventure mode has two modes: Mode: Story and Mode: Adventure. Mode: Story directly inputs what you type into the story while Mode: Adventure turns what you write into actions. Click on Mode: story or Mode: Adventure near the box to swap between them.

Q: Does it switch only after entering the initial prompt?<br>
A: It switches to story if you dont have a prompt typed up yet.

## Colab
Q: What is Colab?<br>
A: Google Colaboratory (or Colab for short) is a free environment to write code in jupyter notebook. The program provides access to GPUs (Graphics Processing Unit) and TPUs (Tensor Processing Unit).

Q: Why do we use Colab to run KoboldAI?<br>
A: Colab is currently the only way (except for Kaggle) to get the free computing power needed to run models in KoboldAI.

Q: Why don't we use Kaggle to run KoboldAI then?<br>
A: Kaggle does not support all of the features required for KoboldAI.

Q: What is a provider?<br>
A: To run, KoboldAI needs a server where this can be done. There are currently three providers that provide this capability: Cloudflare, Localtunnel, and ngrok (not represented in Colab). Once you have finished downloading and running KoboldAI in Colab, a link provided by one of these providers is given.

Q: What are the differences between Cloudflare and Localtunnel?<br>
A: Cloudflare is a company. Their servers are often blocked by antivirus, so if you want to run KoboldAI with this provider, be sure to exclude the link from your antivirus. Example: Exceptions -> Add Exception -> https://*.tryclouddflare.com/*. Localtunnel is one guy. Its servers are less stable (may be unavailable more often), but they are not blocked by antivirus.

Q: What are the differences between the GPU and TPU versions of KoboldAI?<br>
A: In order to work, AI models must run on the GPU or TPU. It is possible to run models from 1.3B (and smaller) to 6B on the free GPU available from Colab. Bigger models, from 6B up to 20B (the maximum you can run in Colab), can only be run on a TPU. This is due to GPU restrictions imposed by Colab developers. So the answer is: The size of the models you can run on the GPU and TPU versions.

Q: Why can't we run all models on the GPU?<br>
A: Theoretically, we can. Moreover, the GPU is better suited to run AI models than TPU. However, it is worth remembering that each model requires a certain amount of VRAM/RAM and disk space to run. The current free GPU in Colab only gives 12GB RAM, which is clearly not enough to run models bigger than 6B. That's why the TPU is used to run models from 6B (it provides much more RAM).

Q: I keep getting a message that TPU accelerators are not available.<br>
A: The use of TPU in Colab is limited because of the need to share this resource among all users. It depends on the frequency and duration of your TPU usage as well as busy hours. To solve this problem, try waiting 1 to 5 minutes on the TPU Colab page without reloading it, and then click "Connect" again. Repeat until you get access, or try again later.

Q: What are the busy hours?<br>
A: Busy hours is the time of day during which TPU is most often used by users and mostly by Google (since developers also use TPU for their needs). During busy hours, your access to TPU is likely to be so limited that you will constantly get a message denying access to TPU accelerators. To solve this problem, run KoboldAI on TPU between night and morning. Busy hours start in the morning and last all day until late evening, so the only time the TPU runtime environment will be 100% available is at night.

Q: What is the Captcha and how long can I use the TPU/GPU?<br>
A: The TPU/GPU can be used for up to 12 hours. However, Colab checks your activity every 30 minutes (on average) (whether you use TPU/GPU passively, wasting resources or not) by showing you a captcha. To ensure that your usage priority is not lowered and that you can continue to use TPU/GPU without problems, click on the captcha. It will disappear for the next 30 minutes or more.

Q: What should I do after I finished using KoboldAI?<br>
A: Get back to TPU/GPU Colab page, go to the "Runtime menu", click on "Manage Sessions" and terminate your open sessions that you no longer need. This trick can help you maintain higher priority towards getting a TPU.

Q: I want to run KoboldAI in Colab with my preset settings (my preferred model/version/provider) instead of having to change the default settings in the Colab TPU page every time. How do I do this?<br>
A: Change any of the parameters on the Colab TPU page (model/version/provider). At the top, next to "Help" you will see "Cannot save changes". Click on this and a window will appear with the option "Save a copy in Drive". Click on that. Voila! Now you have a copy of the official notebook with which you can do whatever you want (including changing the startup settings to suit your preferences).

Q: Does KoboldAI have custom models support?<br>
A: Yes, it does. You can run any AI model (up to 20B size) that can generate text from the [Huggingface](https://huggingface.co/models?pipeline_tag=text-generation&sort=downloads) website. To do this, on the page of the selected model, click on the "Copy model name to clipboard" square icon next to the model name highlighted in bold. Then go to the TPU/GPU Colab page (it depends on the size of the model you chose: GPU is for 1.3 and up to 6B models, TPU is for 6B and up to 20B models) and paste with Ctrl+C and Ctrl+V the path to the model in the "Model" field. The result will look like this: "Model: EleutherAI/gpt-j-6B". That's it, now you can run it the same way you run the KoboldAI models.

## Local

Q: What are the system requirements to run KoboldAI on my machine?<br>
A: The base program is around 13 GB, not including the sizes of the installer and the models. You don't need any particular graphics card to run on CPU but to run on GPU you need an NVIDIA card with CUDA compute capability at least 3.7 or an AMD card supported by ROCm. If you want to use an AMD card with ROCm you additionally must be running Linux. The memory requirements vary depending on the model.

Q: What should I do to start playing Kobold offline (to run it on my machine)?<br>
A: Download the [installer](https://sourceforge.net/projects/koboldai/files/latest/download) and run it, follow the onscreen instructions and then when you start the game you'll be asked to pick a model. The model is downloaded to your hard drive and you won't have to download it again unless you want to try a different model. Once the model is loaded you can load a previous story or create one in the usual way by adding the memory section (a few lines you want it to remember, main character, location, goals), author's note (writing style, genre, etc.) and world info entries (characters, locations, etc.).

Q: Does it matter if I close the command window?<br>
A: Yes, that will exit the program.

## Local Errors

Q: How do I fix the error ['subst' is not recognized as an internal or external command, operable program or batch file]?<br>
A: This is solved by making sure [C:\Windows\System32] is set in the Path in environment variables for both user and system as the program can't find the subst.exe. To do this you have to go into system properties, then the advanced tab, then into the environment variables. Set the variable to [Path] if it doesn't already exist, then set the value to [C:\Windows\System32].

***

P.S. If you still have questions, please see the other pages on this wiki. They may have information you are looking for.