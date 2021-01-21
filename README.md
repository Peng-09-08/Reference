# Reference
* Markdown語法介紹
https://ithelp.ithome.com.tw/articles/10203758

## Get Tab key from Winform
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

## Get/Replace string between two characters
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

## Get key of Dictionary by value
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

## Find index of items in array
https://stackoverflow.com/a/13291849<br>
`Ex:`
```C#
string[] str = new string[] { "AA", "BB", "CC", "DD", "EE", "FF" };
var temp = str.Select((v, i) => new { Index = i, Value = v }).Where(x => x.Value == "CC")
    .Select(x => x.Index).ToList(); //temp[0] = 2
```

## Initialize and Compare array
```C#
//Initialize
int[] a = Array.CreateInstance(typeof(int), 5);
```
https://dotblogs.com.tw/rainmaker/2012/02/02/67456<br>
`Ex:`
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

## Drag and Drop files
```C#
public partial class Form1 : Form 
{
    public Form1() 
    {
	InitializeComponent();
	this.AllowDrop = true;
        this.DragEnter += new DragEventHandler(Form1_DragEnter);
        this.DragDrop += new DragEventHandler(Form1_DragDrop);
    }

    private void Form1_DragEnter(object sender, DragEventArgs e) 
    {
	if (e.Data.GetDataPresent(DataFormats.FileDrop)) 
	    e.Effect = DragDropEffects.Copy;
    }

    private void Form1_DragDrop(object sender, DragEventArgs e) 
    {
	string[] files = (string[])e.Data.GetData(DataFormats.FileDrop);
	//...
    }
  }
```

## @符號用法
https://dotblogs.com.tw/yypass2002/2013/08/13/114354<br>
`Ex:`
```C#
//1. 限定字串
string fileName = @"D:\Temp\Test.txt"; //D:\\Temp\\Test.txt

//2. 字串跨行
string test = @"ABC
 DEF
 GHI
 J";

//3. 將關鍵字作為識別字
string @case = "123";
```

## Set focus to form
https://stackoverflow.com/a/7358286<br>
`Ex:`
```C#
[DllImport("user32.dll")]
static extern bool SetForegroundWindow(IntPtr hWnd);

private void SetFocusToForm()
{
    //Set focus to CheckEEProm.exe after dragging file
    Process currentProcess = Process.GetCurrentProcess();
    IntPtr hWnd = currentProcess.MainWindowHandle;
    if (hWnd != IntPtr.Zero)
        SetForegroundWindow(hWnd);
}

private void textBox_DragDrop(object sender, DragEventArgs e)
{
    //拖曳檔案到textBox後，讓焦點回到form上
    //...
    SetFocusToForm();
}
```

## Button with 3D border
https://stackoverflow.com/a/37485355

## 使用建置前事件命令列執行批次檔(執行檔)
https://dotblogs.com.tw/killysss/2014/11/27/147445

