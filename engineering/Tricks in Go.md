## [Link](https://github.com/golang/go/wiki/SliceTricks)

## Notes
 - This primarily started as notes for the "Slice Tricks In Go" doc, but figured it may actually prove more useful as a general "go cheat sheet" that captures all the little workarounds, quick one liners, etc. that come with using Go
 - ### Appending a slice to another slice (sees)
    - **variadic arguments:** (the `...` syntax) packs arguments that you pass into a function  into one slice (and vice versa when calling that function)
    - **examples**
 	   - `a = append(a, b...)` appends slice b to slice a
 	   - alternatively you can do `a = append(a, 1, 2 ,3)` to append it element by element

### Copying an array
```go
a := []int{1,2,3}
b := make([]int, len(a))
copy(b,a) // builtin copy(dst, src []Type)```

```

### Delete (and Shift)
```go
a = append(a[:i], a[i+1:]...) 
// append elements before i (exclusive) to i+1 (until end)
// probably only do this for non-structs or pointers because it can cause potential memory problems
```

### Reverse elements
```go
for left, right := 0, len(a)-1; left < right; left, right = left+1, right-1 {
	a[left], a[right] = a[right], a[left]
}
```
 - explanation: for `left` and `right` indices that start at opposite ends of the slice, swap elements until the pointers cross

### Shuffle elements
 [import "math/rand"](https://pkg.go.dev/math/rand#Shuffle)

```go
// func Shuffle(n int, swap func(i, j int))
// uses the default pseudo-random range to swap elements

rand.Shuffle(len(a), func(i,j int) {
    a[i], a[j] = a[j], a[i]
})
```

### Sliding Window
 revisit after I've reviewed this pattern in [[Grokking the Coding Interview]]
 
 ```go
func slidingWindow(size int, input []int) [][]int {
	// returns the input slice as the first element
	if len(input) <= size {
		return [][]int{input}
	}

	// allocate slice at the precise size we need
	r := make([][]int, 0, len(input)-size+1)

	for i, j := 0, size; j <= len(input); i, j = i+1, j+1 {
		r = append(r, input[i:j])
	}

	return r
}
```

### Sets in Go
 - Go doesn't have sets as a built-in type or a contains function on slices/arrays for that matter. So it's nice to keep in mind that the "Go way of doing things" here is to make the type you want as a map:

```go
set := map[T]bool{...}
// technically you could also map to an empty struct
// which is somewhat more memory efficient, but I think 
// it kills readability and just isn't worth the dust of memory

// checking something is in the set is still fast ...
if set[x] {
  // do stuff
}

// alternatively the longer normal-map way of doing things
if val, ok := set[x]; ok {
  // do stuff here again
}```
Source: [contains method for a slice in go](https://stackoverflow.com/questions/10485743/contains-method-for-a-slice)

 ### Type Assertions & Type Casting
 - There's a subtle different and I think it's actually important to know the difference both to avoid getting tripped up AND because demonstrating that I understand the difference (and when to use one over the other) could look good during interviews
 - {{[[TODO]]}} need to expand on this a little more and write up a good example to better understand this stuff

 - Source: [Trying to convert interface to int](https://stackoverflow.com/questions/18041334/convert-interface-to-int), [Go Conversions](https://go.dev/ref/spec#Conversions), [Go Type Assertions](https://go.dev/ref/spec#Type_assertions)

### Strings, Bytes, Runes and Characters In Go
 - A string holds arbitrary bytes -- it's not required to hold Unicode or UTF-8 encoded text. A string == a slice of bytes. 
    - The post also talks about some nuances that comes with trying to print strings (since they can just be bytes) but skipping over that for the most part
 - Side note on how you can write a string literal like `const placeOfInterest = '⌘'`
    - **Go source code is UTF-8**, so the source code for the string literal is UTF-8 text. If that string literal contains no escape sequences, which a raw string cannot, the constructed string will hold exactly the source text between the quotes. 
    - So by definition and by construction the raw string will always contain a valid UTF-8 representation of its contents.
 - Re: what's expanded on in [[The Absolute Minimum Every Software Developer Should Know About Character Sets (No Excuses)]], the notion of a "character" in computing ambiguous, if we think of bytes (or a set of bytes) as containers that correspond to their Unicode symbol (i.e. code points), then it becomes a little clearer why we can't just say 1 byte == 1 character
 - Go introduces the concept of a **rune **to basically map to a code point i.e. an `int32`
 - Using a `for range` loop actually iterates through a UTF-8 string rune-by-rune, while a standard for loop, would actually iterate one byte at a time.
    - English alphabets can't tell the difference, but it's important if we do anything beyond those characters (nowadays emojis are a great example of how this is useful)
 - Sources: https://go.dev/blog/strings, [[The Absolute Minimum Every Software Developer Should Know About Character Sets (No Excuses)]]


