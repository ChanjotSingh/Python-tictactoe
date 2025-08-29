a1 = [1, 4, 7]
a2 = [2, 5, 8]
a3 = [3, 6, 9]

def print_board():
    for i in range(3):
        print(a1[i], a2[i], a3[i])

def mark_position(pos, mark):
    for i in range(3):
        if a1[i] == pos:
            a1[i] = mark
            return True
        elif a2[i] == pos:
            a2[i] = mark
            return True
        elif a3[i] == pos:
            a3[i] = mark
            return True
    return False

def check_win(mark):
    if all(x == mark for x in a1): return True
    if all(x == mark for x in a2): return True
    if all(x == mark for x in a3): return True
    for i in range(3):
        if a1[i] == mark and a2[i] == mark and a3[i] == mark:
            return True
    if a1[0] == mark and a2[1] == mark and a3[2] == mark:
        return True
    if a1[2] == mark and a2[1] == mark and a3[0] == mark:
        return True
    return False

print_board()
while True:
    a = int(input("Player 1 choose a position: "))
    if not mark_position(a, 'X'):
        print("Invalid move! Try again.")
        continue
    print_board()
    if check_win('X'):
        print("Player 1 wins!")
        break

    b = int(input("Player 2 choose a position: "))
    if not mark_position(b, 'O'):
        print("Invalid move! Try again.")
        continue
    print_board()
    if check_win('O'):
        print("Player 2 wins!")
        break

    filled = all(isinstance(x, str) for x in a1 + a2 + a3)
    if filled:
        print("Game Over! It's a draw.")
        break
