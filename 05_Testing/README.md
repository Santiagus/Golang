# Testing

This project is an update of previous project 04_MultiGreetings, it will add use of :
- Testing

1. Copy 03_RandomGreeting to a new folder.
    ```bash    
    Golang/$ cp -r 04_MultiGreetings/ 05_Testing/
    Golang/$ cd 05_Testing
    Golang/04_MultiGreetings/$
    ```
2. Add *greetings/greetings_test.go* file
   - *_test* end tells go test cmd the file contains test functions
   - Test functions take a pointer to the testing package's *testing.T type* as a parameter. You use this parameter's methods for reporting and logging from your test.


   <details><summary>greetings_test.go</summary>

    ```go
    package greetings

    import (
        "testing"
        "regexp"
    )

    // TestHelloName calls greetings.Hello with a name, checking
    // for a valid return value.
    func TestHelloName(t *testing.T) {
        name := "Gladys"
        want := regexp.MustCompile(`\b`+name+`\b`)
        msg, err := Hello("Gladys")
        if !want.MatchString(msg) || err != nil {
            t.Fatalf(`Hello("Gladys") = %q, %v, want match for %#q, nil`, msg, err, want)
        }
    }

    // TestHelloEmpty calls greetings.Hello with an empty string,
    // checking for an error.
    func TestHelloEmpty(t *testing.T) {
        msg, err := Hello("")
        if msg != "" || err == nil {
            t.Fatalf(`Hello("") = %q, %v, want "", error`, msg, err)
        }
    }
    ```
   </details>
   </br>

4. Run test in *greetings/* folder:   
    ```bash
    05_Testing/greetings$ go test
    PASS
    ok      example.com/greetings   0.001s
    05_Testing/greetings$ go test -v
    === RUN   TestHelloName
    --- PASS: TestHelloName (0.00s)
    === RUN   TestHelloEmpty
    --- PASS: TestHelloEmpty (0.00s)
    PASS
    ok      example.com/greetings   0.001s
    ```
    
5. Break grettings.Hello function to view a failing test
    ```go    
    // message := fmt.Sprintf(randomFormat(), name)
    message := fmt.Sprint(randomFormat())        
    ```
    Output:
    ```bash
    05_Testing/greetings$ go test
    --- FAIL: TestHelloName (0.00s)
        greetings_test.go:15: Hello("Gladys") = "Hi, %v. Welcome!", <nil>, want match for `\bGladys\b`, nil
    FAIL
    exit status 1
    FAIL    example.com/greetings   0.001s
    ```