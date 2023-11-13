# oas

These files are generated and bundled from our internal OpenAPI specs.

You can browse interactive versions of our OAS on [our docs](https://docs.codat.io/).

### API specs

| API | Description | JSON | YAML |
| :- | :- | :- | :- |
| [Common API](https://docs.codat.io/codat-api#/) | Manage the building blocks of Codat, including companies, connections, and more.  | [JSON](https://raw.githubusercontent.com/codatio/oas/main/json/Codat-Common.json) | [YAML](https://raw.githubusercontent.com/codatio/oas/main/yaml/Codat-Common.yaml)
| [Accounting API](https://docs.codat.io/accounting-api#/) | Access standardized accounting data from our accounting integrations.  | [JSON](https://raw.githubusercontent.com/codatio/oas/main/json/Codat-Accounting.json) | [YAML](https://raw.githubusercontent.com/codatio/oas/main/yaml/Codat-Accounting.yaml)
| [Banking API](https://docs.codat.io/banking-api#/) | Access standardized banking data from our banking integrations.  | [JSON](https://raw.githubusercontent.com/codatio/oas/main/json/Codat-Banking.json) | [YAML](https://raw.githubusercontent.com/codatio/oas/main/yaml/Codat-Banking.yaml)
| [Commerce API](https://docs.codat.io/commerce-api#/) | Access standardized commerce data from our commerce integrations.  | [JSON](https://raw.githubusercontent.com/codatio/oas/main/json/Codat-Commerce.json) | [YAML](https://raw.githubusercontent.com/codatio/oas/main/yaml/Codat-Commerce.yaml)
| [Bank Feeds API](https://docs.codat.io/bank-feeds-api#/) | Set up bank feeds from accounts in your application to supported accounting platforms.  | [JSON](https://raw.githubusercontent.com/codatio/oas/main/json/Codat-Bank-Feeds.json) | [YAML](https://raw.githubusercontent.com/codatio/oas/main/yaml/Codat-Bank-Feeds.yaml)
| [Assess API](https://docs.codat.io/assess-api#/) | Make credit decisions backed by enhanced financials, metrics, reports, and data integrity features.  | [JSON](https://raw.githubusercontent.com/codatio/oas/main/json/Codat-Assess.json) | [YAML](https://raw.githubusercontent.com/codatio/oas/main/yaml/Codat-Assess.yaml)
| [Sync for Expenses API](https://docs.codat.io/sync-for-expenses-api#/) | Push merchants' data from your ecommerce or point-of-sale (POS) platform into your merchants' accounting platform.  | [JSON](https://raw.githubusercontent.com/codatio/oas/main/json/Codat-Expenses.json) | [YAML](https://raw.githubusercontent.com/codatio/oas/main/yaml/Codat-Expenses.yaml)
| [Sync for Commerce API](https://docs.codat.io/sync-for-commerce-api#/) | Push expenses to accounting platforms.  | [JSON](https://raw.githubusercontent.com/codatio/oas/main/json/Codat-Sync-Commerce.json) | [YAML](https://raw.githubusercontent.com/codatio/oas/main/yaml/Codat-Sync-Commerce.yaml)
| [Files API](https://docs.codat.io/files-api#/) | Capture your SMB's business documents with our file upload functionality.  | [JSON](https://raw.githubusercontent.com/codatio/oas/main/json/Codat-Files.json) | [YAML](https://raw.githubusercontent.com/codatio/oas/main/yaml/Codat-Files.yaml)

### Client library SDKs

- [TypeScript](https://github.com/codatio/client-sdk-typescript)
- [Python](https://github.com/codatio/client-sdk-python)
- [Go](https://github.com/codatio/client-sdk-go)
- COMING SOON! [C#](https://github.com/codatio/client-sdk-csharp)

[Read more about our SDKs](https://docs.codat.io/introduction/libraries)

<!-- No SDK Installation -->
<!-- No SDK Example Usage -->
<!-- No SDK Available Operations -->


<!-- Start Error Handling -->
## Error Handling

Handling errors in this SDK should largely match your expectations.  All operations return a response object or an error, they will never return both.  When specified by the OpenAPI spec document, the SDK will return the appropriate subclass.

| Error Object       | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| sdkerrors.SDKError | 400-600            | */*                |

### Example

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

		var e *sdkerrors.SDKError
		if errors.As(err, &e) {
			// handle error
			log.Fatal(e.Error())
		}
	}
}

```

<!-- End Error Handling -->



<!-- Start Server Selection -->
## Server Selection

### Select Server by Index

You can override the default server globally using the `WithServerIndex` option when initializing the SDK client instance. The selected server will then be used as the default on the operations that use it. This table lists the indexes associated with the available servers:

| # | Server | Variables |
| - | ------ | --------- |
| 0 | `http://petstore.swagger.io/v1` | None |

#### Example

```go
package main

import (
	"context"
	codatoas "github.com/anuraagnalluri/codat-oas"
	"log"
)

func main() {
	s := codatoas.New(
		codatoas.WithServerIndex(0),
	)

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


### Override Server URL Per-Client

The default server can also be overridden globally using the `WithServerURL` option when initializing the SDK client instance. For example:
```go
package main

import (
	"context"
	codatoas "github.com/anuraagnalluri/codat-oas"
	"log"
)

func main() {
	s := codatoas.New(
		codatoas.WithServerURL("http://petstore.swagger.io/v1"),
	)

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
<!-- End Server Selection -->



<!-- Start Custom HTTP Client -->
## Custom HTTP Client

The Go SDK makes API calls that wrap an internal HTTP client. The requirements for the HTTP client are very simple. It must match this interface:

```go
type HTTPClient interface {
	Do(req *http.Request) (*http.Response, error)
}
```

The built-in `net/http` client satisfies this interface and a default client based on the built-in is provided by default. To replace this default with a client of your own, you can implement this interface yourself or provide your own client configured as desired. Here's a simple example, which adds a client with a 30 second timeout.

```go
import (
	"net/http"
	"time"
	"github.com/myorg/your-go-sdk"
)

var (
	httpClient = &http.Client{Timeout: 30 * time.Second}
	sdkClient  = sdk.New(sdk.WithClient(httpClient))
)
```

This can be a convenient way to configure timeouts, cookies, proxies, custom headers, and other low-level configuration.
<!-- End Custom HTTP Client -->



<!-- Start Go Types -->

<!-- End Go Types -->

<!-- Placeholder for Future Speakeasy SDK Sections -->


