## Config

https://towardsdatascience.com/use-environment-variable-in-your-next-golang-project-39e17c3aaa66

### os Package
os.Setenv(key, value)
value := os.Getenv(key)

```go
// use os package to get the env variable which is already set
func envVariable(key string) string {

  // set env variable using os package
  os.Setenv(key, "gopher")

  // return the env variable using os package
  return os.Getenv(key)
}

func main() {
  // os package
  value := envVariable("name")

  fmt.Printf("os package: %s = %s \n", "name", value)
}
```

### go get github.com/joho/godotenv
godotenv.Load(".env")
STRONGEST_AVENGER=Thor

```go
// use godot package to load/read the .env file and
// return the value of the key
func goDotEnvVariable(key string) string {

  // load .env file
  err := godotenv.Load(".env")

  if err != nil {
    log.Fatalf("Error loading .env file")
  }

  return os.Getenv(key)
}

func main() {
    // os package
    ... 

  // godotenv package
  dotenv := goDotEnvVariable("STRONGEST_AVENGER")

  fmt.Printf("godotenv : %s = %s \n", "STRONGEST_AVENGER", dotenv)
}
```

### go get github.com/spf13/viper

viper.SetConfigFile(".env")
viper.ReadInConfig()
viper.Get(key)


```go
// use viper package to read .env file
// return the value of the key
func viperEnvVariable(key string) string {

  // SetConfigFile explicitly defines the path, name and extension of the config file.
  // Viper will use this and not check any of the config paths.
  // .env - It will search for the .env file in the current directory
  viper.SetConfigFile(".env")

  // Find and read the config file
  err := viper.ReadInConfig()

  if err != nil {
    log.Fatalf("Error while reading config file %s", err)
  }

  // viper.Get() returns an empty interface{}
  // to get the underlying type of the key,
  // we have to do the type assertion, we know the underlying value is string
  // if we type assert to other type it will throw an error
  value, ok := viper.Get(key).(string)

  // If the type is a string then ok will be true
  // ok will make sure the program not break
  if !ok {
    log.Fatalf("Invalid type assertion")
  }

  return value
}

func main() {

    // os package  
    ...
  
  // godotenv package
  ...

  // viper package read .env
  viperenv := viperEnvVariable("STRONGEST_AVENGER")

  fmt.Printf("viper : %s = %s \n", "STRONGEST_AVENGER", viperenv)
}
```