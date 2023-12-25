# Hello World

First Golan Project that prints a "Hello World!!" using standard output.

1. Start your module using the go mod init command. \
    ```bash
    $ go mod init helloworld
    go: creating new go.mod: module helloworld
    ```
2. Create *helloworld.go* (I use VS Code) \
   `code helloworld.go` 

   **NOTE:** VS Code will ask to install [gopls](https://pkg.go.dev/golang.org/x/tools/gopls) if not installed.

   <details><summary>helloworld.go</summary>
   
    ```go
    package main

    import "fmt"

    func main() {
        fmt.Println("Hello World!!!")
    }
    ```
   </details>

3. Run the program \
   ```bash
   $ go run helloworld.go
   Hello World!!!
   ```
