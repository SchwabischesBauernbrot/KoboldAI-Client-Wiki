## Introduction
A collection of frequently asked questions and answers by users. The answers are based on other users' experiences with KoboldAI, so they may not always be completely accurate.
## KoboldAI
Q: What is a token?<br>
A: Token is a piece of word (about 3-4 characters).

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
A: In order to work, AI models must run on the GPU or TPU. It is possible to run models from 1.3B (and smaller) to 6B on the free GPU available from Colab. This is due to GPU restrictions imposed by Colab developers. Bigger models, from 6B up to 20B (the maximum you can run in Colab), can only be run on a TPU.

Q: Why can't we run all models on the GPU?<br>
A: Theoretically, we can. Moreover, the GPU is better suited to run AI models than TPU. However, it is worth remembering that each model requires a certain amount of VRAM/RAM and disk space to run. The current free GPU in Colab only gives 12GB RAM, which is clearly not enough to run models bigger than 6B. That's why the TPU is used to run models from 6B (it provides much more RAM).

Q: I keep getting a message that TPU accelerators are not available.<br>
A: The use of TPU in Colab is limited because of the need to share this resource among all users. It depends on the frequency and duration of your TPU usage as well as busy hours. To solve this problem, try waiting 1 to 5 minutes on the TPU Colab page without reloading it, and then click "Connect" again. Repeat until you get access, or try again later.

Q: What are the busy hours?<br>
A: Busy hours is the time of day during which TPU is most often used by users and mostly by Google (since developers also use TPU for their needs). During busy hours, your access to TPU is likely to be so limited that you will constantly get a message denying access to TPU accelerators. To solve this problem, run KoboldAI on TPU between night and morning. Busy hours start in the morning and last at small intervals all day until late evening, so the only time the TPU runtime environment will be 100% available is at night.

Q: Does the GPU version have the same access limitations as the TPU version?<br>
A: Usually, no, it doesn't. The GPU version is always available.

Q: What is the Captcha and how long can I use the TPU/GPU?<br>
A: The TPU/GPU can be used for up to 12 hours. However, Colab checks your activity every 30 minutes (on average) (whether you use TPU/GPU passively, wasting resources or not) by showing you a captcha. To ensure that your usage priority is not lowered and that you can continue to use TPU/GPU without problems, click on the captcha. It will disappear for the next 30 minutes or more.

Q: I want to run KoboldAI in Colab with my preset settings (my preferred model/version/provider) instead of having to change the default settings in the Colab TPU page every time. How do I do this?<br>
A: Change any of the parameters on the Colab TPU page (model/version/provider). At the top, next to "Help" you will see "Cannot save changes". Click on this and a window will appear with the option "Save a copy in Drive". Click on that. Voila! Now you have a copy of the official notebook with which you can do whatever you want (including changing the startup settings to suit your preferences).

## Colab Problems

Q: When I ran KoboldAI with Cloudflare, I got an Argo Tunnel error (Error 1033) when I clicked the generated link. What should I do?<br>
A: Wait 1 to 5 minutes and refresh the page.

Q: I got this error. What should I do? ( W external/org_tensorflow/tensorflow/compiler/xla/python/tpu_driver/client/tpu_client.cc:618] TPU Execute is taking a long time. This might be due to a deadlock between multiple TPU cores or a very slow program. )<br>
A: Sometimes you can get faulty TPU. Go to Runtime -> Sessions and then end all sessions you can get a new one.

***

P.S. If you don't find the answers to any questions, please see the other pages on this wiki. They may have information about what you are looking for.