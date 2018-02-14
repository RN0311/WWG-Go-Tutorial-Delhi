![CLI](https://github.com/RN0311/WWG-Go-Tutorial-Delhi/blob/master/img/cli.png)
## Build a "Tower of Hanoi" program in Go
Let's understand through this program, mechanics of writing and compiling programs in Go.
<br >

First create a file named ``` tower_of_hanoi.go ```.Then in the main package create the function main.
Now print out the line "Tower of Hanoi!". 
```Go
package main

import (
	"fmt"
	"time"
)
func main() {
	fmt.Println("Tower of Hanoi!")
	}
```
Firstly, let's understand the what is ``` Tower of Hanoi ``` and logic to solve.<br >

**Introduction**: The game "Towers of Hanoi" uses three rods. 
A number of disks is stacked in decreasing order from the bottom to the top of one rod, i.e. the largest disk at the bottom and the smallest one on top.  
**Problem Statement**: You've to move tower of disks from one rod to another rod.<br >
**Constraints**: 
* Only one disk must be moved at a time.
* Only the most upper disk from one of the rods can be moved during a single move.
* It can be put on another rod, if this rod is empty or if the most upper disk of this rod is larger 
than the one which is moved.<br >
Let visualize using below infographic!
![Hanoi](https://github.com/RN0311/WWG-Go-Tutorial-Delhi/blob/master/img/tower.png)
Now it's code.
```Go
package main

import (
	"fmt"
	"time"
)

const Towers = 3
const Disks = 5

type Hanoi [Towers][]int

func main() {
        fmt.Println("Tower of Hanoi!")
	var state Hanoi
	state.init(Disks)
	state.move(Disks, 0, 1, 2)
}

func (h *Hanoi) init(n int) {
	h[0] = make([]int, n)
	for i := range h[0] {
		h[0][i] = n - i
	}
	h.print()
}

func (h *Hanoi) move(n, a, b, c int) {
	if n <= 0 {
		return
	}
	h.move(n-1, a, c, b)
	disk := h[a][len(h[a])-1]
	h[a] = h[a][:len(h[a])-1]
	h[c] = append(h[c], disk)
	h.print()
	h.move(n-1, b, a, c)
}

func (h *Hanoi) print() {
	fmt.Print("\f")
	for i := Disks; i >= 0; i-- {
		for j := 0; j < Towers; j++ {
			if i == 0 {
				fmt.Print("_/||\\_")
			} else if len(h[j]) >= i {
				fmt.Printf("  %02d  ", h[j][i-1])
			} else {
				fmt.Print("  ||  ")
			}
		}
		fmt.Println()
	}
	fmt.Println()
	time.Sleep(time.Second / 5)
}
```
