Robot MDP

States: idle, low battery, broken down, finished all tasks
Actions: idle (recharge), help human, clean house
Rewards: break down (-5), run out of battery (-1), idle (0), clean house (+1), help human (+3), finish all tasks (+10)
Transitions:
- idle (recharge), from idle or low battery: go to idle (1.0)
- help human, from idle: idle (0.6), low battery (0.3), broken down (0.1)
- clean house, from idle: idle (0.6), low battery (0.3), finished all tasks (0.1)
- help human or clean house, from low battery: run out of battery and go to idle (0.5), low battery (0.3), broken down (0.2)
- if the robot breaks down or runs out of battery, it gets that penalty instead of the task reward
Initial state: idle
End states: broken down, finished all tasks

How it behaves:
- on low battery the robot should recharge, because working there often ends in running out of battery or breaking down
- from idle, help human pays more per step (+3) but risks breaking down (-5) and clean house pays less but is the only way to finish (+10)

Process:
- first version: one state idle, break down and run out of battery were listed as actions, I had no probabilities, end states ended at a total score -6 or +10
- edits: added states low battery, broken down, finished all tasks, I changed break down and run out of battery into random outcomes, I added transition probabilities

Possible extension:
- clean house removes one room (0.8) and at 0 rooms the robot has finished all tasks (+10)
- help human gives +3 only if a human is asking and requests appear randomly like 0.3 per step
