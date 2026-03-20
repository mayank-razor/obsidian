```go
highscore := make([]int ,4)
```

### how to add val
```go
highscore = append(highscore,values) 
```

### how to remove val
```go
var courses = []string{"react","js","swift","python","golang"}

var index int = 2

courses = append(courses[:index],courses[index+1:]...)
```
