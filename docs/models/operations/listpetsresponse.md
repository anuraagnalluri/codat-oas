# ListPetsResponse


## Fields

| Field                                                   | Type                                                    | Required                                                | Description                                             |
| ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- |
| `ContentType`                                           | *string*                                                | :heavy_check_mark:                                      | HTTP response content type for this operation           |
| `StatusCode`                                            | *int*                                                   | :heavy_check_mark:                                      | HTTP response status code for this operation            |
| `RawResponse`                                           | [*http.Response](https://pkg.go.dev/net/http#Response)  | :heavy_check_mark:                                      | Raw HTTP response; suitable for custom response parsing |
| `Pets`                                                  | [][components.Pet](../../models/components/pet.md)      | :heavy_minus_sign:                                      | A paged array of pets                                   |
| `Error`                                                 | [*components.Error](../../models/components/error.md)   | :heavy_minus_sign:                                      | unexpected error                                        |
| `Headers`                                               | map[string][]*string*                                   | :heavy_check_mark:                                      | N/A                                                     |