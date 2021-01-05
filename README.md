# Reference
* Markdown語法介紹
https://ithelp.ithome.com.tw/articles/10203758

## 1. Get Tab key from Winform
https://dotblogs.com.tw/rainmaker/2013/07/17/111261<br>
`Ex:`
```C#
protected override bool ProcessCmdKey(ref Message msg, Keys keyData)
{
	Keys keyPressed = (Keys)msg.WParam.ToInt32();
	switch (keyPressed)
	{
		case Keys.Tab:
			//...
			return true;
		default:
			return base.ProcessCmdKey(ref msg, keyData);
	}
}
```

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

## 4. Find index of items in array
https://stackoverflow.com/a/13291849<br>
`Ex:`
```C#
string[] str = new string[] { "AA", "BB", "CC", "DD", "EE", "FF" };
var temp = str.Select((v, i) => new { Index = i, Value = v }).Where(x => x.Value == "CC")
    .Select(x => x.Index).ToList(); //temp[0] = 2
```

## 5. Initialize and Compare array
`Ex:`
```C#
//Initialize
int[] a = Array.CreateInstance(typeof(int), 5);
```
https://dotblogs.com.tw/rainmaker/2012/02/02/67456<br>

```C#
//Compare by SequenceEqual
string[] array1 = new string[] { "Data", "Account", "credit", "Debit" }; 
string[] array2 = new string[] { "Data1", "Account1", "credit", "Debit" }; 
string[] array3 = new string[] { "Account", "credit", "Debit", "Data"};
string[] array4 = new string[] { "Data", "Account", "credit", "Debit" }; 
bool isarray12thesame = array1.SequenceEqual(array2); //false
bool isarray13thesame = array1.SequenceEqual(array3); //false
bool isarray14thesame = array1.SequenceEqual(array4); //true
```
