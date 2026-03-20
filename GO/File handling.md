

* to create a file
```go
file,err := os.Create("./fileName.txt")
```
* to add content into it
```go
length,err := io.WriteString(file,content)
```
to read a file

```go
ioutil.ReadFile(file)
```
anything coming from api call is in form of bytes