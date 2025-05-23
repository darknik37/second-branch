# second-branch
«Мой второй репозиторий на GitHub
def print_board(board):
    for row in board:
        print(" | ".join(row))
        print("-" * 9)

def check_winner(board):
    # Проверка строк
    for row in board:
        if row[0] == row[1] == row[2] != " ":
            return row[0]

    # Проверка столбцов
    for col in range(3):
        if board[0][col] == board[1][col] == board[2][col] != " ":
            return board[0][col]

    # Проверка диагоналей
    if board[0][0] == board[1][1] == board[2][2] != " ":
        return board[0][0]
    if board[0][2] == board[1][1] == board[2][0] != " ":
        return board[0][2]

    return None

def is_board_full(board):
    for row in board:
        if " " in row:
            return False
    return True

def tic_tac_toe():
    board = [[" " for _ in range(3)] for _ in range(3)]
    current_player = "X"

    while True:
        print_board(board)
        print(f"Ход игрока {current_player}")

        try:
            row = int(input("Введите номер строки (0, 1, 2): "))
            col = int(input("Введите номер столбца (0, 1, 2): "))
        except ValueError:
            print("Пожалуйста, введите числа 0, 1 или 2!")
            continue

        if row not in [0, 1, 2] or col not in [0, 1, 2]:
            print("Некорректный ввод. Числа должны быть 0, 1 или 2!")
            continue

        if board[row][col] != " ":
            print("Эта клетка уже занята!")
            continue

        board[row][col] = current_player

        winner = check_winner(board)
        if winner:
            print_board(board)
            print(f"Игрок {winner} победил!")
            break
      
        if is_board_full(board):
            print_board(board)
            print("Ничья!")
            break

        current_player = "O" if current_player == "X" else "X"

if name == "main":
    tic_tac_toe()  
