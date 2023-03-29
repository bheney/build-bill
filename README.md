# Deviations From Proposal

## Naming convention
* BeepBops are Phantoms
    * This name is cooler and a better description.
    * I wanted to use a Danny Phantom sprite.

## Enemy count and population
* In the proposal I wanted to have the total count of enemies randomly generated.
    * I did not explicitly say how enemy typing would be assigned, but my first thought was:
        * For each enemy in the range of enemies generated, assign a random type.
        * Populate that enemy.
* This approach will not work without the use of cloning.
    * As a work-around, I would need to create a sprite for every possible enemy.
        * Without any restrictions on distribution, with a maximum of 8 enemies per stage, I would need to create and manage 16 sprites to cover each worst-case scenario.
        * Sprites would be activated and populated based on the same randomization algorithm.
    * To keep things manageable, I altered the algorithm so that I only have 8 sprites to worry about.
        * I capped the max number of Phantoms per stage to 5.
        * Similarly, the max number of Boopzerkerz is 3.
        * Total enemy population algorithm remains unchanged.
        * Boopzerkez count is assigned semi-randomly.
        * Phantom count is the difference.

## Stage construction
* I would have liked to built the stage dynamically to account for future changes to point zones or change the colors level by level,
* This is harder than it's worth in Scratch, so 4 zones and their boundaries are hard-coded.

## Key precedence
* When controlling Bill, direction keys have precedence in the following order:
    * Up
    * Down
    * Left
    * Right
* That is, no matter what other keys are pressed, if the 'up' key is pressed, Bill will move up
* If any other arrow keys are pressed, Bill cannot move right.
* This structure exists because:
    * The event blocks are OS-dependent. If the OS is configured to delay holding a key from its initial press, Scratch recieves the same signal
        * This causes a start-stop-start motion for Bill
    * The sensing blocks are not OS dependent and do not have this limitation
        * The sensing blocks are implemented in nested if statements.
        * Early blocks essentialy override the later blocks.

## Wall construciton
* Walls are created as clones, otherwise there would be 16 * 12 * 2 = 384 sprites to manage with the current 30 px character sizes
* It should be impossible to exceed Scratch's 300 clone/sprite limit as Bill is not allowed to cross walls (192 max)

## Enemy movement
* The enemy movement algorithm is not as refined as I had hoped.
    * Idealy, enemies would follow the maze out towards Bill.
    * This is somewhat beyond Scratch's capabilities:
        * When enemies encounter a wall, there is no way to access that wall's orientation as a clone (see above).
        * It is not effective to record a history of Bill's movement. When an enemy encouters a wall, there is no way to know which wall it is or where to begin retracing the history.
    * Instead of following walls to get to Bill, enemies choose a random random direction when they encounter a corner in the maze.
* There is another oddity in enemy movemnt. I will call it the Karate Oddity:
    * Before moving, enemies must determine where the walls are so that they don't bump into them or walk through them.
    * Becuase walls are clones, the 'distance to' block gets confused. Instead, enemy sprites 'premove' in each direction to determine if it is a legal move.
    * This looks odd because Scratch will not accurately calculate collisions for hidden sprites. The enemy sprites must remain visible durring this process.
    * The movement is imperceptably quick, but the sprites appear to flail as they rotate between premoves.
    * It doesn't impact game performance, and if I cared about making this look perfect, I wouldn't be doing it in Scratch.

# Future Improvements

## Points
* I got a little ambitious with my project proposal. Admitedly, instead of finding something that Scratch could do, I tried to make Scratch do something that I wanted to do. There are no points in this implimentations.
    * It's not that points would be technically difficult to implement, but it is just one thing I did not give myself time to develop.

## Artwork
* Graphic design is not my passion.
* I had a lot of mechanics and interactions to define in this game and artwork took a back seat.
