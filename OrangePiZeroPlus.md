### Orange Pi Zero Plus
![http://www.orangepi.org/images/pi_Zero%20plus_shuoming_en.jpg](http://www.orangepi.org/images/pi_Zero%20plus_shuoming_en.jpg)

### Operating System
For the OS I used [Armbian](https://www.armbian.com/download/?tx_maker=xunlong)

### Basic Setup
- connect it with a physical network cable to your local network
- use SSH to log in with root - 1234
- sudo apt-get update
- sudo apt-get upgrade
- sudo apt-get install python3-dev python3-pip python3-setuptools git virtualenv psmisc

### Octoprint Install
sudo adduser octoprint
sudo usermod -a -G tty octoprint
sudo usermod -a -G dialout octoprint
sudo adduser octoprint sudo

####edit sudoers:
sudo visudo

####at the end of the file add a line:

octoprint ALL=(ALL) NOPASSWD:ALL

[CTRL]-[X] + [Y] + [Enter] saves the doc

####Now clear the password :

sudo passwd octoprint -d

####Login as octoprint

sudo su octoprint

####goto homedir

cd ~

####Install Pyserial 3.5
python3 -m pip install pyserial

### Octoprint itself
git clone https://github.com/foosel/OctoPrint.git

cd OctoPrint

virtualenv --python=python3 venv

./venv/bin/python setup.py install

###Test Server
~/OctoPrint/venv/bin/octoprint serve

sudo cp ~/OctoPrint/scripts/octoprint.init /etc/init.d/octoprint
sudo chmod +x /etc/init.d/octoprint
sudo cp ~/OctoPrint/scripts/octoprint.default /etc/default/octoprint

sudo nano /etc/default/octoprint

![](https://github.com/mybesttools/orangepi_octoprint_installmanuals/blob/main/octoprint_daemon.png?raw=true)

[CTRL]-[X] + [Y] + [Enter] saves the doc

sudo reboot





