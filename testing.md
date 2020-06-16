### basic testing in golang

https://quii.gitbook.io/learn-go-with-tests/go-fundamentals/hello-world


It needs to be in a file with a name like xxx_test.go

The test function must start with the word Test

The test function takes one argument only t *testing.T

Errorf method on our t which will print out a message if test is failed

t.Run
t.helper()

go test -v