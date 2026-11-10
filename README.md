package main
import "fmt"
func main() {
    var a, b, x, y, gcd, lcm int
    fmt.Print("Enter two numbers: ")
    fmt.Scan(&a, &b)
    x, y = a, b
    for y != 0 {
        x, y = y, x%y
    }
    gcd = x
    lcm = (a * b) / gcd
    fmt.Println("GCD =", gcd)
    fmt.Println("LCM =", lcm)
}

