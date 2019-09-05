# 1.03 to 1.04 upgrade, do this if you have a working modded 1.03

0. Copy old files to new TG (*note: not TGMAIN-CUDA*) folder (except for model folders and stuff not related to TecoGAN)
2. Remove TGMAIN-CUDA folder
3. Create a new TGMAIN-CUDA folder (should be empty at this point)
1. Get updated callsubprocess.py
2. `pyinstaller -F callsubprocess.py`
3. The last step created a file "callsubprocess.exe" in the folder \dist\, rename that file to tgmain.exe, put it in the TGMAIN-CUDA folder
4. Get runGan104.py and main104.py if you don't have them from https://github.com/tentakuru/TecoGAN (download as .zip), put in TG folder
5. In the top of runGan104.py replace the path with your own TG path
6. In TGMAIN-CUDA folder create a file called GAN.txt and write `104` and save (no spaces, no enter)
7. Now it works! ... maybe...
