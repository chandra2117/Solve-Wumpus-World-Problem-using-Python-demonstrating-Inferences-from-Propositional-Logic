# Solve-Wumpus-World-Problem-using-Python-demonstrating-Inferences-from-Propositional-Logic
## Name:
## Register Number:
## Aim:
To solve Wumpus World Problem using Python demonstrating Inferences from Propositional Logic

## Problem Description
#### Wumpus World
The Wumpus world is a simple world example to illustrate the worth of a knowledge-based agent and to represent knowledge representation.
The figure below shows a Wumpus world containing one pit and one Wumpus. There is an agent in room [1,1]. The goal of the agent is to exit the Wumpus world alive. The agent can exit the Wumpus world by reaching room [4,4]. The wumpus world contains exactly one Wumpus and one pit. There will be a breeze in the rooms adjacent to the pit, and there will be a stench in the rooms adjacent to Wumpus.

<img width="433" height="328" alt="image" src="https://github.com/user-attachments/assets/41ea4294-f9e7-4fd3-ac8c-126841d73749" />


#### Wumpus World Representation
This is a python program that uses propositional logic sentences to check which rooms are safe.

It is assumed that there will always be a safe path that the agent can take to exit the Wumpus world. The logical agent can take four actions: Up, Down, Left and Right. These actions help the agent move from one room to an adjacent room. The agent can perceive two things: Breeze and Stench.
## Pogram:

```

wumpus = [["Save", "Breeze", "PIT", "Breeze"],
          ["Smell", "Save", "Breeze", "Save"],
          ["WUMPUS", "GOLD", "PIT", "Breeze"],
          ["Smell", "Save", "Breeze", "PIT"]]

# Initial Variables
row = 0         # Player starts at top-left corner
column = 0
arrow = True     # Player has an arrow initially
player = True    # Controls the game loop
score = 0        # Starting score

while player:
    choice = input("press u to move up\npress d to move down\npress l to move left\npress r to move right\n")
    if choice == "u":
        if row != 0:
            row -= 1
        else:
            print("move denied")

        print("current location: ", wumpus[row][column], "\n")

    elif choice == "d":
        if row != 3:
            row += 1
        else:
            print("move denied")

        print("current location: ", wumpus[row][column], "\n")

    elif choice == "l":
        if column != 0:
            column -= 1
        else:
            print("move denied")

        print("current location: ", wumpus[row][column], "\n")

    elif choice == "r":
        if column != 3:
            column += 1
        else:
            print("move denied")

        print("current location: ", wumpus[row][column], "\n")

    else:
        print("move denied")

    # Check for Wumpus smell and shooting logic
    if wumpus[row][column] == "Smell" and arrow:
        arrow_choice = input("do you want to throw an arrow-->\npress y to throw\npress n to save your arrow\n")
        if arrow_choice == "y":
            arrow_throw = input("press u to throw up\npress d to throw down\npress l to throw left\npress r to throw right\n")
            if arrow_throw == "u":
                if row > 0 and wumpus[row - 1][column] == "WUMPUS":
                    print("wumpus killed!")
                    score += 1000
                    print("score: ", score)
                    wumpus[row - 1][column] = "Save"
                    wumpus[1][0] = "Save"
                    wumpus[3][0] = "Save"
                else:
                    print("arrow wasted...")
                    score -= 10
                    print("score: ", score)
            elif arrow_throw == "d":
                if row < 3 and wumpus[row + 1][column] == "WUMPUS":
                    print("wumpus killed!")
                    score += 1000
                    print("score: ", score)
                    wumpus[row + 1][column] = "Save"
                    wumpus[1][0] = "Save"
                    wumpus[3][0] = "Save"
                else:
                    print("arrow wasted...")
                    score -= 10
                    print("score: ", score)
            elif arrow_throw == "l":
                if column > 0 and wumpus[row][column - 1] == "WUMPUS":
                    print("wumpus killed!")
                    score += 1000
                    print("score: ", score)
                    wumpus[row][column - 1] = "Save"
                    wumpus[1][0] = "Save"
                    wumpus[3][0] = "Save"
                else:
                    print("arrow wasted...")
                    score -= 10
                    print("score: ", score)
            elif arrow_throw == "r":
                if column < 3 and wumpus[row][column + 1] == "WUMPUS":
                    print("wumpus killed!")
                    score += 1000
                    print("score: ", score)
                    wumpus[row][column + 1] = "Save"
                    wumpus[1][0] = "Save"
                    wumpus[3][0] = "Save"
                else:
                    print("arrow wasted...")
                    score -= 10
                    print("score: ", score)

            arrow = False

    # If player meets Wumpus
    if wumpus[row][column] == "WUMPUS":
        score -= 1000
        print("\nWumpus here!!\nYou Die\nYour score is: ", score, "\n")
        break

    # If player reaches GOLD
    if wumpus[row][column] == "GOLD":
        score += 1000
        print("Congratulations! You found the GOLD!")
        print("Your final score is: ", score)
        break

    # If player falls in PIT
    if wumpus[row][column] == "PIT":
        score -= 1000
        print("Ahhhhh!!!!\nYou fell in pit.\nYour score is: ", score, "\n")
        break

```

## Input and Output:
<img width="1353" height="668" alt="image" src="https://github.com/user-attachments/assets/e8a70b23-0da7-4b3b-82d7-fe5fd0c856b9" />

<img width="1397" height="647" alt="image" src="https://github.com/user-attachments/assets/8b93200c-36b8-4cb2-9863-aba5ac23ee68" />

## Result:
Thus the program was successfully executed.
