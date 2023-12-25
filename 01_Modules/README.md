# Hello World

First Golan Project that prints a "Hello World!!" using standard output.

1. Create a folder to place greetings module source code.
    ```bash
    $ mkdir greetings
    $ cd greetings
    ```
2. Enable dependency tracking using the go mod init command. \
    ```bash
    $ go mod init example.com/greetings
    go: creating new go.mod: example.com/greetings
    ```
3. Create *greetings.go* (I use VS Code) \
   <details><summary>greetings.go</summary>
   
    ```go
    package greetings

    import "fmt"

    // Hello returns a greeting for the named person.
    func Hello(name string) string {
        // Return a greeting that embeds the name in a message.
        message := fmt.Sprintf("Hi, %v. Welcome!", name)
        return message
    }
    ```
   </details>

4. Create hello directory and main file *hello.go* in the project folder
    ```bash
    $ cd ..
    $ mkdir hello
    $ cd hello
    ```
    
    Project folder structure should look as follows:
    ```bash 
    <home>/
    |-- greetings/
    |-- hello/
    ```
5. Enable dependency tracking for hello module
    ```bash
    $ go mod init example.com/hello`
    go: creating new go.mod: module example.com/hello
    ```

6. Create hello.go file and add the following code.
    <details><summary>hello.go</summary>
    
    ```go
    package main

    import (
        "fmt"

        "example.com/greetings"
    )

    func main() {
        // Get a greeting message and print it.
        message := greetings.Hello("Gladys")
        fmt.Println(message)
    }
    ```
    </details>
    </br>

7. Adapt module to find greetings
    `$ go mod edit -replace example.com/greetings=../greetings`

8. Synchronize module's dependencies

    ```bash
    $ go mod tidy`
    go: found example.com/greetings in example.com/greetings v0.0.0-00010101000000-000000000000
    ```

9. Run the program \
   ```bash
   $ go run .
   Hi, Gladys. Welcome!
   ```
