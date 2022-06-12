# ACEtictactoe
Tic Tac Toe for ACE

import os       
    
board = [' ',' ',' ',' ',' ',' ',' ',' ',' ',' ']    
player = 1
   
########Parameters##########    
Win = 1    
Draw = -1    
Running = 0    
Stop = 1    
###########################    
Game = Running    
Mark = 'X'    

#To print player's name
if __name__ == "__main__":
 
    print("Player A")
    player1 = input("Enter the name : ")
    print("\n")
    
    print("Player B")
    player2 = input("Enter the name : ")
    print("\n")
     

#To draw the board
def Board():    
    print(" %c | %c | %c " % (board[1],board[2],board[3]))    
    print("___|___|___")    
    print(" %c | %c | %c " % (board[4],board[5],board[6]))    
    print("___|___|___")    
    print(" %c | %c | %c " % (board[7],board[8],board[9]))    
    print("   |   |   ")    
   
#To check if position is still empty   
def CheckPosition(x):    
    if(board[x] == ' '):    
        return True    
    else:    
        return False    
   
#To check if player has won    
def CheckWin():    
    global Game    
    #Winning condition - Horizontal    
    if(board[1] == board[2] and board[2] == board[3] and board[1] != ' '):    Game = Win    
    elif(board[4] == board[5] and board[5] == board[6] and board[4] != ' '):    Game = Win    
    elif(board[7] == board[8] and board[8] == board[9] and board[7] != ' '):    Game = Win    
    
    #Winning condition - Vertical   
    elif(board[1] == board[4] and board[4] == board[7] and board[1] != ' '):    Game = Win    
    elif(board[2] == board[5] and board[5] == board[8] and board[2] != ' '):    Game = Win    
    elif(board[3] == board[6] and board[6] == board[9] and board[3] != ' '):    Game = Win    
    
    #Winning condition - Diagonal    
    elif(board[1] == board[5] and board[5] == board[9] and board[5] != ' '):    Game = Win    
    elif(board[3] == board[5] and board[5] == board[7] and board[5] != ' '):    Game = Win    
    
    #Tie or Draw   
    elif(board[1]!=' ' and board[2]!=' ' and board[3]!=' ' and board[4]!=' ' and board[5]!=' ' and board[6]!=' ' and board[7]!=' ' and board[8]!=' ' and board[9]!=' '):    
        Game = Draw    
    else:            
        Game = Running    
    
print("Tic-Tac-Toe")    
print("Player A [X] --- Player B [O]\n")    
print()    
print()    
print("Please Wait...")    
while(Game == Running):    
    #os.system('cls')    
    Board()    
    if(player % 2 != 0):    
        print("Player A's Turn")    
        Mark = 'X'    
    else:    
        print("Player B's Turn")    
        Mark = 'O'    
    choice = int(input("Chose a number between [1-9] to mark : "))
    
    if(CheckPosition(choice)):    
        board[choice] = Mark    
        player+=1
        CheckWin()

    
#os.system('cls')    
Board()    
if(Game==Draw):    
    print("Draw Game")    
elif(Game==Win):    
    player-=1    
    if(player%2!=0):    
        print("Player A Won")    
    else:    
        print("Player B Won")    
