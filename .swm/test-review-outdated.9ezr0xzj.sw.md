---
id: 9ezr0xzj
title: Test review outdated
file_version: 1.1.2
app_version: 1.9.0
---

<br/>

<br/>

`isMovable`<swm-token data-swm-token=":source/component/map.py:20:3:3:`    def isMovable(self, map_x, map_y):`"/> and `getMapIndex`<swm-token data-swm-token=":source/component/map.py:23:3:3:`    def getMapIndex(self, x, y):`"/> is the origin of `getMapGridPos`<swm-token data-swm-token=":source/component/map.py:28:3:3:`    def getMapGridPos(self, map_x, map_y):`"/> Understand the offset of `MAP_OFFSET_X`<swm-token data-swm-token=":source/component/map.py:24:7:7:`        x -= c.MAP_OFFSET_X`"/>`and` `MAP_OFFSET_Y`<swm-token data-swm-token=":source/component/map.py:25:7:7:`        y -= c.MAP_OFFSET_Y`"/>
<!-- NOTE-swimm-snippet: the lines below link your snippet to Swimm -->
### 📄 source/component/map.py
```python
9          def __init__(self, width, height):
10             self.width = width
11             self.height = height
12             self.map = [[0 for x in range(self.width)] for y in range(self.height)]
13     
14         def isValid(self, map_x, map_y):
15             if (map_x < 0 or map_x >= self.width or
16                 map_y < 0 or map_y >= self.height):
17                 return False
18             return True
19         
20         def isMovable(self, map_x, map_y):
21             return (self.map[map_y][map_x] == c.MAP_EMPTY)
22         
23         def getMapIndex(self, x, y):
24             x -= c.MAP_OFFSET_X
25             y -= c.MAP_OFFSET_Y
26             return (x // c.GRID_X_SIZE, y // c.GRID_Y_SIZE)
27         
28         def getMapGridPos(self, map_x, map_y):
29             return (map_x * c.GRID_X_SIZE + c.GRID_X_SIZE//2 + c.MAP_OFFSET_X,
30                     map_y * c.GRID_Y_SIZE + c.GRID_Y_SIZE//5 * 3 + c.MAP_OFFSET_Y)
31         
32         def setMapGridType(self, map_x, map_y, type):
33             self.map[map_y][map_x] = type
34     
35         def getRandomMapIndex(self):
36             map_x = random.randint(0, self.width-1)
37             map_y = random.randint(0, self.height-1)
38             return (map_x, map_y)
39     
40         def showPlant(self, x, y):
41             pos = None
42             map_x, map_y = self.getMapIndex(x, y)
43             if self.isValid(map_x, map_y) and self.isMovable(map_x, map_y):
44                 pos = self.getMapGridPos(map_x, map_y)
45             return pos
```

<br/>

Th

<br/>

`87`<swm-token data-swm-token=":source/component/menubar.py:8:4:4:`PANEL_Y_START = 87`"/> and `74`<swm-token data-swm-token=":source/component/menubar.py:10:4:4:`PANEL_Y_INTERNAL = 74`"/>\`of a oaowfejaowie<br/>
<!-- NOTE-swimm-snippet: the lines below link your snippet to Swimm -->
### 📄 source/component/menubar.py
```python
7      
8      PANEL_Y_START = 87
9      PANEL_X_START = 22
10     PANEL_Y_INTERNAL = 74
11     PANEL_X_INTERNAL = 53
12     CARD_LIST_NUM = 8
```

<br/>

`name`<swm-token data-swm-token=":source/component/plant.py:122:3:3:`        self.name = name`"/> `health`<swm-token data-swm-token=":source/component/plant.py:123:3:3:`        self.health = health`"/>
<!-- NOTE-swimm-snippet: the lines below link your snippet to Swimm -->
### 📄 source/component/plant.py
<!-- collapsed -->

```python
122            self.name = name
123            self.health = health
124            self.state = c.IDLE
125            self.bullet_group = bullet_group
126            self.can_sleep = False
127            self.animate_timer = 0
128            self.animate_interval = 100
129            self.hit_timer = 0
```

<br/>

<br/>

<br/>


<!-- NOTE-swimm-snippet: the lines below link your snippet to Swimm -->
### 📄 source/component/zombie.py
```python
29             self.walk_timer = 0
30             self.animate_timer = 0
31             self.attack_timer = 0
32             self.state = c.WALK
33             self.animate_interval = 150
34             self.ice_slow_ratio = 1
35             self.ice_slow_timer = 0
36             self.hit_timer = 0
37             self.speed = 1
38             self.freeze_timer = 0
39             self.is_hypno = False # the zombie is hypo and attack other zombies when it ate a HypnoShroom
```

<br/>


<!-- NOTE-swimm-snippet: the lines below link your snippet to Swimm -->
### 📄 source/component/zombie.py
<!-- collapsed -->

```python
3      import pygame as pg
4      from .. import tool
5      from .. import constants as c
6      
```

<br/>


<!-- NOTE-swimm-snippet: the lines below link your snippet to Swimm -->
### 📄 source/data/entity/plant.json
<!-- collapsed -->

```json
3              "PeaNormal":{"x":28, "y":0, "width":28, "height":34},
4              "PeaIce":{"x":26, "y":0, "width":30, "height":34},
5              "Chomper":{"x":0, "y":0, "width":100, "height":114},
6              "PuffShroom":{"x":0, "y":28, "width":35, "height":38},
7              "PuffShroomSleep":{"x":1, "y":0, "width":39, "height":65},
8              "BulletMushRoom":{"x":0, "y":1, "width":55, "height":21},
9              "PotatoMine":{"x":0, "y":0, "width":75, "height":55},
10             "Squash":{"x":10, "y":140, "width":80, "height":86},
11             "SquashAim":{"x":10, "y":140, "width":80, "height":86},
12             "Spikeweed":{"x":3, "y":0, "width":80, "height":35}
```

<br/>


<!-- NOTE-swimm-snippet: the lines below link your snippet to Swimm -->
### 📄 source/data/entity/zombie.json
<!-- collapsed -->

```json
2          "zombie_image_rect":{
3              "Zombie":{"x":62, "width":90},
4              "ZombieAttack":{"x":62, "width":90},
5              "ZombieLostHead":{"x":62, "width":90},
6              "ZombieLostHeadAttack":{"x":62, "width":90},
7              "ZombieDie":{"x":0, "width":164},
8              "BoomDie":{"x":68, "width":80},
9              "ConeheadZombie":{"x":80, "width":80},
10             "ConeheadZombieAttack":{"x":79, "width":87},
11             "BucketheadZombie":{"x":54, "width":90},
12             "BucketheadZombieAttack":{"x":46, "width":90},
13             "FlagZombie":{"x":56, "width":110},
14             "FlagZombieAttack":{"x":60, "width":100},
15             "FlagZombieLostHead":{"x":55, "width":110},
16             "FlagZombieLostHeadAttack":{"x":55, "width":110},
17             "NewspaperZombie":{"x":48, "width":92},
18             "NewspaperZombieAttack":{"x":48, "width":92},
19             "NewspaperZombieNoPaper":{"x":40, "width":98},
20             "NewspaperZombieNoPaperAttack":{"x":48, "width":92},
21             "NewspaperZombieLostHead":{"x":44, "width":96},
22             "NewspaperZombieLostHeadAttack":{"x":48, "width":92},
23             "NewspaperZombieDie":{"x":0, "width":100}
24         }
```

<br/>

This file was generated by Swimm. [Click here to view it in the app](http://localhost:5000/repos/Z2l0aHViJTNBJTNBUHl0aG9uUGxhbnRzVnNab21iaWVzJTNBJTNBc2h1anV1dQ==/docs/9ezr0xzj).
