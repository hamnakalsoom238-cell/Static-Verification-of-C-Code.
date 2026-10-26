# Review Checklist - Static Code Verification

| Category | Results (Issues / OK) | Defect Description |
| :--- | :--- | :--- |
| **Initialization** | Issues | Uninitialized variables (`sum` in `averageAttack()`, `name` in `readBoss()`). |
| **Pointers** | Issues | Potential dangling pointer deletion in `defeatMonster()` (`delete m;` while `monsters` array still holds the dangling address). Also, missing deep copy constructor for `Game` class (shallow copy of pointers causes double-free crash in `copy` destructor). |
| **Arrays / Buffers** | Issues | Buffer overflow risk in `readBoss()` using raw `char* name = new char[10];` with `std::cin >> name;`. Also, array out-of-bounds loop condition in `totalMonsterHealth()` (`i <= monsterCount`). |
| **Loops** | Issues | Off-by-one error (`i <= monsterCount`) in `totalMonsterHealth()`, leading to out-of-bounds memory access. |
| **Arithmetic** | Issues | Division by zero or integer truncation in `averageAttack()` and `calculateDamage()`. |
| **Control Flow** | Issues | Missing return statement in `playerRank()` if score is $\le 100$, and incorrect assignment operator `=` used instead of equality `==` in `findMonster()`. |
| **Function Call** | Issues | Passing unvalidated/invalid IDs (e.g., passing `99` which doesn't exist) causes null-pointer dereference in `attackMonster()`. |
| **Classes** | Issues | Missing rule of three (copy constructor / assignment operator) in `Game` class, causing double-deletion issues when copied. |
