# Robotics Fundamentals (No Hardware Required!)

## What is Robotics?

At its core, robotics is about creating systems that can:
1. **Sense** the environment
2. **Decide** what to do
3. **Act** based on decisions

**You don't need motors and circuits to learn these concepts!**

```python
# This IS robotics:
while True:
    # SENSE
    distance = robot.sense_forward()
    
    # DECIDE
    if distance < 2:
        action = "turn_right"
    else:
        action = "move_forward"
    
    # ACT
    robot.execute(action)
```

---

## Building a Grid World

Let's create a simple 2D world where our robot can live.

### The GridWorld Class

```python
class GridWorld:
    """A 2D grid environment for robots"""
    
    def __init__(self, width=10, height=10):
        self.width = width
        self.height = height
        self.obstacles = set()  # Set of (x, y) tuples
        self.goal = None
    
    def add_obstacle(self, x, y):
        """Place an obstacle at position"""
        if 0 <= x < self.width and 0 <= y < self.height:
            self.obstacles.add((x, y))
    
    def set_goal(self, x, y):
        """Set the goal position"""
        self.goal = (x, y)
    
    def is_obstacle(self, x, y):
        """Check if position has obstacle"""
        return (x, y) in self.obstacles
    
    def is_valid(self, x, y):
        """Check if position is within bounds and not blocked"""
        if not (0 <= x < self.width and 0 <= y < self.height):
            return False
        return not self.is_obstacle(x, y)
    
    def display(self, robot_pos=None):
        """Print a text representation of the world"""
        for y in range(self.height):
            row = ""
            for x in range(self.width):
                if robot_pos and (x, y) == robot_pos:
                    row += "R "  # Robot
                elif self.goal and (x, y) == self.goal:
                    row += "G "  # Goal
                elif (x, y) in self.obstacles:
                    row += "X "  # Obstacle
                else:
                    row += ". "  # Empty
            print(row)
        print()

# Create a world
world = GridWorld(8, 8)
world.add_obstacle(3, 3)
world.add_obstacle(3, 4)
world.add_obstacle(3, 5)
world.set_goal(7, 7)
world.display()
```

**Output:**
```
. . . . . . . . 
. . . . . . . . 
. . . . . . . . 
. . . X . . . . 
. . . X . . . . 
. . . X . . . . 
. . . . . . . . 
. . . . . . . G 
```

---

## Creating a Robot Class

```python
class Robot:
    """A simple robot that can move in a grid world"""
    
    # Direction constants
    NORTH = 0
    EAST = 1
    SOUTH = 2
    WEST = 3
    
    def __init__(self, world, x=0, y=0):
        self.world = world
        self.x = x
        self.y = y
        self.direction = self.NORTH
        self.step_count = 0
        self.log = []
    
    def get_position(self):
        """Return current position"""
        return (self.x, self.y)
    
    def get_direction_name(self):
        """Get direction as string"""
        directions = ["NORTH", "EAST", "SOUTH", "WEST"]
        return directions[self.direction]
    
    def turn_left(self):
        """Turn 90 degrees left"""
        self.direction = (self.direction - 1) % 4
        self.log.append(f"Step {self.step_count}: Turned left to {self.get_direction_name()}")
    
    def turn_right(self):
        """Turn 90 degrees right"""
        self.direction = (self.direction + 1) % 4
        self.log.append(f"Step {self.step_count}: Turned right to {self.get_direction_name()}")
    
    def get_forward_position(self):
        """Calculate position one step forward"""
        x, y = self.x, self.y
        
        if self.direction == self.NORTH:
            y -= 1
        elif self.direction == self.EAST:
            x += 1
        elif self.direction == self.SOUTH:
            y += 1
        elif self.direction == self.WEST:
            x -= 1
        
        return (x, y)
    
    def can_move_forward(self):
        """Check if robot can move forward"""
        next_x, next_y = self.get_forward_position()
        return self.world.is_valid(next_x, next_y)
    
    def move_forward(self):
        """Move forward one step if possible"""
        if self.can_move_forward():
            self.x, self.y = self.get_forward_position()
            self.step_count += 1
            self.log.append(f"Step {self.step_count}: Moved to ({self.x}, {self.y})")
            return True
        else:
            self.log.append(f"Step {self.step_count}: Cannot move forward - blocked!")
            return False
    
    def at_goal(self):
        """Check if robot reached the goal"""
        return (self.x, self.y) == self.world.goal
    
    def sense_forward(self):
        """Return distance to obstacle ahead (simple sensor)"""
        distance = 0
        x, y = self.x, self.y
        
        # Move in current direction until hitting obstacle or edge
        while True:
            if self.direction == self.NORTH:
                y -= 1
            elif self.direction == self.EAST:
                x += 1
            elif self.direction == self.SOUTH:
                y += 1
            elif self.direction == self.WEST:
                x -= 1
            
            distance += 1
            
            # Check if hit obstacle or boundary
            if not self.world.is_valid(x, y):
                return distance
            
            # Prevent infinite loop
            if distance > max(self.world.width, self.world.height):
                return distance
    
    def print_log(self):
        """Print all logged actions"""
        for entry in self.log:
            print(entry)
```

---

## Using the Robot

### Example 1: Manual Control

```python
# Create world and robot
world = GridWorld(8, 8)
world.add_obstacle(3, 3)
world.set_goal(5, 0)

robot = Robot(world, x=0, y=0)

# Manual commands
print("Initial state:")
world.display(robot.get_position())

robot.move_forward()  # Can't move (off grid)
robot.turn_right()
robot.move_forward()
robot.move_forward()
robot.turn_left()
robot.move_forward()

print("\nAfter movements:")
world.display(robot.get_position())

print("\nRobot log:")
robot.print_log()
```

### Example 2: Simple Autonomous Behavior

```python
def simple_navigator(robot, max_steps=50):
    """Navigate to goal using simple right-hand rule"""
    
    step = 0
    while not robot.at_goal() and step < max_steps:
        if robot.can_move_forward():
            robot.move_forward()
        else:
            robot.turn_right()
        
        step += 1
        
        # Show progress every 10 steps
        if step % 10 == 0:
            print(f"\nStep {step}:")
            robot.world.display(robot.get_position())
    
    if robot.at_goal():
        print(f"\n🎉 Goal reached in {robot.step_count} steps!")
    else:
        print(f"\n❌ Goal not reached after {max_steps} steps")
    
    return robot.at_goal()

# Use it
world = GridWorld(8, 8)
world.set_goal(7, 7)
robot = Robot(world, x=0, y=0)

simple_navigator(robot)
```

---

## Sensors: Virtual Detection

### Distance Sensor

```python
# How far until obstacle?
distance = robot.sense_forward()
print(f"Distance ahead: {distance}")

# Use it for decisions
if distance < 2:
    print("Obstacle very close - turning!")
    robot.turn_right()
elif distance < 5:
    print("Obstacle ahead - preparing to turn")
```

### Obstacle Detection (Boolean)

```python
def has_obstacle_ahead(robot):
    """Simple yes/no obstacle detection"""
    return not robot.can_move_forward()

# Use it
if has_obstacle_ahead(robot):
    robot.turn_left()
else:
    robot.move_forward()
```

### Goal Detection

```python
def distance_to_goal(robot):
    """Manhattan distance to goal"""
    if not robot.world.goal:
        return None
    
    gx, gy = robot.world.goal
    return abs(robot.x - gx) + abs(robot.y - gy)

# Use it
dist = distance_to_goal(robot)
print(f"Distance to goal: {dist}")
```

---

## The Sense-Think-Act Loop

This is the heart of robotics:

```python
def autonomous_robot(robot, max_steps=100):
    """Demonstrate sense-think-act loop"""
    
    for step in range(max_steps):
        # SENSE
        can_move = robot.can_move_forward()
        dist_to_goal = distance_to_goal(robot)
        
        # THINK (decide based on sensors)
        if robot.at_goal():
            action = "celebrate"
        elif can_move and dist_to_goal > 5:
            action = "move_forward"
        elif can_move:
            action = "move_carefully"
        else:
            action = "turn_and_search"
        
        # ACT (execute decision)
        if action == "celebrate":
            print(f"🎉 Goal reached in {step} steps!")
            break
        elif action == "move_forward":
            robot.move_forward()
        elif action == "move_carefully":
            robot.move_forward()
            # Check surroundings more carefully
        elif action == "turn_and_search":
            robot.turn_right()
        
        # Display every few steps
        if step % 20 == 0:
            print(f"\nStep {step}:")
            robot.world.display(robot.get_position())
```

---

## Practical Example: Library Robot

```python
class LibraryRobot(Robot):
    """A robot that finds books in a library"""
    
    def __init__(self, world, x=0, y=0):
        super().__init__(world, x, y)
        self.books_found = []
    
    def find_book(self, book_location):
        """Navigate to a book location"""
        self.world.set_goal(*book_location)
        print(f"Searching for book at {book_location}")
        
        # Simple navigation
        while not self.at_goal():
            if self.can_move_forward():
                self.move_forward()
            else:
                self.turn_right()
            
            if self.step_count > 100:
                print("Book not found - path blocked")
                return False
        
        self.books_found.append(book_location)
        print(f"✓ Book found! Total books: {len(self.books_found)}")
        return True

# Use the library robot
library = GridWorld(15, 15)
# Add shelves as obstacles
for x in range(3, 12):
    library.add_obstacle(x, 5)
    library.add_obstacle(x, 10)

lib_robot = LibraryRobot(library, x=0, y=0)
lib_robot.find_book((14, 14))
library.display(lib_robot.get_position())
```

---

## Summary

✅ **Robotics = Sense + Decide + Act**  
✅ **Simulation teaches real concepts**  
✅ **OOP perfect for robot design**  
✅ **Grid worlds enable navigation**  
✅ **Virtual sensors provide data**  
✅ **Decision algorithms control behavior**  

---

**Next:** Build more complex robots in your capstone project!
