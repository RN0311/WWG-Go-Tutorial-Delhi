![CLI](https://github.com/RN0311/WWG-Go-Tutorial-Delhi/blob/master/img/cli.png)
## Build a "Tower of Hanoi" program in Go
Let's understand through this program, mechanics of writing and compiling programs in Go.
<br >

First create a file named ``` tower_of_hanoi.go ```.Then in the main package create the function main.
Now print out the line "Tower of Hanoi!". 
```Go
package main
import fmt
func main() {
	fmt.Println("Tower of Hanoi!")
	}
```
Firstly, let's understand the what is ``` Tower of Hanoi ``` and logic to solve.<br >

**Introduction**: The game "Towers of Hanoi" uses three rods. 
A number of disks is stacked in decreasing order from the bottom to the top of one rod, i.e. the largest disk at the bottom and the smallest one on top.  
**Problem Statement**: You've to move tower of disks from one rod to another rod.
**Constraints**: 
* Only one disk must be moved at a time.
* Only the most upper disk from one of the rods can be moved during a single move.
* It can be put on another rod, if this rod is empty or if the most upper disk of this rod is larger 
than the one which is moved.<br >

![Hanoi](https://github.com/RN0311/WWG-Go-Tutorial-Delhi/blob/master/img/tower.png)
