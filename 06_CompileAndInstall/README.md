## Compile and install the application

- *go build* command compiles the packages, along with their dependencies
- *go install* command compiles and installs the packages.

### Build
For single files: \
`$ go build <file_name>`
```bash
00_HelloWorld$ go build helloworld.go
00_HelloWorld$ ./helloworld
Hello World!!!
```
For modules: \
`$ go build` (In main module folder) \

```bash
05_Testing/hello$ go build
05_Testing/hello$ ./hello
map[Darrin:Hi, Darrin. Welcome! Gladys:Great to see you, Gladys! Samantha:Hail, Samantha! Well met!]
```

*NOTE:* More info `go help build`

### Installation (run it without specifying its path)

- Discover Go install path \
`go list -f '{{.Target}}'`

- Add the Go install directory to your system's shell path.
`$ export PATH=$PATH:/path/to/your/install/directory`

- As an alternative, change the install target by setting the GOBIN variable using the go env command:
`$ go env -w GOBIN=/path/to/your/bin`


