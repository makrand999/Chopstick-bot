# Chopsticks AI Bot

Welcome to the **Chopsticks AI Bot**, a strategic hand game implemented with the **Monte Carlo Tree Search (MCTS)** algorithm. This AI bot allows you to play against a computer opponent in a turn-based game of Chopsticks.

[click here to play](https://makrand999.github.io/Chopstick-bot/)

---

## **Game Rules**

Chopsticks is a two-player hand game where the goal is to "kill" both of your opponent's hands by reducing their hand counts to zero. Below are the rules and gameplay instructions:

### **Basic Rules**

1. **Starting State**:
   - Each player begins with **one finger** on each hand.
   - Game state representation:
     - Player Hands: `[1, 1]`
     - Opponent Hands: `[1, 1]`

2. **Game Objective**:
   - The goal is to make both of your opponent's hands **dead** by reducing their hand values to **0**.

3. **Gameplay**:
   - Players take turns selecting an available move during their turn.
   - A hand becomes **dead (0)** if its finger count reaches **5 or more**.

4. **Move Options**:
   - Players can perform one of the following actions during their turn:

     **1. Attack**:  
     - Use one of your hands to add its finger count to one of your opponent's hands.
     - The resulting total **must not exceed 5 fingers**. If the sum exceeds 5, the move is invalid.
     - Example:
       - Your hand: `2`
       - Opponent’s hand: `3`
       - **Invalid Attack**: `2 + 3 = 5` (exceeds the limit).

     **2. Split**:  
     - Redistribute the total fingers between your two hands.
     - Example:
       - Your hands: `[3, 0]`
       - Split to: `[1, 2]`.

5. **Turn Rotation**:
   - Players alternate turns.
   - The active player chooses their move, and then the turn switches to the opponent.

---

### **Additional Rules**

1. **Attack Restrictions**:
   - You cannot attack if the total sum of fingers on your hand and the target opponent's hand exceeds **5 fingers**.

2. **Modulo Arithmetic**:
   - If a hand reaches exactly **5 fingers** during an attack, it becomes dead (`0`).
   - Example:
     - Hand with `5 fingers → 5 % 5 = 0`.

3. **Splitting Rules**:
   - You can only split if the total fingers on your hands allow a valid redistribution.
   - Splitting affects only your own hands and does not impact the opponent's hands.

---

### **Winning the Game**
- The game ends when both of the opponent's hands are dead (`[0, 0]`).
- The player with live hands remaining is declared the winner.

---

## **How to Use Game Options**

There are two main actions: **Attack** and **Split**.

### **1. Attack**
- Each player's hands are identified as `0` and `1`.  
  Example: If the AI's hands are `[1, 2]`, hand `0` has `1` finger, and hand `1` has `2` fingers.

- You can attack by adding the finger count from one of your hands to one of the AI's hands.  
  Example:  
  - If your hands are `[2, 1]` and the AI's hands are `[3, 2]`, you can:
    - Attack from your hand `0` to the AI's hand `1`.
    - This results in: AI's hands = `[3, (2 + 2)] = [3, 4]`.

### **2. Split**
- Redistribute the total fingers on your hands.  
  **Note**: You can only move fingers to your **left hand (hand `0`)**.

- Example: If your hands are `[2, 3]`:
  - Move `1` finger to hand `0`: `[2, 3] → [1, 4]`.
  - Move `0` fingers to hand `0`: `[2, 3] → [0, 5] = [0, 0]` (both hands are dead).
  - Move `3` fingers to hand `0`: `[2, 3] → [3, 2]`.

---

## **Example Gameplay**

### **Starting State**
- Player Hands: `[1, 1]`
- Opponent Hands: `[1, 1]`

### **Player 1's Turn (Attack)**:
- Player 1 attacks Opponent's first hand using their first hand:
  - Opponent Hands: `[1, 1] → [(1 + 1), 1] = [2, 1]`.

### **Player 2's Turn (Split)**:
- Opponent splits their hands: `[2, 1] → [1, 2]`.

### **Player 1's Turn (Attack)**:
- Player 1 attacks Opponent's second hand with their second hand:
  - Opponent Hands: `[1, 2] → [1, (2 + 1)] = [1, 3]`.

### **Invalid Attack Example**:
- Player 1 tries to attack Opponent's first hand with their first hand:
  - Opponent's first hand: `2`
  - Player's attacking hand: `4`
  - **Invalid Attack**: `2 + 4 = 6` (sum exceeds 5).

---

## **How the AI Works**

This AI bot uses the **Monte Carlo Tree Search (MCTS)** algorithm to determine the best move. The MCTS process involves:

1. **Simulating Moves**: Running multiple simulations to explore possible future game states.
2. **Evaluating Outcomes**: Assessing the success rates of moves based on simulated outcomes.
3. **Choosing the Best Move**: Selecting the move with the highest win probability.

The AI's decision-making is dynamic and adapts based on the game state.

---

## **Features**
- **Strategic AI**: Uses MCTS to provide a challenging opponent.
- **Interactive Gameplay**: Allows players to choose their moves and play against the AI.
- **Customizable Settings**: Modify the number of simulations for the AI to adjust difficulty.

---

Enjoy the game and see if you can outsmart the AI! 🖐️✨
