import pygame
import os

# Inicializar pygame
pygame.init()

# Configuración de la ventana
WINDOW_WIDTH = 800
WINDOW_HEIGHT = 600
window = pygame.display.set_mode((WINDOW_WIDTH, WINDOW_HEIGHT))
pygame.display.set_caption('Reproductor de Música')

# Variables de control
current_track = 0
playlist = [os.path.join('music', 'song1.mp3'), os.path.join('music', 'song2.mp3'), os.path.join('music', 'song3.mp3')]

# Función para cargar y reproducir la pista actual
def play_music():
    pygame.mixer.music.load(playlist[current_track])
    pygame.mixer.music.play()

# Bucle principal del juego
running = True
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
        elif event.type == pygame.KEYDOWN:
            if event.key == pygame.K_SPACE:
                play_music()
            elif event.key == pygame.K_RIGHT:
                current_track = (current_track + 1) % len(playlist)
                play_music()
            elif event.key == pygame.K_LEFT:
                current_track = (current_track - 1) % len(playlist)
                play_music()

    # Actualizar la pantalla
    pygame.display.flip()

# Salir de pygame
pygame.quit()
