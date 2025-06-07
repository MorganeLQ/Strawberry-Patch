# Strawberry-Patch

import pygame

class StrawberryPatch:
    def __init__(self):
      #general setup
      pygame.init()

      pygame.display.set_caption('Strawberry Patch')
      self.display = pygame.display.set_mode((800, 700))

      #clock
      self.clock = pygame.time.Clock()
       
      #movement
      self.movement = [False, False, False, False]
   
    def run(self):
      
      #import background image
      bg_surf = pygame.image.load('Images/Background.jpeg').convert_alpha()
      #ground surface
      ground = pygame.image.load('Images/ground.png').convert_alpha()

      #importing player image
      player = pygame.image.load('Images/Player.png').convert_alpha()
      #size of player
      player = pygame.transform.scale(player, (50, 60))
      #create a rectangle around the player
      player_rect = player.get_rect(center = (400, 350))
   
      while True:
          self.display.blit(player, player_rect)
          self.player_rect[1] += self.movement[1] - self.movement[0]
         #event loop
          for event in pygame.event.get():
             #closing the game
              if event.type == pygame.QUIT:
                 pygame.quit()
                 exit()
              if event.KEYDOWN:
                 if event.key == pygame.K_UP:
                    self.movement[0] = True
                 if event.key == pygame.K_DOWN:
                    self.movement[1] = True
                 if event.key == pygame.K_RIGHT:
                    self.movement[2] = True
                 if event.key == pygame.K_LEFT:
                    self.movement[3] = True
              if event.KEYUP:
                 if event.key == pygame.K_UP:
                    self.movement[0] = False
                 if event.key == pygame.K_DOWN:
                    self.movement[1] = False
                 if event.key == pygame.K_RIGHT:
                    self.movement[2] = False
                 if event.key == pygame.K_LEFT:
                    self.movement[3] = False
          #Display
          #update surface color
          self.display.fill('pink')
          #draw the background
          self.display.blit(bg_surf, (0,0))
      
          #draw the ground
          self.display.blit(ground, (50, 600))
         
          #move player to the right
          player_rect.left += 1
          #position of player
          self.display.blit(player, (player_rect))
          
          pygame.display.update()
          self.clock.tick(120)
      
      pygame.quit() 

StrawberryPatch().run()
