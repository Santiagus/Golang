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

### Download and modify the golang.org/x/example/hello module

1. Clone the repository from the workspace directory
    ```bash
    07_MultiModuleProject$ git clone https://go.googlesource.com/example
    Cloning into 'example'...
    remote: Total 165 (delta 27), reused 165 (delta 27)
    Receiving objects: 100% (165/165), 434.18 KiB | 1022.00 KiB/s, done.
    Resolving deltas: 100% (27/27), done.
    Add the module to the workspace
    ```
2. Add module to the workspace:
    ```bash
    07_MultiModuleProject$ go work use ./example/hello
    ```
3. Check *go.work* file content
    ```bash
    go 1.21.5
    use (
            ./example/hello
            ./hello
    )
    ```

4. Create a new file named *int.go* in the *workspace/example/hello/reverse* 
    <details><summary>07_MultiModuleProject/example/hello/reverse</summary>

    ```go
    package reverse

    import "strconv"

    // Int returns the decimal reversal of the integer i.
    func Int(i int) int {
        i, _ = strconv.Atoi(String(strconv.Itoa(i)))
        return i
    }
    ```
    </details>

5. Modify the hello program to use the function.
    ```go
    package main

    import (
        "fmt"
        "golang.org/x/example/hello/reverse"
    )

    func main() {
        fmt.Println(reverse.String("Hello"), reverse.Int(24601))
    }
    ```

6. Run the code in the workspace
    ```bash
    $ go run ./hello
    olleH 10642
    ```

The Go command finds the *example.com/hello* module specified in the command line in the hello directory specified by the go.work file

go.work can be used instead of adding replace directives to work across multiple modules.

Since the two modules are in the same workspace it’s easy to make a change in one module and use it in another.