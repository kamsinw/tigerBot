# tigerBot
Lego spike prime robot project for Sierra canyon's Honors Engineering class.


## Goals: 
We want to be able to imitate the walking movement of a tiger and its pouncing action after the tiger sees an object, as well as making it roar through the speakers on the hub. In addition, we could try to implement the super sensitive hearing of the tiger through Arduino but that is set for future consideration after we get our basic goals done.

Walking:















  Our research:
Tigers walk one side at a time
Back leg moves before the front leg, so it is a staggered delay
When the tiger lifts its leg the paw goes down and then when it goes down the tiger’s paw flattens 
	Out implementation:
We want to use the motors, one in front and one in back, to create walking motion



Pouncing:


The hind legs are longer than the front legs
When the tiger lifts its leg the paw goes down and then when it goes down the tiger’s paw flattens 
Tigers have forward-facing eyes rather than one on each side of their head. This provides binocular vision because each eye's field of vision overlaps creating a three-dimensional image. Binocular vision enables them to accurately assess distances and depth which is extremely useful for maneuvering within their complex environment and stalking prey.



TIGER MOVEMENT:


Skeletal Structure:
Try to imitate joints in legs through 3D printing


Environmental Interaction:
Tigers are actually native to Asia (not Africa!)
Tigers main senses is vision and hearing, vision we can replicate
Tigers are specifically found in rain forests, grasslands, savannas and even mangrove swamps
Due to their native habitats, they are enabled to jump and pounce quickly to different destinations such as branches or on prey.
Movements to implement:
Sit to pounce
The robot slowly leans make and sits on hind legs, and based on ultra sonic sensor values, it decides when to pounce
After time, the robot “pseudo-learns” and decides to pounce after a longer distance

Walking 
Imitate the walking sequence of the tiger. The restriction is since we have only two motors, how will we sync up the front and back legs on one side versus the others
Use one motor for front, one for the back
Convert rotational motion to linear motion
Set motor timing so that the front will be slightly delayed in movement from the back
Since the hind legs are longer than the front legs, we have to add that into consideration



Things to learn:
	How to increase velocity of motors with gears
	Joint movement- Legos are stiff and not very flexible, possible 3d printed element


1.19.23
Components:
- Ultrasonic sensor
- Lego spike prime block
- Two small-sized Motor
- One large Motor
- Spare included and 3D-printed components for the body
- Possibly and arduino
- Possible code blocks:
	
For the project we decided to use Python 3 in order to code our robot. Included below is pseudo-code for the behavior of our robots. 
We did not include the proper syntax for simplicity sake 

``` python
#instantiate  motor 
#create motor pair
# instantiate distance sensor
# Define initial parameters
initial_distance_threshold = 10  # Initial distance threshold for pouncing
time_to_pseudo_learn = 60  # Time after which the robot pseudo-learns (in seconds)
pseudo_learned_distance_threshold = 15  # Updated distance threshold after pseudo-learning


# Function to simulate robot behavior
def robot_behavior():
	# Slowly lean back and sit on hind legs
	slowly_lean_back_and_sit()

	# Loop to continuously monitor ultrasonic sensor values
	while True:
    	# Get current distance from ultrasonic sensor
    	current_distance = read_ultrasonic_sensor()

    	# Check if it's time to pseudo-learn
    	if elapsed_time_since_start() >= time_to_pseudo_learn:
        	# Pseudo-learn by updating distance threshold
        	distance_threshold = pseudo_learned_distance_threshold
    	else:
        	distance_threshold = initial_distance_threshold

    	# Decide to pounce based on distance
    	if current_distance <= distance_threshold:
        	pounce()
        	break  # Exit the loop after pouncing

# Function to simulate slowly leaning back and sitting
def slowly_lean_back_and_sit():
	# Implement the code for slowly leaning back and sitting
	# This may involve adjusting servo motors or other mechanisms

# Function to read ultrasonic sensor values
def read_ultrasonic_sensor():
	# Implement the code to read values from the ultrasonic sensor
	# This may involve using a library or interacting with hardware

# Function to measure elapsed time since the start
def elapsed_time_since_start():
	# Implement the code to measure and return elapsed time
	# This may involve using a timer or tracking system time

# Function to simulate pouncing action
def pounce():
	# Implement the code for the robot to pounce
	# This may involve activating motors or performing specific actions

# Main program
robot_behavior()
```



WALKING
``` python
# Define walking parameters
step_duration = 1  # Duration of each step in seconds
leg_lift_height = 5  # Height to lift the legs during walking (in degrees)
leg_movement_angle = 30  # Angle of movement for the legs (in degrees)
offset = 60

# Function to simulate tiger walking
def tiger_walking():
	# Loop to continuously perform walking steps
	while True:
    	# Perform a step with the right side legs
    	move_legs('right', step_duration)

    	# Perform a step with the left side legs
    	move_legs('left', step_duration)

# Function to move the legs on one side
def move_legs(side, duration):
	# Sync up front and back legs on the specified side using only two motors
	if side == 'right':
    	lift_and_move_leg('front_right', leg_lift_height, leg_movement_angle, duration)
    	lift_and_move_leg('back_right', leg_lift_height, -leg_movement_angle, duration)
	elif side == 'left':
    	lift_and_move_leg('front_left', leg_lift_height, -leg_movement_angle, duration)
    	lift_and_move_leg('back_left', leg_lift_height, leg_movement_angle, duration)

# Function to lift and move a leg
def lift_and_move_leg(leg, lift_height, move_angle, duration):
	lift_leg(leg, lift_height)
	move_leg(leg, move_angle, duration)
	lower_leg(leg)

# Functions to control individual leg movements
def lift_leg(leg, height):
	# Implement the code to lift the specified leg to the specified height
	# This may involve adjusting servo motors or other mechanisms

def move_leg(leg, angle, duration):
	# Implement the code to move the specified leg by the specified angle
	# This may involve adjusting servo motors or other mechanisms

	# Simulate walking by maintaining the leg in the moved position for the specified duration
	wait(duration)

def lower_leg(leg):
	# Implement the code to lower the specified leg to the initial position
	# This may involve adjusting servo motors or other mechanisms

# Function to simulate a waiting period
def wait(duration):
	# Implement the code to pause execution for the specified duration
	# This may involve using a timer or a sleep function

# Main program
tiger_walking()

```



