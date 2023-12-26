# Random Greeting

This project is an update of previous project 02_ErrorHandling, it will add use of :
- Dynamic Array
- Random funcion from math library

1. Copy 02_ErrorHandling to a new folder.
    ```bash
    Golang/$ mkdir 03_RandomGreeting
    Golang/$ cp -r 02_ErrorHandling/* 03_RandomGreeting/
    Golang/$ cd 03_RandomGreeting
    Golang/03_RandomGreeting/$
    ```
2. Add randomFormat() function to *greetings.go* and using his return value as message.
   <details><summary>greetings.go</summary>

    ```go
    package greetings

    import (
        "errors"
        "fmt"
        "math/rand"
    )

    // Hello returns a greeting for the named person.
    func Hello(name string) (string, error) {
        // If no name was given, return an error with a message.
        if name == "" {
            return "", errors.New("empty name")
        }

        // If a name was received, return a value that embeds the name
        // in a greeting message.
        message := fmt.Sprintf(randomFormat(), name)
        return message, nil
    }

    // randomFormat returns one of a set of greeting messages. The returned
    // message is selected at random.
    func randomFormat() string {
        // A slice of message formats.
        formats := []string{
            "Hi, %v. Welcome!",
            "Great to see you, %v!",
            "Hail, %v! Well met!",
        }

        // Return a randomly selected message format by specifying
        // a random index for the slice of formats.
        return formats[rand.Intn(len(formats))]
    }
    ```
   </details>
   </br>

4. Update *hello.go* to use a name in *greetings.Hello("")* : \
   `message, err := greetings.Hello("Fernando")`

5. Run the program several times to confirm randomized behaviour \
   ```bash
    Golang/hello$ go run .
    Hail, Fernando! Well met!
    Great to see you, Fernando!
    Hail, Fernando! Well met!
   ```
