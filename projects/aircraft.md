---
layout: project
type: project
image: img/aircraft.png
title: Aircraft Fight Game
date: 02/11/2022
published: true
labels:
  - Python
  - Game Development
  - Pygame
summary: "Developed a game called Aircraft Fight Game based on the Pygame shooter framework, featuring player-controlled aircraft, dynamic enemy interactions, collectible power-ups, and increasing difficulty through modular and scalable design."
---

<div class="text-center p-4">
  <img width="200px" src="../img/micromouse/micromouse-robot.png" class="img-thumbnail" >
  <img width="200px" src="../img/micromouse/micromouse-robot-2.jpg" class="img-thumbnail" >
  <img width="200px" src="../img/micromouse/micromouse-circuit.png" class="img-thumbnail" >
</div>

For this project, I developed a game called Aircraft Fight Game using Python and Pygame. This game features a main character, an aircraft that moves in four directions (up, down, left, and right) while automatically firing bullets at incoming enemies. The enemies come in three sizes: small, medium, and large. Each enemy has a health bar and once hit, their health decreases until they are destroyed. Players earn points upon destroying enemies, with the score depending on the enemy's size: small planes award 100 points, medium planes 200, and large planes 300. As the game progresses, the difficulty increases as enemies move faster. The main aircraft starts with three lives, and if hit by an enemy, it loses one. The game ends when the player runs out of lives. Additionally, there are supply drops that provide helpful items such as upgraded weapons for firing more bullets at once, faster firing rates, or restoring life to the player.

To develop the Aircraft Fight Game, I used Python and the Pygame library, which provides tools for 2D game development. The game was built with a modular design, where key components like the player aircraft, enemies, bullets, and supply items were implemented as separate classes. This structure allowed me to focus on each element individually and make improvements without affecting the overall system. The game relies on event-driven programming, where player actions, such as keyboard inputs for movement and mouse clicks to pause, are handled in real-time. I also used Pygame’s timer events to introduce periodic actions, like dropping supply items or enabling power-ups such as double bullets. To optimize performance, I implemented object pools for bullets and supplies, reusing existing objects by resetting their states instead of creating new ones repeatedly. The game adjusts its difficulty dynamically by spawning more enemies and increasing their speed as the player’s score increases, achieved through functions that add enemies and modify their speeds. Collision detection, a critical feature, was implemented using Pygame’s sprite collision tools, allowing precise interactions between bullets, enemies, and the player aircraft. These collisions drive the core gameplay, such as reducing enemy health, triggering destruction animations, and updating the score. Supply items, including weapon upgrades, faster shooting rates, and extra lives, were added to keep the gameplay engaging, while a scoring system rewards players based on the size and difficulty of defeated enemies. The main game loop, optimized for a consistent frame rate using Pygame’s clock functions, ensures smooth gameplay even as the game becomes more intense. By combining these features, I created a game that is responsive, visually appealing, and progressively challenging, showcasing my ability to develop interactive and dynamic systems while focusing on an enjoyable user experience.

Here is some code that illustrates how the game getting harder and harder, how the background music is loaded in, and how the aircraft moves:

```cpp
byte ADCRead(byte ch)
{
import pygame
import sys
import traceback
import myplane
import enemy
import bullet
import supply

from pygame.locals import *
from random import *

# Initialization of pygame
pygame.init()
pygame.mixer.init()

# game background setting
# background size 
bg_size = width, height = 1048, 768
screen = pygame.display.set_mode(bg_size)
# Screen name
pygame.display.set_caption("Aircraft_Fight_Game")
# Load background image
background = pygame.image.load("scene.png").convert()

BLACK = (0, 0, 0)
WHITE = (255, 255, 255)
GREEN = (0, 255, 0)
RED = (255, 0, 0)

# Import Music and set value name
pygame.mixer.music.load("backgroundmusic.wav")
pygame.mixer.music.set_volume(0.2)
bullet_sound = pygame.mixer.Sound("bullet.wav")
bullet_sound.set_volume(0.2)
bomb_sound = pygame.mixer.Sound("use_bomb.wav")
bomb_sound.set_volume(0.2)
supply_sound = pygame.mixer.Sound("supply.wav")
supply_sound.set_volume(0.2)
get_bomb_sound = pygame.mixer.Sound("get_bomb.wav")
get_bomb_sound.set_volume(0.2)
get_bullet_sound = pygame.mixer.Sound("get_bullet.wav")
get_bullet_sound.set_volume(0.2)
upgrade_sound = pygame.mixer.Sound("upgrade.wav")
upgrade_sound.set_volume(0.2)
enemy3_fly_sound = pygame.mixer.Sound("enemy3_flying.wav")
enemy3_fly_sound.set_volume(0.2)
enemy1_down_sound = pygame.mixer.Sound("enemy1_down.wav")
enemy1_down_sound.set_volume(0.2)
enemy2_down_sound = pygame.mixer.Sound("enemy2_down.wav")
enemy2_down_sound.set_volume(0.2)
enemy3_down_sound = pygame.mixer.Sound("enemy3_down.wav")
enemy3_down_sound.set_volume(0.5)
me_down_sound = pygame.mixer.Sound("me_died_music.wav")
me_down_sound.set_volume(0.2)


def add_small_enemies(group1, group2, num):
    for i in range(num):
        e1 = enemy.SmallEnemy(bg_size)
        group1.add(e1)
        group2.add(e1)

def add_mid_enemies(group1, group2, num):
    for i in range(num):
        e2 = enemy.MidEnemy(bg_size)
        group1.add(e2)
        group2.add(e2)

def add_big_enemies(group1, group2, num):
    for i in range(num):
        e3 = enemy.BigEnemy(bg_size)
        group1.add(e3)
        group2.add(e3)

def inc_speed(target, inc):
    for each in target:
        each.speed += inc

#Set the main parameters of the main module
def main():
    #Play the background music 
    pygame.mixer.music.play(-1)

    # Generate our plane
    me = myplane.MyPlane(bg_size)
    #All aircraft are euqal to this value. So when we do collision detect, we could just use this value.
    enemies = pygame.sprite.Group()

    # Generate small enemy
    # We define a function, because we want the difficulty increases ov time.
    small_enemies = pygame.sprite.Group()
    add_small_enemies(small_enemies, enemies, 15)

    # Generate mudium enemy
    mid_enemies = pygame.sprite.Group()
    add_mid_enemies(mid_enemies, enemies, 4)

    # Generate boss
    big_enemies = pygame.sprite.Group()
    add_big_enemies(big_enemies, enemies, 2)

    # Generate bullets
    # put the bullets image into the list
    bullet1 = []
    bullet1_index = 0
    BULLET1_NUM = 100
    for i in range(BULLET1_NUM):
        bullet1.append(bullet.Bullet1(me.rect.midtop))

    # Generate the super bullets
    bullet2 = []
    bullet2_index = 0
    BULLET2_NUM = 8
    for i in range(BULLET2_NUM//2):
        bullet2.append(bullet.Bullet2((me.rect.centerx-33, me.rect.centery)))
        bullet2.append(bullet.Bullet2((me.rect.centerx+30, me.rect.centery)))
    # Set the frame value
    clock = pygame.time.Clock()

    # index of death images
    e1_destroy_index = 0
    e2_destroy_index = 0
    e3_destroy_index = 0
    me_destroy_index = 0

    # Score
    score = 0
    score_font = pygame.font.Font("font.ttf", 36)

    # the icon for whether you to pause the game
    paused = False
    pause_nor_image = pygame.image.load("pause_nor.png").convert_alpha()
    pause_pressed_image = pygame.image.load("pause_pressed.png").convert_alpha()
    resume_nor_image = pygame.image.load("resume_nor.png").convert_alpha()
    resume_pressed_image = pygame.image.load("resume_pressed.png").convert_alpha()
    paused_rect = pause_nor_image.get_rect()
    paused_rect.left, paused_rect.top = width - paused_rect.width - 10, 10
    paused_image = pause_nor_image

    # set diffculy level
    level = 1

    # all screen boob
    bomb_image = pygame.image.load("bomb.png").convert_alpha()
    bomb_rect = bomb_image.get_rect()
    bomb_font = pygame.font.Font("font.ttf", 48)
    bomb_num = 3

    # every 30 second drop a supply
    bullet_supply = supply.Bullet_Supply(bg_size)
    bomb_supply = supply.Bomb_Supply(bg_size)
    SUPPLY_TIME = USEREVENT
    pygame.time.set_timer(SUPPLY_TIME, 30 * 1000)

    # How long could the bullets last
    DOUBLE_BULLET_TIME = USEREVENT + 1

    # icon for whether you want to use the super bullets
    is_double_bullet = False

    # Cancel allied invincibility timer
    INVINCIBLE_TIME = USEREVENT + 2

    # Life
    life_image = pygame.image.load("me_1.png").convert_alpha()
    life_rect = life_image.get_rect()
    life_num = 3

    # Used to prevent repeated opening of log files
    recorded = False


    # Used for switch the image
    switch_image = True

    # Used for delay the time
    delay = 100

    running = True
    #Quit the screen
    while running:
        for event in pygame.event.get():
            if event.type == QUIT:
                pygame.quit()
                sys.exit()

            elif event.type == MOUSEBUTTONDOWN:
                if event.button == 1 and paused_rect.collidepoint(event.pos):
                    paused = not paused
                    if paused:
                        pygame.time.set_timer(SUPPLY_TIME, 0)
                        pygame.mixer.music.pause()
                        pygame.mixer.pause()
                    else:
                        pygame.time.set_timer(SUPPLY_TIME, 30 * 1000)
                        pygame.mixer.music.unpause()
                        pygame.mixer.unpause()

            elif event.type == MOUSEMOTION:
                if paused_rect.collidepoint(event.pos):
                    if paused:
                        paused_image = resume_pressed_image
                    else:
                        paused_image = pause_pressed_image
                else:
                    if paused:
                        paused_image = resume_nor_image
                    else:
                       paused_image = pause_nor_image

            elif event.type == KEYDOWN:
                if event.key == K_SPACE:
                    if bomb_num:
                        bomb_num -= 1
                        bomb_sound.play()
                        for each in enemies:
                            if each.rect.bottom > 0:
                                each.active = False

            elif event.type == SUPPLY_TIME:
                supply_sound.play()
                if choice([True, False]):
                    bomb_supply.reset()
                else:
                    bullet_supply.reset()

            elif event.type == DOUBLE_BULLET_TIME:
                is_double_bullet = False
                pygame.time.set_timer(DOUBLE_BULLET_TIME, 0)

            elif event.type == INVINCIBLE_TIME:
                me.invincible = False
                pygame.time.set_timer(INVINCIBLE_TIME, 0)
                         

        # Increase difficulty based on user's score
        if level == 1 and score > 50000:
            level = 2
            upgrade_sound.play()
            # Add 3 small enemy planes, 2 medium enemy planes and 1 large enemy plane
            add_small_enemies(small_enemies, enemies, 3)
            add_mid_enemies(mid_enemies, enemies, 2)
            add_big_enemies(big_enemies, enemies, 1)
            # Increases the speed of small enemy planes
            inc_speed(small_enemies, 1)
        elif level == 2 and score > 300000:
            level = 3
            upgrade_sound.play()
            # Add 5 small enemy planes, 3 medium enemy planes and 2 large enemy planes
            add_small_enemies(small_enemies, enemies, 5)
            add_mid_enemies(mid_enemies, enemies, 3)
            add_big_enemies(big_enemies, enemies, 2)
            # Increases the speed of small enemy planes
            inc_speed(small_enemies, 1)
            inc_speed(mid_enemies, 1)
        elif level == 3 and score > 600000:
            level = 4
            upgrade_sound.play()
            # Add 5 small enemy planes, 3 medium enemy planes and 2 large enemy planes
            add_small_enemies(small_enemies, enemies, 5)
            add_mid_enemies(mid_enemies, enemies, 3)
            add_big_enemies(big_enemies, enemies, 2)
            # Increases the speed of small enemy planes
            inc_speed(small_enemies, 1)
            inc_speed(mid_enemies, 1)
        elif level == 4 and score > 1000000:
            level = 5
            upgrade_sound.play()
            # Add 5 small enemy planes, 3 medium enemy planes and 2 large enemy planes
            add_small_enemies(small_enemies, enemies, 5)
            add_mid_enemies(mid_enemies, enemies, 3)
            add_big_enemies(big_enemies, enemies, 2)
            # Increases the speed of small enemy planes
            inc_speed(small_enemies, 1)
            inc_speed(mid_enemies, 1)
