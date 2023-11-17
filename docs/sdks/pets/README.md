# Pets
(*Pets*)

## Overview

CRUD pet resource.

### Available Operations

* [ListPets](#listpets) - List all pets
* [CreatePets](#createpets) - Create a pet
* [ShowPetByID](#showpetbyid) - Info for a specific pet

## ListPets

List all pets

### Example Usage

```go
package main

import(
	codatoas "github.com/anuraagnalluri/codat-oas"
	"context"
	"log"
)

func main() {
    s := codatoas.New()


    var limit *int = 21453

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

### Parameters

| Parameter                                             | Type                                                  | Required                                              | Description                                           |
| ----------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- |
| `ctx`                                                 | [context.Context](https://pkg.go.dev/context#Context) | :heavy_check_mark:                                    | The context to use for the request.                   |
| `limit`                                               | **int*                                                | :heavy_minus_sign:                                    | How many items to return at one time (max 100)        |


### Response

**[*operations.ListPetsResponse](../../models/operations/listpetsresponse.md), error**
| Error Object       | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| sdkerrors.SDKError | 400-600            | */*                |

## CreatePets

Create a pet

### Example Usage

```go
package main

import(
	codatoas "github.com/anuraagnalluri/codat-oas"
	"context"
	"log"
	"net/http"
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

### Parameters

| Parameter                                             | Type                                                  | Required                                              | Description                                           |
| ----------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- |
| `ctx`                                                 | [context.Context](https://pkg.go.dev/context#Context) | :heavy_check_mark:                                    | The context to use for the request.                   |


### Response

**[*operations.CreatePetsResponse](../../models/operations/createpetsresponse.md), error**
| Error Object       | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| sdkerrors.SDKError | 400-600            | */*                |

## ShowPetByID

Info for a specific pet

### Example Usage

```go
package main

import(
	codatoas "github.com/anuraagnalluri/codat-oas"
	"context"
	"log"
)

func main() {
    s := codatoas.New()


    var petID string = "string"

    ctx := context.Background()
    res, err := s.Pets.ShowPetByID(ctx, petID)
    if err != nil {
        log.Fatal(err)
    }

    if res.Pet != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                             | Type                                                  | Required                                              | Description                                           |
| ----------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- |
| `ctx`                                                 | [context.Context](https://pkg.go.dev/context#Context) | :heavy_check_mark:                                    | The context to use for the request.                   |
| `petID`                                               | *string*                                              | :heavy_check_mark:                                    | The id of the pet to retrieve                         |


### Response

**[*operations.ShowPetByIDResponse](../../models/operations/showpetbyidresponse.md), error**
| Error Object       | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| sdkerrors.SDKError | 400-600            | */*                |
