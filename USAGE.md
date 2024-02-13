<!-- Start SDK Example Usage [usage] -->
```go
package main

import (
	"context"
	codatoas "github.com/anuraagnalluri/codat-oas"
	"log"
)

func main() {
	s := codatoas.New()

	var limit *int = codatoas.Int(21453)

	ctx := context.Background()
	res, err := s.Pets.ListPets(ctx, limit)
	if err != nil {
		log.Fatal(err)
	}

	if res.Pets != nil {
		// handle response
	}
}

```
<!-- End SDK Example Usage [usage] -->