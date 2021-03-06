The deriveTraverse function applies a given function to each element of a list, returning a list of results in the same order or an error.

Given the following input:

```go
package traverse

import "strconv"

func toInts(ss []string) ([]int, error) {
	return deriveTraverse(strconv.Atoi, ss)
}
```

goderive will generate the following code:

```go
// Code generated by goderive DO NOT EDIT.

package traverse

// deriveTraverse returns a list where each element of the input list has been morphed by the input function or an error.
func deriveTraverse(f func(string) (int, error), list []string) ([]int, error) {
	out := make([]int, len(list))
	var err error
	for i, elem := range list {
		out[i], err = f(elem)
		if err != nil {
			return nil, err
		}
	}
	return out, nil
}
```