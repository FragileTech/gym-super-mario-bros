# gym-super-mario-bros

[![PackageVersion][pypi-version]][pypi-home]
[![PythonVersion][python-version]][python-home]
[![Stable][pypi-status]][pypi-home]
[![Format][pypi-format]][pypi-home]
[![License][pypi-license]](LICENSE)

[pypi-version]: https://badge.fury.io/py/gym-super-mario-bros.svg
[pypi-license]: https://img.shields.io/pypi/l/gym-super-mario-bros.svg
[pypi-status]: https://img.shields.io/pypi/status/gym-super-mario-bros.svg
[pypi-format]: https://img.shields.io/pypi/format/gym-super-mario-bros.svg
[pypi-home]: https://badge.fury.io/py/gym-super-mario-bros
[python-version]: https://img.shields.io/pypi/pyversions/gym-super-mario-bros.svg
[python-home]: https://python.org

![walk1](https://github.com/Kautenja/gym-super-mario-bros/blob/master/gym_super_mario_bros/sprites/smb1/Characters/Mario/Mario%20-%20Walk1.gif)
![walk2](https://github.com/Kautenja/gym-super-mario-bros/blob/master/gym_super_mario_bros/sprites/smb1/Characters/Mario/Mario%20-%20Walk2.gif)
![walk3](https://github.com/Kautenja/gym-super-mario-bros/blob/master/gym_super_mario_bros/sprites/smb1/Characters/Mario/Mario%20-%20Walk3.gif)
![jump](https://github.com/Kautenja/gym-super-mario-bros/blob/master/gym_super_mario_bros/sprites/smb1/Characters/Mario/Mario%20-%20Jump.gif)

An [OpenAI Gym](https://github.com/openai/gym) environment for
Super Mario Bros. & Super Mario Bros. 2 (Lost Levels) on The Nintendo
Entertainment System (NES).

# Installation

The preferred installation of `gym-super-mario-bros` is from `pip`:

```shell
pip install gym-super-mario-bros
```

## NES Emulator

`gym-super-mario-bros` uses [FCEUX](http://www.fceux.com/web/home.html) to emulate NES games.
Make sure it's installed and in your `$PATH`.

### Unix

```shell
sudo apt-get install fceux
```

### Mac

```shell
brew install fceux
```

# Usage

You must import `gym_super_mario_bros` before trying to make an environment. This is
because gym environments are registered at runtime.

```python
import gym_super_mario_bros
env = gym_super_mario_bros.make('SuperMarioBros-v0')

done = True
for step in range(5000):
    if done:
        state = env.reset()
    state, reward, done, info = env.step(env.action_space.sample())

env.close()
```

**NOTE:** `gym_super_mario_bros.make` is just an alias to `gym.make` for
convenience.

# Environments

These environments allow 3 attempts (lives) to make it through the 32 levels
of the game. The environments only send reward-able game-play frames to
agents; No cut-scenes, loading screens, etc. are sent from the NES emulator
to an agent nor can an agent perform actions during these occurrences. If a
cut-scene is not able to be skipped by hacking the NES's RAM, the environment
will lock the Python process until the emulator is ready for the next action.

| Environment                     | Game | Frameskip | ROM           | Screenshot |
|:--------------------------------|:-----|:----------|:--------------|:-----------|
| `SuperMarioBros-v0`             | SMB  | 4         | standard      | ![][v0]    |
| `SuperMarioBros-v1`             | SMB  | 4         | down-sampled  | ![][v1]    |
| `SuperMarioBros-v2`             | SMB  | 4         | pixelated     | ![][v2]    |
| `SuperMarioBros-v3`             | SMB  | 4         | rectangles    | ![][v3]    |
| `SuperMarioBrosNoFrameskip-v0`  | SMB  | 1         | standard      | ![][v0]    |
| `SuperMarioBrosNoFrameskip-v1`  | SMB  | 1         | down-sampled  | ![][v1]    |
| `SuperMarioBrosNoFrameskip-v2`  | SMB  | 1         | pixelated     | ![][v2]    |
| `SuperMarioBrosNoFrameskip-v3`  | SMB  | 1         | rectangles    | ![][v3]    |
| `SuperMarioBros2-v0`            | SMB2 | 4         | standard      | ![][2-v0]  |
| `SuperMarioBros2-v1`            | SMB2 | 4         | down-sampled  | ![][2-v1]  |
| `SuperMarioBros2NoFrameskip-v0` | SMB2 | 1         | standard      | ![][2-v0]  |
| `SuperMarioBros2NoFrameskip-v1` | SMB2 | 1         | down-sampled  | ![][2-v1]  |

[v0]: https://user-images.githubusercontent.com/2184469/40948820-3d15e5c2-6830-11e8-81d4-ecfaffee0a14.png
[v1]: https://user-images.githubusercontent.com/2184469/40948819-3cff6c48-6830-11e8-8373-8fad1665ac72.png
[v2]: https://user-images.githubusercontent.com/2184469/40948818-3cea09d4-6830-11e8-8efa-8f34d8b05b11.png
[v3]: https://user-images.githubusercontent.com/2184469/40948817-3cd6600a-6830-11e8-8abb-9cee6a31d377.png
[2-v0]: https://user-images.githubusercontent.com/2184469/40948822-3d3b8412-6830-11e8-860b-af3802f5373f.png
[2-v1]: https://user-images.githubusercontent.com/2184469/40948821-3d2d61a2-6830-11e8-8789-a92e750aa9a8.png

# Citation

Please cite `gym-super-mario-bros` if you use it in your research.

```tex
@misc{gym-super-mario-bros,
  author = {Christian Kauten},
  title = {{S}uper {M}ario {B}ros for {O}pen{AI} {G}ym},
  year = {2018},
  publisher = {GitHub},
  howpublished = {\url{https://github.com/Kautenja/gym-super-mario-bros}},
}
```
