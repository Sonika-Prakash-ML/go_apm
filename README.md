# go_apm

This provides the instrumentation modules for the Go web frameworks.
Currently this supports Goji web framework (https://github.com/zenazn/goji).


**Pre-requisite**

Install the Elastic APM Go Agent with the following command.
```bash
go get go.elastic.co/apm/v2
```


**module/apmgoji**

Package apmgoji provides middleware for the Goji web framework. This middleware traces all the incoming requests and reports each transaction to the APM server.
The apmgoji middleware will also recover panics and send them to Elastic APM.


**Example**

```go
import (
	"github.com/Sonika-dot-Prakash/go_apm/module/apmgoji"
)

func main() {
	goji.Use(goji.DefaultMux.Router)
	goji.Use(apmgoji.Middleware())
	...
}
```