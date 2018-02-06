<p align="center">
  <img src="https://github.com/RN0311/Go-Tutorial/blob/master/img/wwglogo.png" width="400" height="300">
</p>

## Installation 
The **Go** programming language is an open source project which is expressive, concise, clean, and efficient. It is popular for many applications, at many companies, and has a robust set of tools 
and over 90,000 repos.<br >
This tutorial will walk you through downloading and installation of Go 1.8 as well as building a simple ``` Hello world ``` program.
Here is an example of how all Go code is organized under ``` GOPATH```:
```

$GOPATH
├── bin
├── pkg
└── src
    ├── github.com
    │   └── tools
    │       └── godep    
    ├── google.golang.org
    │   └── cloud
    │       └── bigtable
    ├── gopkg.in
    │   └── tomb.v2
    └── launchpad.net
        └── gozk
            └── zookeeper

```
So, you will need to set ``` GOPATH ``` to a directory of your choosing:
```
$ mkdir $HOME/gopath
$ export GOPATH=$HOME/gopath
```
When working with Go tools, sometimes executables will be installed to your workspace's bin directory. 
To make it easier to work with these installed tools, add the workspace's bin subdirectory to your PATH:
``` $ export PATH=$PATH:$GOPATH/bin ```
Now you can install Go.

## Step 1 - Installing Go
To ensure that you have the latest security patches and fixes, in your Ubuntu machines, run the below commands.
```
sudo apt-get update
sudo apt-get -y upgrade
```
Now, download latest package for Go by running command <br >
``` sudo curl -O https://storage.googleapis.com/golang/go1.8.linux-amd64.tar.gz ``` <br >
Further, unpack the package using ``` tar ```. And create a folder using the package name, and then move it to ``` /usr/local ```.
```
sudo tar -xvf go1.8.linux-amd64.tar.gz
sudo mv go /usr/local
```
The Go package is now in ``` /usr/local ``` which also ensures Go is in your ``` $PATH ``` for Linux.

## Step 2 - Configuring the Go paths
The paths in above step are all given are relative to the location of your Go installation in ``` /usr/local ```. 
But if you chose a new directory, or have the file in downloaded location, modify the above commands to match your new location.

First, set Go’s root value, which tells Go where to look for its files.
``` 
sudo nano ~/.profile 
```
At the end of the file,add this line:<br >
``` 
export PATH=$PATH:/usr/local/go/bin
```
If you chose an alternate installation location for Go, then add below lines instead to the same file and save & close it.<br >
``` 
export GOROOT=$HOME/go
export PATH=$PATH:$GOROOT/bin
```
## Step 3 - Testing your Go installation
* A simple test would be to test the version of Go i.e. ``` go version ```


* Create a new directory for your Go workspace something like below : <br >
``` mkdir $HOME/test_case ```
and you can now, point Go to the new workspace by exporting ``` GOPATH ```.
```
export GOPATH=$HOME/test_case
```
* Next, you can create a simple **hello_world.go** file.
```
nano test_case/hello_world.go
```
* Below is the code snippet of Hello World program in Go.
```Go
package main
import "fmt"
func main() {
    fmt.Printf("Hello, World\n")
}
```
* To run the above snippet in development mode use ``` $ go run hello_world.go ```.

* To build programs into binaries use ``` go build ``` and then execute binary directly.
``` Go
$ go build hello_world.go 
$ ./hello_world
```
