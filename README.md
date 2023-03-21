# Deviations From Proposal
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
        * I capped the max number of BeepBops per stage to 5.
        * Similarly, the max number of Boopzerkerz is 3.
        * Total enemy population algorithm remains unchanged.
        * Boopzerkez count is assigned semi-randomly.
        * BeepBop count is the difference.
