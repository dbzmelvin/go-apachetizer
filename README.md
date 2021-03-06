# go-apachetizer
Simple and lightweight Apache2 Config Detector and Parser

<a href="https://goreportcard.com/report/github.com/dbzmelvin/go-apachetizer"><img src="https://goreportcard.com/badge/github.com/dbzmelvin/go-apachetizer"></a>

## Used external Dependencies
* none

## Docs
**All code examples are not handling any errors please keep that in mind**

##### VHostConfDetector(cfgPath string)
This function will detect all configs save it into a <br>[]string array and returns the []string
```go
package main

import(
	"github.com/dbzmelvin/go-apachetizer"
	"fmt"
	)

func main(){
	list, _ :=  apachetizer.VHostConfDetector("./etc/apache2/sites-available")
	fmt.Printf("This is your list: %s", list)
}
```

##### VHostConfParser(file io.Reader)
This function will parse the given config file, you have to pass an io.Reader
```go
package main

import(
	"github.com/dbzmelvin/go-apachetizer"
	"fmt"
	"os"
	"encoding/json"
	)

func main(){
    Reader, _ := os.Open("./etc/apache2/testconfig-le-ssl.conf") //io.Reader
    config, _ := apachetizer.VHostConfParser(Reader) //Parse the config
    jsonEncoded, _ := json.Marshal(config) //Encode the []string array to json []byte array
    fmt.Println(string(jsonEncoded)) //Print the []byte array as string
}
```

## License
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
