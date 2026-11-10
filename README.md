
==================================================
WEEK 1 – GCD AND LCM
==================================================

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


==================================================
WEEK 2 – NUMBER PYRAMID
==================================================

package main
import "fmt"

func main() {
    n := 5
    num := 1

    for i := 1; i <= n; i++ {
        for j := 1; j <= n-i; j++ {
            fmt.Print(" ")
        }

        for k := 1; k <= i; k++ {
            fmt.Print(num, " ")
            num++
        }

        fmt.Println()
    }
}


==================================================
WEEK 3 – STRUCTURE USING PACKAGE
==================================================

FILE 1: person/person.go

package person
import "fmt"

type Student struct {
    Name string
    Age int
}

func (s Student) Display() {
    fmt.Println("Name:", s.Name)
    fmt.Println("Age:", s.Age)
}


FILE 2: main.go

package main
import "week3/person"

func main() {
    s := person.Student{
        Name: "Lavan",
        Age: 21,
    }

    s.Display()
}

Execution:
go mod init week3
go run .


==================================================
WEEK 4 – STANDARD DEVIATION
==================================================

package main
import (
    "fmt"
    "math"
)

func main() {
    nums := []float64{2, 4, 4, 4, 5, 5, 7, 9}

    mean := 0.0

    for i := 0; i < len(nums); i++ {
        mean += nums[i]
    }

    mean /= float64(len(nums))

    sum := 0.0

    for i := 0; i < len(nums); i++ {
        sum += math.Pow(nums[i]-mean, 2)
    }

    variance := sum / float64(len(nums))
    sd := math.Sqrt(variance)

    fmt.Println("Standard Deviation =", sd)
}


==================================================
WEEK 5 – FLOYD'S TRIANGLE
==================================================

package main
import "fmt"

func main() {
    n := 5
    num := 1

    for i := 1; i <= n; i++ {
        for j := 1; j <= i; j++ {
            fmt.Print(num, " ")
            num++
        }

        fmt.Println()
    }
}


==================================================
WEEK 6 – STRING CONCATENATION
==================================================

package main
import "fmt"

func main() {
    str1 := "Hello"
    str2 := "World"

    result := str1 + " " + str2

    fmt.Println(result)
}


==================================================
WEEK 7 – PALINDROME STRING
==================================================

package main
import "fmt"

func main() {
    str := "madam"
    reverse := ""

    for i := len(str)-1; i >= 0; i-- {
        reverse += string(str[i])
    }

    if str == reverse {
        fmt.Println("Palindrome")
    } else {
        fmt.Println("Not Palindrome")
    }
}


==================================================
WEEK 8 – CONTACT FORM USING HTML TEMPLATE
==================================================

package main
import (
    "html/template"
    "net/http"
)

type Contact struct {
    Name string
    Email string
    Message string
    Success string
}

var tmpl = template.Must(template.New("form").Parse(`
<html>
<body>
    <h2>Contact Form</h2>

    <form method="POST" action="/contact">
        Name: <input name="name"><br><br>
        Email: <input name="email"><br><br>
        Message: <textarea name="message"></textarea><br><br>
        <button type="submit">Submit</button>
    </form>

    <p>{{.Success}}</p>
</body>
</html>
`))

func contactHandler(w http.ResponseWriter, r *http.Request) {
    data := Contact{}

    if r.Method == http.MethodPost {
        r.ParseForm()

        data.Name = r.FormValue("name")
        data.Email = r.FormValue("email")
        data.Message = r.FormValue("message")

        data.Success = "Contact form submitted successfully!"
    }

    tmpl.Execute(w, data)
}

func main() {
    http.HandleFunc("/", contactHandler)
    http.HandleFunc("/contact", contactHandler)

    http.ListenAndServe(":8080", nil)
}

Execution:
go run main.go

Open:
http://localhost:8080


==================================================
WEEK 9 – AVERAGE USING ARRAY
==================================================

package main
import "fmt"

func main() {
    a := [5]int{10, 20, 30, 40, 50}
    sum := 0

    for i := 0; i < len(a); i++ {
        sum += a[i]
    }

    avg := sum / len(a)

    fmt.Println("Average =", avg)
}


==================================================
WEEK 10 – REMOVE DUPLICATES USING MAP
==================================================

package main
import "fmt"

func main() {
    arr := []int{2, 4, 1, 2, 1}

    result := []int{}
    seen := make(map[int]bool)

    for i := 0; i < len(arr); i++ {
        n := arr[i]

        if seen[n] == false {
            result = append(result, n)
            seen[n] = true
        }
    }

    fmt.Println("Result:", result)
}


==================================================
WEEK 11 – REVERSE SORT INTEGERS AND STRINGS
==================================================

package main
import "fmt"

func reverseSortIntegers(arr []int) []int {
    for i := 0; i < len(arr); i++ {
        for j := i+1; j < len(arr); j++ {
            if arr[i] < arr[j] {
                arr[i], arr[j] = arr[j], arr[i]
            }
        }
    }

    return arr
}

func reverseSortStrings(arr []string) []string {
    for i := 0; i < len(arr); i++ {
        for j := i+1; j < len(arr); j++ {
            if arr[i] < arr[j] {
                arr[i], arr[j] = arr[j], arr[i]
            }
        }
    }

    return arr
}

func main() {
    a := []int{1, 2, 3, 4}
    b := []string{"Tan", "Veer", "Rao"}

    fmt.Println(reverseSortIntegers(a))
    fmt.Println(reverseSortStrings(b))
}


==================================================
WEEK 12 – REVERSE SORT INTEGERS USING sort.Reverse()
==================================================

package main
import (
    "fmt"
    "sort"
)

func main() {
    arr := []int{1, 2, 3, 4, 5}

    sort.Sort(sort.Reverse(sort.IntSlice(arr)))

    fmt.Println("Reverse Sorted Array:", arr)
}


==================================================
WEEK 13 – STRING FUNCTIONS
==================================================

package main
import "fmt"

func Contains(str, sub string) bool {
    for i := 0; i+len(sub) <= len(str); i++ {
        if str[i:i+len(sub)] == sub {
            return true
        }
    }

    return false
}

func ContainsAny(str, chars string) bool {
    for i := 0; i < len(chars); i++ {
        for j := 0; j < len(str); j++ {
            if chars[i] == str[j] {
                return true
            }
        }
    }

    return false
}

func Count(str, sub string) int {
    count := 0

    if len(sub) == 0 {
        return 0
    }

    for i := 0; i+len(sub) <= len(str); i++ {
        if str[i:i+len(sub)] == sub {
            count++
            i += len(sub)-1
        }
    }

    return count
}

func EqualFold(a, b string) bool {
    if len(a) != len(b) {
        return false
    }

    for i := 0; i < len(a); i++ {
        x, y := a[i], b[i]

        if x >= 'A' && x <= 'Z' {
            x += 32
        }

        if y >= 'A' && y <= 'Z' {
            y += 32
        }

        if x != y {
            return false
        }
    }

    return true
}

func main() {
    fmt.Println(Contains("Hello World", "World"))
    fmt.Println(ContainsAny("Hello", "xyz"))
    fmt.Println(Count("Hello Hello", "Hello"))
    fmt.Println(EqualFold("GO", "go"))
}
