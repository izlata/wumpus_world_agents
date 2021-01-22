# wumpus_world_agents
The Wumpus World Agents (Probabilistic, Q-learning)


### The Wumpus World Environment

The rules of the environment were mostly taken from Russell and Norvig, Artificial Intelligence: A Modern Approach.

The Wumpus World is a grid of squares surrounded by walls (represents a cave), where each square can contain agents and objects. 
* The Agent always starts in the lower left corner - in the code it is labelled as (0, 0), facing to the right (Agent’s orientation - East).
*	The Agent dies if it enters a square containing a pit or a live monster Wumpus. It is safe to enter a square with a dead Wumpus.
*	The Agent's goal is to find the gold and bring it back to the start as quickly as possible, without being killed, and climb out of the cave. Also, the agent may be allowed to climb out of the cave without gold. 
*	The game ends either when the Agent dies or when the Agent climbs out of the cave.

The locations of the gold and the Wumpus are chosen randomly, with a uniform distribution, from the squares other than the start square. In addition, each square other than the start can be a pit, with probability = pit_prob

The Agent is facing one of four possible directions (Agent’s orientation): North, South, East or West.

**The Agent’s Actions:**
*	The Agent can go Forward
*	Turn Right by 90°
*	Turn Left by 90°
*	The action Grab can be used to pick up the gold if it is in the same square as the Agent
*	The action Shoot can be used to fire an arrow in a straight line in the direction the agent is facing, the arrow continues until it either kills the Wumpus or hits a wall. The Agent has only one arrow
*	The action Climb, can be used to climb out of the cave, but only from the start square

**The Agent’s Percepts:**
*	In the square containing the Wumpus and in the directly (not diagonally) adjacent squares, the Agent will receive a Stench
*	In the squares directly adjacent to a pit, the Agent will perceive a Breeze
*	In the square where the gold is, the Agent will perceive a Glitter
*	When an Agent walks into a wall it will perceive a Bump
*	When the Wumpus is killed, it emits a woeful Scream that can be perceived anywhere in the cave

The Percept also contains the **reward** calculated by the environment after each Agent's action : +1000 for climbing out of the cave with the gold, -1000 for falling into a pit or being eaten by the Wumpus, -1 for each action taken and -10 for using the arrow.

An environment is initialized with the following parameters:
-	width of the grid
-	height of the grid
-	allow climb without gold
-	pit probability: the probability of a pit being added to each square except (0, 0)

The standard game is an initialization of (4, 4, True, 0.2).

Notes:
-	The Agent must only have access to the Percepts. The Agent should not be able to access any other information about the state of the Environment (where the Wumpus is, whether there is a pit in a location, etc.)
-	The Wumpus and pits do not move during a game, but they will move from one game to the next

