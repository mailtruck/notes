golang bindings: http://go-lang.cat-v.org/library-bindings

secret wip: https://play.golang.org/p/yXgRAfHnpg

## iterate over a struct /w reflect

> http://stackoverflow.com/questions/18926303/iterate-through-a-struct-in-go

```
import (
    "fmt"
    "reflect"
)

func main() {
    x := struct{Foo string; Bar int }{"foo", 2}

    v := reflect.ValueOf(x)

    values := make([]interface{}, v.NumField())

    for i := 0; i < v.NumField(); i++ {
        values[i] = v.Field(i).Interface()
    }

    fmt.Println(values)
}
```
## write a csv file

> https://golangcode.com/write-data-to-a-csv-file/


```
package main

import (
    "os"
    "log"
    "encoding/csv"
)

var data = [][]string{{"Line1", "Hello Readers of:"}, {"Line2", "golangcode.com"}}

func main() {
    file, err := os.Create("result.csv")
    checkError("Cannot create file", err)
    defer file.Close()

    writer := csv.NewWriter(file)
    defer writer.Flush()

    for _, value := range data {
        err := writer.Write(value)
        checkError("Cannot write to file", err)
    }
}

func checkError(message string, err error) {
    if err != nil {
        log.Fatal(message, err)
    }
}
```

## Appending to a slice

```
package main

import "fmt"

func main() {
	var s []int
	printSlice(s)

	// append works on nil slices.
	s = append(s, 0)
	printSlice(s)

	// The slice grows as needed.
	s = append(s, 1)
	printSlice(s)

	// We can add more than one element at a time.
	s = append(s, 2, 3, 4)
	printSlice(s)
}

func printSlice(s []int) {
	fmt.Printf("len=%d cap=%d %v\n", len(s), cap(s), s)
}
```

## Get the field names of a struct as strings

```
package main

import (
	"fmt"
	"reflect"
)

type Thing struct {
	Name string
	Address string
}

func main() {

	fieldNames := []string{}
	fmt.Println("Hello, playground")
	thing := Thing{"Ron", "1302 Justice Glen"}
	
	v := reflect.ValueOf(thing)
	
	for i := 0; i < v.NumField(); i++ {
		fieldName := v.Type().Field(i).Name
		fmt.Println(fieldName)
		fieldNames = append(fieldNames, fieldName)
	}
	
	fmt.Println(fieldNames)
	
}
```

## Stream data to a compressed csv
```
package main

import (
	"bufio"
	"compress/gzip"
	"encoding/csv"
	"fmt"
	"log"
	"os"
)

var data = [][]string{{"dingo", "starr"}, {"boshi", "fierce"}}

func main() {
	fmt.Println(data)
	s := "data.csv.gz"
	fi, err := os.OpenFile(s, os.O_WRONLY|os.O_APPEND|os.O_CREATE, 0660)
	if err != nil {
		log.Fatal(err)
	}
	defer fi.Close()

	gw := gzip.NewWriter(fi)
	defer gw.Close()

	writer := bufio.NewWriter(gw)
	defer writer.Flush()

	out := csv.NewWriter(writer)
	defer out.Flush()

	for _, value := range data {
		fmt.Println(value)
		out.Write(value)
	}
}
```