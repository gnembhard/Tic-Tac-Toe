# Project 1 : Tic-Tac-Toe
# Desccription: This program is a classic game of Tic-Tac-Toe that is played between the user and a generated computer using the Minimax Algorithm
and initiating the alpha beta pruning due to having runtime and recursion errors 

        
# Player Definitions
player_1 = 'X'
player_2 = 'O'  # computer

# Function to check for available space
def free_space(position, board):
    return board[position] == ' '

# Function to display the Tic-Tac-Toe board
def print_board(board):
    print(board[7] + '|' + board[8] + '|' + board[9])
    print('-+-+-')
    print(board[4] + '|' + board[5] + '|' + board[6])
    print('-+-+-')
    print(board[1] + '|' + board[2] + '|' + board[3])

# Function to check for a win and checks rows, columns and diagonial for winning combo
def check_win(current_player, board):
    for i in range(1, 9, 3):
        # Check rows
        if board[i] == board[i + 1] == board[i + 2] == current_player:
            return True

    for i in range(1,4):
        # Check column
        if board[i] == board[i + 3] == board[i + 6] == current_player:
            return True
    #check diagonal
    if board[1] == board[5] == board[9] == current_player:
        return True
    if board[3] == board[5] == board[7] == current_player:
        return True

    return False

# Function to check for a tie
def check_tie(board):
    return " " not in board[1:]

# Minimax algorithm with alpha-beta pruning due to recursion error/ referenced from Rischal Hurbans Grokking artificial intelligence algorithms 
def minimax(board, depth, alpha, beta, maximizing):
    if check_win(player_1, board):
        return -1
    elif check_win(player_2, board):
        return 1
    elif check_tie(board):
        return 0

    if maximizing:
        max_eval = -float('inf')
        for i in range(1, 10):
            if free_space(i, board):
                board[i] = player_2
                eval = minimax(board, depth + 1, alpha, beta, False)
                board[i] = ' '
                max_eval = max(max_eval, eval)
                alpha = max(alpha, eval)
                if beta <= alpha:
                    break  
        return max_eval
    else:
        min_eval = float('inf')
        for i in range(1, 10):
            if free_space(i, board):
                board[i] = player_1
                eval = minimax(board, depth + 1, alpha, beta, True)
                board[i] = ' '
                min_eval = min(min_eval, eval)
                beta = min(beta, eval)
                if beta <= alpha:
                    break  
        return min_eval

# Find the best move for player_2 (computer)
def best_position(board):
    best_move = -1
    best_score = -float('inf')
    for i in range(1, 10):
        if free_space(i, board):
            board[i] = player_2
            score = minimax(board, 0, -float('inf'), float('inf'), False)
            board[i] = ' '
            if score > best_score:
                best_score = score
                best_move = i
    return best_move

# Main game loop
def main():
    # Initializes Board
    while True:
        current_player = player_1
        board = [' ' for x in range(10)]
        print("Welcome to Tic-Tac-Toe Beta v1")
        while True:
            # initializes Game
            print_board(board)
            print(f"Player {current_player}'s turn.")
            if current_player == player_1:
                position = int(input("Enter a position (1-9): "))
                if 1 <= position <= 9 and free_space(position, board):
                    board[position] = current_player
                else:
                    print("Invalid move. Try again.")
                    continue
            else:
                position = best_position(board)
                board[position] = current_player

            if check_win(current_player, board):
                print_board(board)
                print(f"Player {current_player} wins!")
                break

            if check_tie(board):
                print_board(board)
                print("It's a draw!")
                break

            current_player = player_2 if current_player == player_1 else player_1
           # Restart 
        play_again = input('Do you want to play again? (Y/N): ')
        if play_again.lower() != 'y' and play_again.lower() != 'yes':
            break

# Ensures the main func is executed
if __name__ == "__main__":
    main()
