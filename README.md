# install-gym-mujoco-notes

*mujoco*

1.50

`unzip mujoco150_linux.zip ~/.mujoco/`

The path is `~/.mujoco/mujoco150/bin..`

Put the `mjkey.txt` in `~/.mujoco/` and `~/.mujoco/mujoco150/bin`

```
sudo cp ~/.mujoco/mujoco150/bin/*.so /usr/local/lib
echo export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib >>~/.bashrc
source ~/.bashrc
~/.mujoco/mujoco150/bin/simulate
```
and drag the model in the window.

*virtualenv*

```
pip3 install virtualenv
virtualenv -p /usr/bin/python3 gymlab
source gymlab/bin/active
```

*mujoco-py*
Instead of installing mujoco-py from pip, try cloning the source and installing it with pip install -e . [bug]
```
git clone https://github.com/openai/mujoco-py
cd mujoco-py
pip install e .
```

*gym*
```
git clone https://github.com/openai/gym.git
cd gym
pip install -e .[all]
```

*test*

gym_test.py
```
import mujoco_py
import gym
from os.path import dirname

env = gym.make('Walker2d-v2')
env.reset()
for _ in range(1000):
    env.render()
    env.step(env.action_space.sample())
```
`python gym_test.py`

[bug]: https://github.com/openai/mujoco-py/issues/99
