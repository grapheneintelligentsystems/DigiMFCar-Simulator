# DigiMFCar-Simulator
## Installation Instructions for Donkey car in Ubuntu 20.04 for compatibility with Ardupilot and PX4

Video Tutorial here: (https://youtu.be/OzZRESrNndU)

**SUPER SOS** update Linux with latest libraries
```bash
sudo apt update
```
install git
```bash
sudo apt update
sudo apt install git
```
Install python via MiniConda and create a new python virtual environment 
```bash
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash ./Miniconda3-latest-Linux-x86_64.sh
```
After installation and initialization create a list of its libraries of the present environment
```bash
conda list
sudo reboot
```
## Install DonkeyCar
Make a new folder for donkey app add switch into
```bash
mkdir DIGIMFDonkey
cd DIGIMFDonkey
```
Download the latest DonkeyCar from github
```bash
git clone https://github.com/autorope/donkeycar
cd donkeycar
```
and update all files
```bash
git checkout main
```
Create a new MiniConta virtual environment for Donkey application
```bash
conda create --name DGMFdonkeyX python=3
```
**SUPER SOS** Then switch to new environment by
```bash
conda activate DGMFdonkeyX
```
Here you install DokeyCar application which just downloaded
```bash
pip install -e .[pc]
```
Install tensor flow 2.2.0 in new environment by
```bash
conda install tensorflow-gpu==2.2.0 
```
Create a local working folder/settings for real donkey car
```bash 
donkey createcar --path /home/ubuntu/DIGIMFDonkey/mycar
```
## Install DonkeyCar SIMULATOR
Download and unzip the simulator for your host pc platform from Donkey Gym Release (https://github.com/tawnkramer/gym-donkeycar/releases)
Place the simulator where you like. For this example it will be /home/ubuntu/DIGIMFDonkey /DonkeySimLinux. Your dir will have a different name depending on platform. 
Finally make the file “donkey_sim.x86_64” executable
```bash 
chmod +x /home/ubuntu/DIGIMFDonkey/DonkeySimLinux/donkey_sim.x86_64
```
Open a new terminal from inside the folder DIGIMFDonkey to have the correct path or switch to folder.
```bash 
cd /home/ubuntu/DIGIMFDonkey
```
Install the gym environment
```bash 
git clone https://github.com/tawnkramer/gym-donkeycar
cd gym-donkeycar
```
**SUPER SOS** Then activate the virtual environment in miniconda if you are not there already 
```bash 
conda activate DGMFdonkeyX
pip install -e .[gym-donkeycar]
```
Create a folder/settings for the simulator
```bash 
donkey createcar --path /home/ubuntu/DIGIMFDonkey/mysim
cd /home/ubuntu/DIGIMFDonkey/mysim
```
Edit your myconfig.py to enable donkey gym simulator wrapper, replace <user-name> and the other parts of the path with actual path of “donkey_sim.x86_64” file (Tip: do CNTRL+C on the file to get the absolute path)
```bash 
gedit myconfig.py
```
Place the lines below at the top of myconfig.py
```bash 
DONKEY_GYM = True
DONKEY_SIM_PATH = "/home/<user-name>/projects/DonkeySimLinux/donkey_sim.x86_64"
DONKEY_GYM_ENV_NAME = "donkey-generated-track-v0"
```
Then try to drive in simulation environment
```bash 
python manage.py drive
```
One’s server simulator starts open web browser and redirect to local Donkey UI at
[Local Server:](http://localhost:8887/drive)

To exit simulator, click on terminal and press CNTRL+C
