```
package main

import (
	"encoding/json"
	"log"
	"net/http"
)

type Res struct {
	Salutation string
	Mood       string
}

func main() {
	http.HandleFunc("/", func(w http.ResponseWriter, r *http.Request) {
		res := Res{
			Salutation: "Ahoy dingo!",
			Mood:       "⚓",
		}

		w.Header().Set("Content-Type", "application/json")

		json.NewEncoder(w).Encode(res)

	})

	log.Fatal(http.ListenAndServe(":8080", nil))
}
```