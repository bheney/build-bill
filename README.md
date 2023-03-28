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
