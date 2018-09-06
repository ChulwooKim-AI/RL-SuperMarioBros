# How to install and run on Windows 10

## 1. Install Windows subsystem bashshell
- Windows Icon > Setting > Update & Security > For developers > Select Developer mode
- Windows Icon > Setting > Search Windows Features > Check Windows Subsystem for Linux > Restart
- Execute Bash >  y (Ubuntu app) > Input ID/PW

## 2. Install Tensorflow
- $ sudo apt-get install python3-pip python3-dev python-virtualenv # for Python 3.n
- $ virtualenv --system-site-packages -p python3 ~/tensorflow # for Python 3.n
- $ source ~/tensorflow/bin/activate
- (tensorflow)~$ pip3 install --upgrade tensorflow     # for Python 3.n

## 3. Install openAI gym
- (tensorflow)~$ sudo apt-get install -y python-numpy python-dev cmake zlib1g-dev libjpeg-dev xvfb libav-tools xorg-dev python-opengl libboost-all-dev libsdl2-dev swig
- $ git clone https://github.com/openai/gym.git
- $ cd gym
- $ pip install -e '.[all]'

## 4. Install xming to excute game in gym
- Download and Install https://sourceforge.net/projects/xming/
- Before excute python code, you should command following this:
    - $ export DISPLAY=:0
- When excuting in cloud server, use this command to turn off game screen:
    - $ export DISPLAY=:99

## (optional) Test code
```python
import gym 
env = gym.make('CartPole-v0')
env.reset()
for _ in range(1000):
    env.render()
    env.step(env.action_space.sample()) # take a random action
```

## 5. Install super mario game
- $ pip install git+https://github.com/chris-chris/gym-super-mario

## 6. Install game emulator
- $ sudo apt-get install fceux

## 7. Modify /ppaquette_gym_super_mario/__init__.py script
- It doesn't support registration class anymore in gym library by OpenAI. So, you need to block the part of code in this library. 
```python
2 #from gym.scoreboard.registration import add_task, add_group
...
46 '''
...
76 '''
```

## 8. Make log folder in fceux
$ mkdir ~/.fceux/log