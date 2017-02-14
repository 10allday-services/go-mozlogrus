# mozlogrus [![GoDoc](https://godoc.org/go.mozilla.org/mozlogrus?status.svg)](https://godoc.org/go.mozilla.org/mozlogrus)
A logging library which conforms to Mozilla's logging standard for [logrus](https://github.com/Sirupsen/logrus).

## Example Usage
```go
package main

import (
	log "github.com/Sirupsen/logrus"
	"go.mozilla.org/mozlogrus"
)

func init() {
	mozlogrus.Enable("ApplicationName")
}

func main() {
	log.WithFields(log.Fields{
		"animal": "walrus",
		"size":   10,
	}).Info("A group of walrus emerges from the ocean")
}
```

```json
$ go run mozlogrus.go | jq
{
  "Timestamp": 1487083306055612200,
  "Type": "app.log",
  "Logger": "ApplicationName",
  "Hostname": "gator3",
  "EnvVersion": "2.0",
  "Pid": 27544,
  "Severity": 4,
  "Fields": {
    "animal": "walrus",
    "msg": "A group of walrus emerges from the ocean",
    "size": 10
  }
}
```
