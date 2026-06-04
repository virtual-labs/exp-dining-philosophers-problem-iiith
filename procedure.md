## Interface Overview

The simulation interface consists of three main sections:

1. **Controls Panel (Left)**: Contains the Reset button and Legend
2. **Simulation Area (Center)**: Shows the interactive visualization and different tabs
3. **Action Log (Right)**: Records all actions taken by philosophers


## How to Use the Simulation

### Basic Controls

- **Reset Button**: Click to restart the simulation with all philosophers thinking and all chopsticks available
- **Tooltips**: Hover over elements with your mouse to see additional information


### Interacting with Philosophers

1. Click on a philosopher (numbered circle) to change their state:

1. Clicking a **thinking** philosopher (gray) makes them **hungry** (yellow)
2. Clicking a **hungry** philosopher attempts to pick up chopsticks
3. Clicking an **eating** philosopher (green) makes them finish eating and return to thinking





### Interacting with Chopsticks

1. Click on a chopstick (rectangular bar between philosophers) to:

1. Pick up an **available** chopstick (blue) for a hungry philosopher
2. Put down a **taken** chopstick (red)





### Understanding Chopstick Assignment

- Philosopher 1 uses chopsticks 1 and 5
- Philosopher 2 uses chopsticks 2 and 1
- Philosopher 3 uses chopsticks 3 and 2
- Philosopher 4 uses chopsticks 4 and 3
- Philosopher 5 uses chopsticks 5 and 4


Each philosopher's left chopstick has the same number as the philosopher, and their right chopstick is the previous one (or chopstick 5 for philosopher 1).

## Tabs Explanation

The simulation offers five tabs with different content:

### 1. Simulation Tab

This is the main interactive visualization where you can:

- See the circular table with philosophers and chopsticks
- Interact with philosophers and chopsticks
- Observe state changes in real-time
- View alert messages when actions cannot be completed


### 2. Manual Guide Tab

Provides detailed instructions on:

- How to interact with philosophers and chopsticks
- Chopstick assignment details
- How to create and observe deadlock
- How to create and observe starvation
- Learning tips for getting the most out of the simulation


### 3. Theory Tab

Explains the theoretical background of the Dining Philosophers problem:

- Origin and purpose of the problem
- Basic setup and rules
- Key concepts illustrated by the problem


### 4. Deadlock Tab

Focuses on understanding deadlock in the context of the Dining Philosophers:

- What causes deadlock in this scenario
- Step-by-step instructions to create a deadlock
- Solutions to prevent deadlock


### 5. Starvation Tab

Explains the concept of starvation:

- How starvation differs from deadlock
- How to observe starvation in the simulation
- Solutions to prevent starvation


## Understanding the Visualization

### Philosopher States

- **Gray**: Thinking - philosopher is currently thinking
- **Yellow**: Hungry - philosopher wants to eat and is trying to acquire chopsticks
- **Green**: Eating - philosopher has both chopsticks and is eating


### Chopstick States

- **Blue**: Available - chopstick can be picked up
- **Red**: Taken - chopstick is being held by a philosopher


## Creating and Observing Deadlock

To create a deadlock:

1. Reset the simulation
2. Click on each philosopher to make them hungry (yellow)
3. Click on each left chopstick to have philosophers pick them up
4. Observe that no philosopher can pick up their right chopstick
5. The simulation will detect this deadlock condition


This demonstrates a circular wait condition where each philosopher is waiting for a resource held by another philosopher.

## Creating and Observing Starvation

To observe starvation:

1. Reset the simulation
2. Make two non-adjacent philosophers (e.g., 1 and 3) repeatedly eat and think
3. Observe that other philosophers (e.g., 2, 4, and 5) rarely get a chance to eat
4. The simulation will detect starvation when the difference in eating counts becomes significant


This demonstrates unfair resource allocation where some processes (philosophers) are denied resources while others repeatedly acquire them.

## Action Log

The Action Log panel records all events in the simulation with timestamps:

- State changes of philosophers
- Picking up and putting down chopsticks
- Eating counts
- Deadlock and starvation detection


This log helps you understand the sequence of events and analyze patterns that lead to problems.

## Tips for Effective Learning

1. **Start Simple**: Begin by making one philosopher hungry and observe the process
2. **Create Patterns**: Try different patterns of philosopher actions
3. **Compare Solutions**: After creating deadlock, try different solutions to prevent it
4. **Use the Log**: Review the action log to understand the sequence of events
5. **Try All Tabs**: Each tab provides different insights into the problem


## Troubleshooting

- **Can't Pick Up a Chopstick?**: Make sure there's a hungry philosopher adjacent to that chopstick
- **Philosopher Won't Eat?**: A philosopher needs both left and right chopsticks to eat
- **Reset Not Working?**: If the simulation seems stuck, refresh the page


## Mobile Device Usage

For the best experience:

- Use the simulation in landscape orientation on mobile devices
- A rotation message will appear if your device is in portrait mode
- Ensure your screen is large enough to see all elements clearly


Enjoy exploring the Dining Philosophers problem and discovering the challenges of concurrent programming!