<!-- Start SDK Example Usage -->
```go
package main

import (
	"context"
	codatoas "github.com/anuraagnalluri/codat-oas"
	"log"
)

func main() {
	s := codatoas.New()

	ctx := context.Background()
	res, err := s.Pets.CreatePets(ctx)
	if err != nil {
		log.Fatal(err)
	}

	if res.StatusCode == http.StatusOK {
		// handle response
	}
}

```
<!-- End SDK Example Usage -->