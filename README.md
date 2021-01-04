# Reference
* Markdown語法介紹
https://ithelp.ithome.com.tw/articles/10203758

## 1. Get Tab key from Winform
https://dotblogs.com.tw/rainmaker/2013/07/17/111261

## 2. Get/Replace string between two characters
https://stackoverflow.com/questions/20701818/how-to-replace-the-text-between-two-characters-in-c-sharp<br>
https://stackoverflow.com/questions/17252615/get-string-between-two-strings-in-a-string/17252672<br>
`Ex:`
```C#
string source = "[Get string] between two characters";
Regex regex = new Regex(@"\[([^\]]+)\]");

string result = regex.Match(source).Value; //[Get string]
result = result.TrimStart('[').TrimEnd(']'); //Get string

string replace = "Replace string";
//不包含"["和"]"
string result2 = regex.Replace(source, replace); //Replace string between two characters
```

## 3. Get key of Dictionary by value
`Ex:`
```C#
Dictionary<int, int> temp = new Dictionary<int, int>()
{
    { 1, 1 },
    { 2, 22 },
    { 3, 333 },
    { 4, 4444 },
};
int result = temp.FirstOrDefault(x => x.Value == 4444).Key; //result = 4
```

