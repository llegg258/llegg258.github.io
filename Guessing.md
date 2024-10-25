```mermaid
---
title: Random Number Guessing Game
---
flowchart TD
    subgraph RandomNumberGen
    direction TB
        RN[Randomly Generated Number] --> IsBetween0And1000{Is the number between 0 and 1000?}
        IsBetween0And1000 --->|No| RN
        IsBetween0And1000 -->|Yes| Truncate[Truncate to give whole number]
        Truncate --> RWN(Random Whole Number)
    end

    subgraph UserInput
    direction TB
        Start([Start])-->GetInput[User, please guess a whole number from 0 to 1000.] -->|UserNum| CheckIfNumber{Check if entry contains any letters or characters other than numbers?}
        CheckIfNumber -->|True| GetInput
        CheckIfNumber -->|False| Check0To1000{Check if user number is from 0 to 1000}
        Check0To1000 -->|False| GetInput
        Check0To1000 -->|True| CheckIfDecimal{Are there any decimals?}
        CheckIfDecimal -->|True| GetInput
        CheckIfDecimal -->|False| InputValid(Input is Valid) --> UserGuess([User's Guess])
    end

RandomNumberGen & UserInput==> Comparison{Is the User's guess correct?}
Comparison -->|Equal To| Correct(Congratulations! You're right!)
Comparison -->|Greater Than| TooHigh(Your guess was too high. Please try again.) --> UserInput
Comparison -->|Less Than| TooLow(Your guess was too low. Please try again.) --> UserInput
```

## Flowchart description
1. Generate a random number with these conditions:
    * Must be between 0 and 1000
    * Must be a whole number
2. Request User's guess of a number
    * Check if user's input is valid
        * Is it a number?  Meaning no letters or characters.
        * Is it a whole number?
        * Is it between 0 and 1000?
3. Compare user's guess to generated number
    * If the guess is the same as the random number, respond with "Congratulations! You're right!"
    * If the guess is too high, respond with "Your guess was too high." and ask them for a new number.
    * If the guess is too low, respond with "Your guess was too low." and ask them for a new number.