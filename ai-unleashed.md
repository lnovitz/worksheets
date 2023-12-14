Written by [Lianna Novitz](https://www.linkedin.com/in/liannanovitz/), with guidance from [Piranavan Selvanandan](https://www.linkedin.com/in/piranavan/) and the following videos:
* [TroubleChute's COMPLETE CRASH COURSE](https://www.youtube.com/watch?v=k-M_bUatcBc)
* [AI Tools Search AUTOMATIC1111 FULL TUTORIAL](https://www.youtube.com/watch?v=hwsvcbFeUTs)

# Start

1. Open your `terminal` application. [Tips on opening terminal](https://www.ionos.com/help/email/troubleshooting-mail-basicmail-business/access-the-command-prompt-or-terminal/)
2. Download `git`, if you don't have it. [Tips on installling git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

**Note**: you can run `git --version` in the commandline to see if `git` is already installed.

3. Download Stable Diffusion according to your operating system (pick 1)
* [Mac](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Installation-on-Apple-Silicon)
* [Windows 10/11 NVidia GPU](https://github.com/AUTOMATIC1111/stable-diffusion-webui#installation-on-windows-1011-with-nvidia-gpus-using-release-package)
* Other [Windows](https://github.com/AUTOMATIC1111/stable-diffusion-webui#automatic-installation-on-windows)
* [Linux](https://github.com/AUTOMATIC1111/stable-diffusion-webui#automatic-installation-on-linux)

**Important**: if you run into any errors, raise your hand or ask a question in the Zoom chat! **No one** left behind during the install process!

**Note**: if you're in-person and finding the download is slow, you can also grab one of the USB sticks. Lianna has pre-downloaded the files for you into the folder `sdui` using the command below:
	 `git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui /Volumes/USB20FD/sdui`.
Copy the `sdui` folder from the USB key to your machine.
  
4. Navigate into the newly created folder `sdui` (or it might be called `stable-diffusion-ui`)

   The inside of the folder should look like below (~ 7GB total)
   
   ![Screenshot 2023-12-10 at 11 39 57 PM](https://github.com/lnovitz/worksheets/assets/32498202/c6ff909d-9eb7-493a-817b-6d4f02ed5a1d)

	If you know your computer is powerful (i.e. [graphics card has at least 4GB of VRAM, 12 GB or more install space](https://www.digitaltrends.com/computing/stable-diffusion-pc-system-requirements/)), you can simply run `./webui.sh`

	Otherwise, try the following command per your OS:

* MacOS: `./webui.sh --opt-split-attention-v1` `--medvram`

	If you know your computer could use a lot of help performance wise, try `lowvram` instead of `medvram`. So the full command is `./webui.sh --opt-split-attention-v1 --lowvram`

 
A new window should pop up that looks like this (minus a weird Einstein face).  If the browser doesn't open automatically but the command succeeded then visit [localhost:7860](http://127.0.0.1:7860)

![Screenshot 2023-12-10 at 8 55 11 PM](https://github.com/lnovitz/worksheets/assets/32498202/d058569b-71ca-4531-aa3e-babc9aaf3018)

# Exercise 1 - `text2img` 
1. Confirm that `text2img` tab is selected at the top left of the window. To the left of the orange button "Generate", type the positive prompt that we decided on as a group (or use `Einstein standing on top of a Christmas tree carrying a sleeping purring cute cat in his arms`)
2. Click the orange button "Generate".
3. If you're not seeing results after about a minute and a moving progress bar, consider restarting the application with the `medvram` (or `lowvram`) arguments mentioned in Step 2 above. To restart, click into your Terminal app and type `Ctrl+C` to stop the application. 
4. Press the up arrow on your keyboard to cycle to the last command you used, and type in the argument `--opt-split-attention-v1 --lowvram` after `./webui.sh` , hit Return to confirm
5. Refine the prompt and keep trying to get an accurate image from your text. 
6. Once you're happy (or we run out of time for this exercise), download the image by right clicking "Save As" to your computer.
   
Note: If you're still experiencing a lot of slowness, consider pairing up with a neighbor to pair program together on their (hopefully faster) computer.
*Does this answer annoy you?* The problem is that Stable Diffusion requires a lot of computer brain - there are services online where you can pay for computer brain like https://beta.dreamstudio.ai/generate - but since we're using Stable Diffusion locally on our own computers, we have only our own computer brain to rely on.

# Exercise 2 - `img2img` 
1. Confirm that `img2img` tab is selected at the top of the window. Below the prompt text boxes, select `Generation > Inpaint sketch`. 
2. Click on `Click to upload` and upload the image we generated from Exercise 1
   
    ![Screenshot 2023-12-10 at 10 55 30 PM](https://github.com/lnovitz/worksheets/assets/32498202/3270373b-5d8f-4b67-9804-c1e515b15a5b)

    ![einstein](https://github.com/lnovitz/worksheets/assets/32498202/55f125b3-2443-4044-8332-578c818e2309)
   
4. It looks like Einstein does not have legs - let's try and fix that. Take your cursor and drag your mouse to paint over the bottom of the image where Einstein's legs should be.

    ![Screenshot 2023-12-10 at 11 00 14 PM](https://github.com/lnovitz/worksheets/assets/32498202/6150106d-ce7b-4609-9b58-977e662fc792)
   
6. In the positive prompt text box, add something like `green animated pants` and click `Generate` 
7. Again, tweak the prompts until you're happy, continuously refining the generated image. For each exercise you might have to click `Generate` 10 or so times with slight prompt tweaking to get what you want.

# Additional Resources

## Extensions
Now that you have installed Stable Diffusion, you can leverage its rich library of extensions to access more dynamic features:
- Control Net: Use reference images to control the composition and pose of people in your generated images [youtube tutorial](https://www.youtube.com/watch?v=mmZSOBSg2E4)
- After Detailer [details](https://stable-diffusion-art.com/automatic1111-extensions/#After_Detailer) or Ultimate SD Upscale [details](https://stable-diffusion-art.com/automatic1111-extensions/#Ultimate_SD_Upscale) for upscaling 512x512 images to larger resolutions
- Roop [details](https://stable-diffusion-art.com/automatic1111-extensions/#Roop) for inserting a face from a photo into your generated image

## Development
You can also develop with the Automatic1111 API available [here](http://127.0.0.1:7860/docs) when Stable Diffusion is running with commandline `--api` or see this [API Example](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/API).
If you want to build your own application using the power of Stable Diffusion, you can create one using the Diffusers [library](https://github.com/huggingface/diffusers) which can be as easy as:
```python
from diffusers import DiffusionPipeline
import torch

pipeline = DiffusionPipeline.from_pretrained("runwayml/stable-diffusion-v1-5", torch_dtype=torch.float16)
pipeline.to("cuda")
pipeline("Einstein standing on top of a Christmas tree carrying a sleeping purring cute cat in his arms").images[0]
```
