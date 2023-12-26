# Error Handling

This project is an update of previous project 01_Modules, adding Error Handling.

1. Copy 01_Modules to a new folder.
    ```bash
    Golang/$ mkdir 02_ErrorHandling
    Golang/$ cp -r 01_Modules/* 02_ErrorHanling/
    Golang/$ cd 02_ErrorHanling
    Golang/02_ErrorHanling/$
    ```
2. Enable dependency tracking using the go mod init command. \
    ```bash
    $ go mod init example.com/greetings
    go: creating new go.mod: example.com/greetings
    ```
3. Add following code to *greetings.go*
   <details><summary>greetings.go</summary>

    ```go
    import (
        "errors"
        "fmt"
    )
    func Hello(name string) (string, error) {
        // If no name was given, return an error with a message.
        if name == "" {
            return "", errors.New("empty name")
        }
        ...
        return message, nil
    }
    ```
   </details>

4. Add following code to *hello.go*
   <details><summary>hello.go</summary>

   ```go
    package main

    import (
        "fmt"
        "log"

        "example.com/greetings"
    )

    func main() {
        // Set properties of the predefined Logger, including
        // the log entry prefix and a flag to disable printing
        // the time, source file, and line number.
        log.SetPrefix("greetings: ")
        log.SetFlags(0)

        // Request a greeting message.
        message, err := greetings.Hello("")
        // If an error was returned, print it to the console and
        // exit the program.
        if err != nil {
            log.Fatal(err)
        }

        // If no error was returned, print the returned message
        // to the console.
        fmt.Println(message)
    }
    ```
   </details>

4. Run the program to confirm error handling \
   ```bash
    Golang/hello$ go run .
    greetings: empty name
    exit status 1
   ```

Program output an error message as expected.

5. Run the program with non empty argument \
    Replace : \
        `message, err := greetings.Hello("")` \
    for  : \
        `message, err := greetings.Hello("Fernando")` \

    Output: \
        `Hi, Fernando. Welcome!`

