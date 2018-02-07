## Build a simple WebServer in Go using net/http package!
First create a file web_server.go and paste the below snippet:
```Go
package main

import "net/http"

func main(){
	http.HandleFunc("/",hello)
	http.ListenAndServe(":8080",nil)
}

func hello(w http.ResponseWriter, r *http.Request){
	w.Write([]byte("hello,Rashmi!"))
}
```
Now, build above program using commands :
```
$ go build web_server.go
$ ./web_server
```
In another terminal run this command :
``` 
curl http://localhost:8080
```
**yay!** You've completed building first webserver in Go! **Time to roll for more!** :smile:

## Fetch data from OpenWeatherMap API using Go
```Go
package main

import (
    "encoding/json"
    "net/http"
    "strings"
)

func main() {
    http.HandleFunc("/hello", hello)

    http.HandleFunc("/weather/", func(w http.ResponseWriter, r *http.Request) {
        city := strings.SplitN(r.URL.Path, "/", 3)[2]

        data, err := query(city)
        if err != nil {
            http.Error(w, err.Error(), http.StatusInternalServerError)
            return
        }

        w.Header().Set("Content-Type", "application/json; charset=utf-8")
        json.NewEncoder(w).Encode(data)
    })

    http.ListenAndServe(":8080", nil)
}

func hello(w http.ResponseWriter, r *http.Request) {
    w.Write([]byte("hello!"))
}

func query(city string) (weatherData, error) {
    resp, err := http.Get("http://api.openweathermap.org/data/2.5/weather?APPID=ADD-YOUR-API=" + city)
    if err != nil {
        return weatherData{}, err
    }

    defer resp.Body.Close()

    var d weatherData

    if err := json.NewDecoder(resp.Body).Decode(&d); err != nil {
        return weatherData{}, err
    }

    return d, nil
}

type weatherData struct {
    Name string `json:"name"`
    Main struct {
        Kelvin float64 `json:"temp"`
    } `json:"main"`
}
```
Now, build and run it.
```
$ go build web.go
$ ./web
$ curl http://localhost:8080/weather/delhi
```

**NB**:The OpenWeatherMap provides a simple and free API for current forecast info. 
Register for a free account to get an API key. 
