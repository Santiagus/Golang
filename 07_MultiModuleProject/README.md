# Multimodule project

1. Create a folder for the project
```bash
$ mkdir 07_MultiModuleProject
$ cd 07_MultiModuleProject
```
2. Create *hello* module
    ```bash
    $ mkdir hello
    $ cd hello
    $ go mod init example.com/hello
    go: creating new go.mod: module example.com/hello
    ```
3. Add dependency on golang.org/x/example/hello/reverse
    ```bash
    $ go get golang.org/x/example/hello/reverse`
    go: downloading golang.org/x/example v0.0.0-20231013143937-1d6d2400d402
    go: downloading golang.org/x/example/hello v0.0.0-20231013143937-1d6d2400d402
    go: added golang.org/x/example/hello v0.0.0-20231013143937-1d6d2400d402
    ```

4. Create *hello.go* in hello directory
    <details><summary>hello.go</summary>

    ```go
    package main

    import (
        "fmt"
        "golang.org/x/example/hello/reverse"
    )

    func main() {
        fmt.Println(reverse.String("Hello"))
    }
    ```
    </details>

5. Run the hello program:
    ```bash
    $ go run .
    olleH
    ```
