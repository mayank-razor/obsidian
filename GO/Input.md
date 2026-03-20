```reader := bufio.NewReader(os.Stdin)

fmt.Println("enter the rating for our pizza")

input, _ := reader.ReadString('\n')

fmt.Println("thanks for rating, ",input)
```

file , ok syntax is used here

