https://play.golang.org/p/24Wde42788

```
package main

import (
	"fmt"
	"reflect"
)

func main() {
	x := struct{Foo string; Bar int }{"foo", 2}

	v := reflect.ValueOf(x)

	values := make([]interface{}, v.NumField())

	for i := 0; i < v.NumField(); i++ {
	        myType := reflect.TypeOf(v.Field(i).Interface())
	fmt.Println(myType)
		values[i] = v.Field(i).Interface()
	}

	fmt.Println(values)
}
```