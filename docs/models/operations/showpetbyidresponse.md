# ShowPetByIDResponse


## Fields

| Field                                                   | Type                                                    | Required                                                | Description                                             |
| ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- |
| `ContentType`                                           | *string*                                                | :heavy_check_mark:                                      | HTTP response content type for this operation           |
| `Error`                                                 | [*components.Error](../../models/components/error.md)   | :heavy_minus_sign:                                      | unexpected error                                        |
| `Pet`                                                   | [*components.Pet](../../models/components/pet.md)       | :heavy_minus_sign:                                      | Expected response to a valid request                    |
| `StatusCode`                                            | *int*                                                   | :heavy_check_mark:                                      | HTTP response status code for this operation            |
| `RawResponse`                                           | [*http.Response](https://pkg.go.dev/net/http#Response)  | :heavy_minus_sign:                                      | Raw HTTP response; suitable for custom response parsing |