## Tutorial: custom TecoGAN build (Win 10)
Note: 1.03 CUDA only for now.

# Installing Python, CUDA and PyTorch
1. Install Python 64-bit (https://www.python.org/downloads/windows/ x86-64 link, don't install 32-bit by mistake).
2. To install PyTorch, open a command prompt by clicking the address bar and typing cmd, then do `pip3 install torch==1.2.0 torchvision==0.4.0 -f https://download.pytorch.org/whl/torch_stable.html`
3. Install CUDA **10.0** (https://developer.nvidia.com/cuda-10.0-download-archive). Do not use 10.1 or tensorflow-gpu will fail.
4. Register at Nvidia Developers and download cuDNN (https://developer.nvidia.com/cudnn , download cuDNN). Place it in C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.0\bin or ensure it's in your system PATH environment variable.

# Installing TecoGAN and other prerequisites
(note, if you've already got tensorflow (non gpu) installed at this point, uninstall it first with `pip uninstall tensorflow`)
1. Go to https://github.com/tentakuru/TecoGAN and click the green Clone or download button, choose download as .zip. Unzip in your \TG folder.
2. In runGan.py, change paths to the correct paths on your system.
More specifically, right click runGan.py and open with notepad (or download visual studio code and use that), then for all paths that start with F:\ , change them to the paths on your system.
3. To install tensorflow-gpu, in your TG folder, open a command prompt by clicking the address bar and typing cmd, then do `pip3 install --ignore-installed --upgrade tensorflow-gpu`
4. To install other prerequisites, in the same cmd, do `pip3 install -r requirements.txt`
5. To confirm that tensorflow-gpu is working correctly, open cmd, then this:

```python
python
import tensorflow as tf

sess = tf.Session(config=tf.ConfigProto(log_device_placement=True))
```

If successful you should see Device mapping: and some information on your GPU. If this says Device mapping: no known devices. , reboot and try again.

# Making callsubprocess.py into an .exe
1. Go to https://github.com/tentakuru/CallSubprocess and click the green Clone or download button, choose download as .zip. Unzip in your \TG folder.
1. In cmd, install pyinstaller by doing `pip3 install pyinstaller`
2. In cmd (in TG folder) do `pyinstaller -F callsubprocess.py` . This will create a .exe of callsubprocess.py called callsubprocess.exe in the subfolder \dist\. Move this file into the main TG folder. 
3. Rename callsubprocess.exe to tgmain-cuda.exe (backup original file first).
4. In the TG folder create a file called GAN.txt with the contents 0 and save the file. **No whitespace (enter, spaces) can be in the file, only a 0.**

You're done. Test it with a video, it will use your own TecoGAN with much faster loading/processing speeds. 
Note that the video process is changed from doing one output folder at a time in separate tgmain-cuda.exes to doing all output folders in one tgmain-cuda.exe and then aborting the process for all remaining calls from the host program (will flash a bunch of cmd windows but isn't any problem)

## Troubleshooting
"AFL doesn't work!" **For AFL to work you need the model found here: https://github.com/tentakuru/TecoGAN/tree/master/model unzip it into the model folder (also extract multi part archive)**
