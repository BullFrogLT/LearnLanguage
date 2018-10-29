```go
package main

import (
	"fmt"
	"strconv"
	"strings"
)

var (
	s1 = "abc123"
	s2 = "123"
)

func StringDemo1 (){
	// 字符串定义
	var sd1 = "abc"
	fmt.Println(sd1)
	fmt.Println(s1)
	fmt.Println(s2)

	var s4 string = "bcd"
	fmt.Println(s4)
}

func StringDemo2 (){
	// 判断字符串是否包含某个内容，全量匹配
	// func Contains(s, substr string) bool
	fmt.Println(strings.Contains(s1, "bc1"))		//Output:ture
	fmt.Println(strings.Contains(s1, "abc2"))		//Output:false


	// 字符串链接，把slice a通过sep链接起来
	// func Contains(s, substr string) bool
	s := []string {"foo", "bar", "baz"}
	fmt.Println(strings.Join(s, ","))
	//Output:foo,bar,baz

	// func Index(s, sep string) int
	// 在字符串s中查找sep所在的位置，返回位置值，找不到返回-1
	fmt.Println(strings.Index("chicken", "ken"))
	fmt.Println(strings.Index("chicken", "dmr"))
	//Output:4
	//-1

	// strings.LastIndex(s, str string) int
	// 在字符串s中从后往前查找sep所在的位置，返回位置值，找不到返回-1
	fmt.Println(strings.Index("chicken", "c"))
	fmt.Println(strings.LastIndex("chicken", "c"))
	//Output:0
	//3

	// func Repeat(s string, count int) string
	// 重复s字符串count次，最后返回重复的字符串
	fmt.Println("ba" + strings.Repeat("na", 2))
	//Output: banana

	// func Replace(s, old, new string, n int) string
	// 在s字符串中，把old字符串替换为new字符串，n表示替换的次数，小于0表示全部替换
	fmt.Println(strings.Replace("oink oink oink", "k", "ky", 2))
	fmt.Println(strings.Replace("oink oink oink", "oink", "moo", -1))
	//Output:oinky oinky oink
	//moo moo moo

	// func Split(s, sep string) []string
	// 把s字符串按照sep分割，返回slice
	fmt.Printf("%q\n", strings.Split("a,b,c", ","))
	fmt.Printf("%q\n", strings.Split("a man a plan a canal panama", "a "))
	fmt.Printf("%q\n", strings.Split(" xyz ", ""))
	fmt.Printf("%q\n", strings.Split("", "Bernardo O'Higgins"))
	//Output:["a" "b" "c"]
	//["" "man " "plan " "canal panama"]
	//[" " "x" "y" "z" " "]
	//[""]

	// strings.Fields(s)
	// 将会利用 1 个或多个空白符号来作为动态长度的分隔符将字符串分割成若干小块，并返回一个 slice，如果字符串只包含空白符号，则返回一个长度为 0 的 slice
	fmt.Printf("%q\n", strings.Fields("Hello, This is a test!"))
	//Output:["Hello," "This" "is" "a" "test!"]

	tablename := "NB_TAB_IM"
	tableslice := strings.Split(tablename, "_")
	fmt.Printf("%s\n", tableslice)
	//Output: [NB TAB IM]

	// func Trim(s string, cutset string) string
	// 在字符串s的头部和尾部去除指定的字符串cutset
	fmt.Printf("[%q]\n", strings.Trim(" !!! Achtung !!! ", "! "))
	//Output:["Achtung"]

	// strings.TrimSpace(s)
	// 在字符串s的头部和尾部去除空格
	fmt.Printf("[%s]\n", strings.TrimSpace(" !!! Achtung !!! "))
	//Output:[!!! Achtung !!!]

	// strings.TrimLeft(s)
	// 在字符串s的头部去除字符串
	fmt.Printf("[%s]\n", strings.TrimLeft(" !!! Achtung !!! ", " !"))
	//Output:[Achtung !!! ]

	// strings.TrimRight(s)
	// 在字符串s的尾部去除字符串
	fmt.Printf("[%s]\n", strings.TrimRight(" !!! Achtung !!! ", " !"))
	//Output:[ !!! Achtung]

	// func Fields(s string) []string
	// 去除s字符串的空格符，并且按照空格分割返回slice
	fmt.Printf("Fields are: %q\n", strings.Fields("  foo bar  baz   "))
	//Output:Fields are: ["foo" "bar" "baz"]

	// strings.Count(s, str string) int
	// Count 用于计算字符串 str 在字符串 s 中出现的非重叠次数
	fmt.Printf("%d\n", strings.Count("abc123abc", "a"))
	//Output:2

	// strings.ToLower(s) string
	// 将字符串修改为小写
	fmt.Printf("%s\n", strings.ToLower("abcABC"))
	//Output:abcabc

	// string.ToUpper(s) string
	// 将字符串修改为大写
	fmt.Printf("%s\n", strings.ToUpper("abcABC"))
	//Output:ABCABC
}


func StringDemo3(){
	// Append 系列函数将整数等转换为字符串后，添加到现有的字节数组中
	s5 := make([]byte , 0, 100)
	s5 = strconv.AppendInt(s5, 4567, 10)
	s5 = strconv.AppendBool(s5, false)
	s5 = strconv.AppendQuote(s5, "abcdefg")
	s5 = strconv.AppendQuoteRune(s5, '单')
	fmt.Println(string(s5))
	//Output:4567false"abcdefg"'单'

	// Format 系列函数把其他类型的转换为字符串
	a := strconv.FormatBool(false)
	b := strconv.FormatFloat(123.23, 'g', 12, 64)
	c := strconv.FormatInt(1234, 10)
	d := strconv.FormatUint(12345, 10)
	e := strconv.Itoa(1023)
	fmt.Println(a, b, c, d, e)
	//Output:false 123.23 1234 12345 1023
}

func StringDemo4(){
	// strings.HasPrefix(s, prefix string) bool
	// HasPrefix 判断字符串 s 是否以 prefix 开头
	s6 := "This is an example of a string"
	fmt.Printf("T/F? Does the string \"%s\" have prefix %s? \n", s6, "Th")
	fmt.Printf("%t\n", strings.HasPrefix(s6, "Th"))
	fmt.Printf("%t\n", strings.HasPrefix(s6, "TH"))
	//Output:T/F? Does the string "This is an example of a string" have prefix Th?
	//true
	//false

	// strings.HasSuffix(s, suffix string) bool
	// HasSuffix 判断字符串 s 是否以 suffix 结尾：
	fmt.Printf("%t\n", strings.HasSuffix(s6, "string"))
	fmt.Printf("%t\n", strings.HasSuffix(s6, "a"))
	//true
	//false

}

func main() {
	// 字符串操作实例
	//StringDemo1()
	//StringDemo2()
	//StringDemo3()
	StringDemo4()
}
```



