# Go Cheat Sheet

## Initial Setup

---

### Create Go Module

```go
go mod init {module name}
go build #builds the module
```

### "Hello World" Example

---

```go
package main
import "fmt"

func main() {
 fmt.Println("Hello, World")
}
```

- *Note:*
  - Every program is made up of ***packages***.
  - Program starts running in **`main`** package.

## Functions

---

- Types come *after* the variable name.
- Below, the function takes two integers in and returns one integer.

```go
func add(x int, y int) int {
 return x + y
}
```

- Types can be crammed together if they are the same data type:

```go
func add(x, y int) int {
 return x + y
}
```

- Multiple values can be returned from functions

```go
func swap(x, y string) (string, string) {
 return y, x
}

func main() {
 a, b := swap("hello", "world")
 fmt.Println(a, b)
}
```

```text
world hello
```

- Values can be returned by name if a variable name is specified with the return type. Those variables will be return by the function.

```go
func plus_five(x, y int) (a, b int) {
 a = x + 5
 b = y + 5
 return
} 
func main() {
 fmt.Println(plus_five(10, 20))
}
```

```text
15 25
```

- Function can be passed to a function
- A function can be closures

## Variables

---

- `var` declares a list of variables

```go
var i, j int = 10, 20
var isGo bool
isGo = true
// Can't mix types in var
//var k int, isC bool
// implicit type declaration can be mixed
var k, isC = 25, false
fmt.Println(i, j, isGo, k, isC)
```

- `:=` can be used for short

```go
k, isC := 25, false
```

### Basic Types

---

```go
bool
string
int  int8  int16  int32  int64
uint uint8 uint16 uint32 uint64 uintptr
byte // alias for uint8
rune // alias for int32
     // represents a Unicode code point
float32 float64
complex64 complex128
```

- Uninitialized variables are given default zero values. 0 for int, "" for strings and false for bools
- If type isn't specified explicitly type is inferenced from the context

```go
i := 10 // i is int
hello := "hello, world" // hello is string
```

- Type conversion is done with T(v)

```go
i := 10
d := float64(i)
```

- constants are declared with `const` keyword. Constants can be declared with `:=`.

```go
const PI = 3.14
```

## Conditional Statements

---

### if/else & else/if

```go
package main
import (
 "fmt"
 "bufio"
 "strconv"
 "strings"
 "os"
)
func main() {
 reader := bufio.NewReader(os.Stdin)
 strInp, _ := reader.ReadString('\n')
 strInp = strings.TrimSpace(strInp)
 intInp, _ := strconv.Atoi(strInp)
 if intInp < 0 {
     fmt.Println("negative")
 } else if intInp > 0 {
     fmt.Println("positive")
 } else {
     fmt.Println("zero")
 }
}
```

- If condition with statement. Variable scope declared in the statement is inside `if`

```go
package main
import (
 "fmt"
 "math"
)
func main() {
 x := -20
  if v := math.Abs(float64(x)); v >= 10 {
      fmt.Println("Too large to process: ", v)
  }
}
```

### Switch

---

- No fall through cases
- Evaluates from top to bottom, stops when a case succeed

```go
package main
import (
 "fmt"
 "math/rand"
 "time"
)
func cast_spell() string {
 spells := []string{
  "Oculus Reparo",
  "Alohomora",
     "Wingardium Leviosa",
 }
 max := len(spells) - 1
 rand.Seed(time.Now().UnixNano())
 index := rand.Intn(max + 1)
 return spells[index]
}
func main() {
 switch spell := cast_spell(); spell {
 case "Oculus Reparo":
     fix_glass()
 case "Alohomora":
     unlock()
 case "Wingardium Leviosa":
     float_object()
 default:
     break_wand()
 }
}
```

- Switch without argument can be used instead of an if/else if/else chain:

```go
switch {
 case input == "left":
  go_left()
 case input == "right":
     go_right()
 case input == "up":
  go_up()
 case input == "down":
     go_down()
 default:
     open_portal()
}
```

## Pointers

---

- There is no pointer arithmetical

```go
package main
import "fmt"
func main() {
 var p *int
 i := 10
 p = &i
 fmt.Printf("%v\n", *p)
}
```

## Structs

---

```go
package main
import "fmt"
type Pixel struct {
 R int
 G int
 B int
}
func main() {
  p := Pixel{5, 10, 0}
  fmt.Println(p.R, p.G, p.B)
}
```

- Pointers to struct can be used as `(*ptr).field`. Shortcut `ptr.field`:

```go
p := Pixel{5, 10, 0}
var q *Pixel
q = &p
r := &p // implicit type
```

- Struct initialization:

```go
a = Pixel{1, 2, 3}
b = Pixel{R: 2, B: 3} // G = 0
c = Pixel{} // R = 0, G = 0, B = 0
d = &Pixel{} // type &Pixel
```

## Arrays

---

```go
var arr [2]string
arr[0] = "hello"
arr[1] = "world"
list := [5]int{1, 2, 3, 4, 5}
var screen [1024]Pixel
screen := []Pixel{Pixel{1, 2, 3}, Pixel{1, 2, 3}} // implicit size
screen := []Pixel{{1, 2, 3}, {1, 2, 3},} // same as above
```

## Slice

---

- Slice are reference to an array

```go
var a [10]int
s := a[1:3] // from index 1 until 3. Includes a[1],a[2]
s := [:3] // from 0 until 3
s := [3:] // from 3 to end
s := [:] // full array
```

- Slices have length and capacity. Length is the number of elements and capacity is the underlying size.
- `make` function can be used to create zero initialized arrays

```go
arr := make([]int, 5) // 5 length, 5 capacity
arr := make([]int, 0, 5) // 0 length, 5 capacity
```

- `append` function can be used to dynamically grow an array

```go
var arr []int // len 0, cap 0
arr = append(arr, 1, 2) // append with element 1 and 2, now len 2, cap 2
```

- Iterate array with for range

```go
arr := []string{"hello", "world", "good", "bye"}
// use both index and value
for index, value := range arr {
  fmt.Println(index, value)
}
// use only value
for _, value := range arr {
  fmt.Println(value)
}
// use only index
for index, _ := range arr {
  fmt.Println(index)
}
```

## Maps

---

- Maps are key-value pairs

```go
var m map[string]int
m = make(map[string]int)
m["one"] = 1
m["two"] = 2
fmt.Println(m["one"])
```

- Short declaration

```go
m := map[string]int{
 "one": 1,
 "two": 2,
}
```

- Check if key exists

```go
value, ok := m["one"]
if ok {
 fmt.Println("Key exists with value", value)
} else {
 fmt.Println("Key does not exist")
}
```

- Delete a key

```go
delete(m, "one")
```

## Loop

---

### For Loops

- Basic for loop

```go
for i := 0; i < 10; i++ {
 fmt.Println(i)
}
```

- While loop

```go
i := 0
for i < 10 {
 fmt.Println(i)
 i++
}
```

- Infinite loop

```go
for {
 fmt.Println("Infinite loop")
}
```

### For With Range

- Iterate over a slice

```go
arr := []int{1, 2, 3, 4, 5}
for index, value := range arr {
 fmt.Println(index, value)
}
```

- Iterate over a map

```go
m := map[string]int{"one": 1, "two": 2}
for key, value := range m {
 fmt.Println(key, value)
}
```

- Iterate over a string

```go
str := "hello"
for index, char := range str {
 fmt.Printf("%d: %c\n", index, char)
}
```
