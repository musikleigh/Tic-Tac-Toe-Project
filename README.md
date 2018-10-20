# Tic-Tac-Toe-Project

      from IPython.display import clear_output
    def display_board(board):
        clear_output()
        print(board[7]+' |',board[8]+' |',board[9])
        print('--|---|--')
        print(board[4]+' |',board[5]+' |',board[6])
        print('--|---|--')
        print(board[1]+' |',board[2]+' |',board[3])

    test_board = ['#','X','O','X','O','X','O','X','O','X']

    display_board(test_board)

    test_board=['#',' ',' ',' ',' ',' ',' ',' ',' ',' ']

    def player_markers():
        player1=' '
        while not (player1=='X' or player1=='O'):
            player1=input('Player 1, would you like to be X or O? ').upper()
        if player1 == 'X':
            return ('X','O')
        else:
            return ('O','X')


    player_markers()

    def place_marker(board, marker, position):
        board[position]=marker

    place_marker(test_board,'X',9)

    display_board(test_board)

    def check_win(board,mark):
        return (board[1]==board[2]==board[3]==mark) or (board[4]==board[5]==board[6]==mark) or (board[7]==board[8]==board[9]==mark) or (board[1]==board[4]==board[7]==mark) or (board[2]==board[5]==board[8]==mark) or (board[3]==board[6]==board[9]==mark) or (board[1]==board[5]==board[9]==mark) or (board[3]==board[5]==board[7]==mark)


    test_board=['#','X','X','X',' ','X','O','X','O','X']

    check_win(test_board,'X')

    import random
    def choose_first():
        flip=random.randint(0,1)
        if flip==0:
            return 'Player 1'
        else:
            return 'Player 2'
    print(choose_first()+' will go first!')

    tictactoe_players=['Player 1','Player 2']

    def space_check(board,position):
        return board[position]==' '

    space_check(test_board,9)

    def full_board_check(board):
        for i in range(1,10):
            if space_check(board,i)==True:
                return False
        return True

    full_board_check(test_board)

    def player_choice(board):
        player_position=0
        while player_position not in [1,2,3,4,5,6,7,8,9] or not space_check(board,player_position):
            player_position=int(input('Choose a position:1-9'))
        return player_position

    player_choice(test_board)

    def replay():
        replay_input=' '
        while not (replay_input=='yes' or replay_input=='no'):
            replay_input=input('Would you like to play again?').lower()
        return replay_input=='yes'

    replay()

    print('Welcome to Tic Tac Toe!')
    while True:
        the_board=[' ']*10
    
        player1,player2=player_markers()

        turn=choose_first()
        print(turn+' will go first!')

        play_game=input('Ready to play? y or n? ')

        if play_game=='y':
            game_on=True
        else:
            game_on=False

        #ask players in order where to place marker
        while game_on:

            if turn=='Player 1':
                display_board(the_board)

                player1_position=player_choice(the_board)

                place_marker(the_board,player1,player1_position)

                if check_win(the_board,player1):
                    display_board(the_board)
                    print('Player 1 has won!')
                    game_on=False

                else:
                    if full_board_check(the_board):
                        print("The game is a tie!")
                        game_on=False

                    else:
                        turn='Player 2'

            else:
                display_board(the_board)

                player2_position=player_choice(the_board)

                place_marker(the_board,player2,player2_position)

                if check_win(the_board,player2):
                    display_board(the_board)
                    print('Player 2 has won!')
                    game_on=False
                else:
                    if full_board_check(the_board):
                        print('The game is a tie!')
                        game_on=False

                    else:
                        turn='Player 1'
    
    
    
    

    if not replay():
        break
    

