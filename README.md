# Ex-5 Rail-Fence-Program

# IMPLEMENTATION OF RAIL FENCE – ROW & COLUMN TRANSFORMATION TECHNIQUE

# AIM:

# To write a C program to implement the rail fence transposition technique.

# DESCRIPTION:

In the rail fence cipher, the plain text is written downwards and diagonally on successive "rails" of an imaginary fence, then moving up when we reach the bottom rail. When we reach the top rail, the message is written downwards again until the whole plaintext is written out. The message is then read off in rows.

# ALGORITHM:

STEP-1: Read the Plain text.
STEP-2: Arrange the plain text in row columnar matrix format.
STEP-3: Now read the keyword depending on the number of columns of the plain text.
STEP-4: Arrange the characters of the keyword in sorted order and the corresponding columns of the plain text.
STEP-5: Read the characters row wise or column wise in the former order to get the cipher text.

# PROGRAM
```python
def encrypt_rail_fence(text, key):
    rail = [['\n' for i in range(len(text))] for j in range(key)]

    dir_down = False
    row, col = 0, 0

    for c in text:
        if row == 0 or row == key - 1:
            dir_down = not dir_down

        rail[row][col] = c
        col += 1

        row = row + 1 if dir_down else row - 1

    # Read the matrix row by row
    result = []
    for i in range(key):
        for j in range(len(text)):
            if rail[i][j] != '\n':
                result.append(rail[i][j])

    return "".join(result)

# ---- MAIN ----
text = input("Enter plain text: ")
key = int(input("Enter key (number of rails): "))

cipher = encrypt_rail_fence(text, key)
print("Cipher text:", cipher)
```
# OUTPUT
<img width="1914" height="462" alt="Screenshot 2025-11-02 174111" src="https://github.com/user-attachments/assets/975c33e4-4262-4aaa-a5ab-9a1c2da442b4" />

# RESULT
Successfully implemented the program for the rail fence transposition technique.
