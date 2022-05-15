# Elliott Wave

Chart Pattern

## Introduction

Elliott Waves are a system of repeating patterns discovered by Ralph Nelson Elliott. Elliott discovered 13 patterns in total, but the 5-3 pattern consisting of 8 waves is considered the basic one.

![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43282992445/original/rBSBOAO7z0NAm11u9j5P0JgRiIDbZ94odQ.png?1640270787)

  
###### According to Elliott's wave theory, waves are divided into "**Motive**” and "**Corrective**”. 

- **Motive waves** are price movements that coincide with the direction of the main trend, 
- **Corrective waves** are movements against the main trend. 

###### In the screenshot shown above:

- the motive waves are `(1), (3), (5), (a), and (c)`
- and corrective waves are `(2), (4), and (b)`

###### Also, according to Elliott, any basic model wave can be represented as:

- motive wave as `5` smaller waves
- corrective wave as `3` smaller waves 

###### Thus, the basic model `5-3` can be represented as:

- `2` waves of a higher wave level 
- and as `34` waves of a lower one


![](https://s3.amazonaws.com/cdn.freshdesk.com/data/helpdesk/attachments/production/43282992516/original/jjF-X0MN1G9GF2kvbk3aFJ73tV2C-g03oA.png?1640270802)

### The Chart Pattern Elliott Wave indicator is configured to recognize the most common wave patterns, which are built according to the following rules:

###### **Impulse (Motive wave):**

1.  Wave structure: `5-3-5-3-5`
2.  Wave `2` does not retrace more than `100%` of the length of wave `1`
3.  Wave `3` moves beyond the end of wave `1`
4.  Wave `3` cannot be the shortest among waves `1, 3, and 5`
5.  Wave `4` does not go beyond the level of wave `1`


###### **ZigZag (Corrective wave):**

1.  Wave structure: `5-3-5`
2.  Wave `b` is shorter than `a`
3.  Wave `c` goes beyond the level of wave `a`


- The indicator analyzes the last `600` bars in search of patterns, 
	- conditionally dividing them into `3` levels along the maximum length. 
- The start and end points of the waves in the found patterns are tied to the most suitable pivots. 
	- If there is no suitable pivot for the start or end point of the whole pattern, the indicator uses the **highest high** and **lowest low** values, respectively. 
- Then the indicator checks the rules for **Impulse** and **ZigZag** and 
	- draws the patterns that are the longest and most fitting (based on sub-wave patterns) - among those the algorithm initially found.


##### The following table is used to indicate the level that the wave belongs to:

Level | Five (Motive wave) | Three (Corrective wave)
----- | ----- | -----
Large | I, II, III, IV, V | A, B, C
Medium | (1), (2), (3), (4), (5) | (a), (b), (c)
Low | 1, 2, 3, 4, 5 | a, b, c

- This table does not correspond to the historical levels of the Elliott wave theory; 
	- it is conditional. 
- It displays the length or nesting level of the pattern.

## Inputs:

- **Source** - Source for the primary search.
- **Invert Pattern** - This flag allows you to change the direction of the pattern, to search for impulse in a downtrend, and a zigzag in an uptrend.
- **Length type** - How the wavelength is calculated when checking the rules of pattern construction:
- **Absolute** - the wavelength is calculated as the price difference between the start and end point of the wave.
- **Percent** - the wavelength is calculated as the percentage change in price between the start and end points of the wave.

## Important note:

When new data is received, the indicator updates and clarifies previously found patterns. Changing any settings of the indicator leads to its complete recalculation. *The result may differ from the expected one*.


  ![Elliot Wave Video - YouTube](https://www.youtube.com/watch?v=XP2z6RRnLQg)
