# Snake and Ladder Game – Python Project

This is a classic Snake and Ladder game built using Python.  
It's a simple, interactive, terminal-based game for two players.  
Roll the dice, climb ladders, avoid snakes, and race to the finish.

Pythin code for the game :

import turtle
import random
import cv2  # Import OpenCV for video playback

screen = turtle.Screen()

def movePlayer1(player, position):
    yPos = (position-1) // 10
    xPos = (position-1) % 10
    y = -170 + yPos * 37
    if yPos % 2 == 0:
        x = -170 + xPos * 38
    else:
        x = 170 - xPos * 38
    player.goto(x, y)

def movePlayer2(player, position):
    yPos = (position-1) // 10
    xPos = (position-1) % 10
    y = -170 + yPos * 37
    if yPos % 2 == 0:
        x = -165 + xPos * 38
    else:
        x = 165 - xPos * 38
    player.goto(x, y)

# Function to play snake video
def play_snake_video():
    cap = cv2.VideoCapture('C:/Users/Mahek/Downloads/Untitled video - Made with Clipchamp.mp4')  # Replace with your video file path
    while cap.isOpened():
        ret, frame = cap.read()
        if not ret:
            break
        cv2.imshow('Snake Attack!', frame)
        if cv2.waitKey(30) & 0xFF == ord('q'):
            break
    cap.release()
    cv2.destroyAllWindows()

# Setup the Snakes & Ladders board
screen.setup(800, 800)
screen.bgpic('C:/Users/Mahek/OneDrive/Desktop/snakeboard2.png')
# Initialise first player...
player1 = turtle.Turtle()
player1.shape("circle")
player1.speed(5)
player1.color("#810081")
player1.pensize(15)
player1.penup()

player2 = turtle.Turtle()
player2.shape("triangle")
player2.speed(5)
player2.color("#008f91")
player2.pensize(15)
player2.penup()

# Position the first player to the bottom left corner of the board (Position 1)
player1Position = 1
movePlayer1(player1, player1Position)
player2Position = 1
movePlayer2(player2, player2Position)

gameOver = False
while not gameOver:

    print("Player 1:")
    input("Press enter to throw the dice...")
    dice = random.randint(1, 6)
    print("You've rolled a " + str(dice))
    player1Position += dice
    movePlayer1(player1, player1Position)
    
    if player1Position == 5:
        print("Climbing up the ladder!")
        player1Position = 35
    elif player1Position == 8:
        print("Climbing up the ladder!")
        player1Position = 13
    elif player1Position == 11:
        print("Climbing up the ladder!")
        player1Position = 52
    elif player1Position == 59:
        print("Climbing up the ladder!")
        player1Position = 83
    elif player1Position == 72:
        print("Climbing up the ladder!")
        player1Position = 91
    elif player1Position == 85:
        print("Climbing up the ladder!") 
        player1position = 96
        player1Position = 96
        
    elif player1Position == 36:
        print("Snake!Run down")
        player1Position = 22
        play_snake_video() 
    elif player1Position == 63:
        print("Snake!Run down")
        player1Position = 41
        play_snake_video() 
    elif player1Position == 67:
        print("Snake!Run down")
        player1Position = 48
        play_snake_video() 
    elif player1Position == 84:
        print("Snake!Run down")
        player1Position = 66
        play_snake_video() 
    elif player1Position == 93:
        print("Snake!Run down")
        player1Position = 86 
        play_snake_video() 
        
    if player1Position > 100:
        player1Position = 100 - (player1Position - 100)
    
    movePlayer1(player1, player1Position)

    if player1Position == 100:
        print("---- Player 1 wins!!! ----")
        gameOver = True

    print("Player 2:")
    input("Press enter to throw the dice...")
    dice = random.randint(1, 6)
    print("You've rolled a " + str(dice))
    player2Position += dice
    movePlayer2(player2, player2Position)

    if player2Position == 5:
        print("Climbing up the ladder!")
        player2Position = 35
    elif player2Position == 8:
        print("Climbing up the ladder!")
        player2Position = 13
    elif player2Position == 11:
        print("Climbing up the ladder!")
        player2Position = 52
    elif player2Position == 59:
        print("Climbing up the ladder!")
        player2Position = 83
    elif player2Position == 72:
        print("Climbing up the ladder!")
        player2Position = 91
    elif player2Position == 85:
        print("Climbing up the ladder!")
        player1Position = 96
    
    elif player2Position == 36:
        print("Snake!Run down")
        player2Position = 22
        play_snake_video() 
    elif player2Position == 63:
        print("Snake!Run down")
        player2Position = 41
        play_snake_video() 
    elif player2Position == 67:
        print("Snake!Run down")
        player2Position = 48
        play_snake_video() 
    elif player2Position == 84:
        print("Snake!Run down")
        player2Position = 66
        play_snake_video() 
    elif player2Position == 93:
        print("Snake!Run down")
        player2Position = 86 
        play_snake_video() 
    if player2Position > 100:
        player2Position = 100 - (player2Position - 100)

    movePlayer2(player2, player2Position)

    if player2Position == 100:
        print("---- Player 2 wins!!! ----")
        gameOver = Truess

