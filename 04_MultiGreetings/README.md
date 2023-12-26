# Multi Greetings

This project is an update of previous project 03_RandomGreeting, it will add use of :
- Function with multiple parameters
- Maps

1. Copy 03_RandomGreeting to a new folder.
    ```bash    
    Golang/$ cp -r 03_RandomGreeting/ 04_MultiGreetings/
    Golang/$ cd 04_MultiGreetings
    Golang/04_MultiGreetings/$
    ```
2. Add *Hellos* function code to *greetings.go*.
   <details><summary>greetings.go</summary>

    ```go
    // Hellos returns a map that associates each of the named people
    // with a greeting message.
    func Hellos(names []string) (map[string]string, error) {
        // A map to associate names with messages.
        messages := make(map[string]string)
        // Loop through the received slice of names, calling
        // the Hello function to get a message for each name.
        for _, name := range names {
            message, err := Hello(name)
            if err != nil {
                return nil, err
            }
            // In the map, associate the retrieved message with
            // the name.
            messages[name] = message
        }
        return messages, nil
    }
    ```
   </details>
   </br>

4. Update *hello.go* to use pass a slice of names when invoking *Hellos* : \
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

        // A slice of names.
        names := []string{"Gladys", "Samantha", "Darrin"}

        // Request greeting messages for the names.
        messages, err := greetings.Hellos(names)
        if err != nil {
            log.Fatal(err)
        }
        // If no error was returned, print the returned map of
        // messages to the console.
        fmt.Println(messages)
    }
    ```

5. Run the program several times to confirm randomized behaviour \
   ```bash
    Golang/hello$ go run .
    Hail, Fernando! Well met!
    Great to see you, Fernando!
    Hail, Fernando! Well met!
   ```
