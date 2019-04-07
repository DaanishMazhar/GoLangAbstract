# GoLangAbstract
This GoLangAbstract package makes extraction summaries from text simple and easy!
This algorithm measures relations within sentences (measuring relevant token similarity), length and position to pick out highlights of the text.

### Abstracts
```bash
export MODELS="<postagging trained models folder path>"

go get github.com/lucasmenendez/gobstact
```

### Run the program!
```go
package main

import (
    "fmt"
    "io/ioutil"
    "github.com/lucasmenendez/gobstract"
)

func main() {
    var input string
    if raw, err := ioutil.ReadFile("input"); err != nil {
        fmt.Println(err)
        return
    } else {
        input = string(raw)
    }

    if t, err := gobstract.NewText(input, "es"); err != nil {
        fmt.Println(err)
    } else {
        var summary []string = t.Summarize()
        for _, sentence := range summary {
            fmt.Println(sentence)
        }
    }    
}
```