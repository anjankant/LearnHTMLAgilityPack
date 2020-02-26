# Learn HTML Agility Pack Step by step --> Web Scraping using C# 
## Scrape websites using HTML Agility Pack C#
## :v: Chapter 1: What is HTML Agility Pack? :cowboy_hat_face:	
After the preamble, now exactly what is **HTML agility pack** :heart_eyes: and why it is used? Many times, it becomes a requirement to read or what is technically called as parse an HTML document where the source could be a file, or a string or another web source. Thus, what is **HTML agility pack c#** is that it is one of the .NET libraries that gives the C# developer :kissing: to read and write the DOM (Document Object Model) and has explicit support for **plain XPath** or **XSLT** and the bonus is :relaxed:, you don't even have to know about these terminologies? The library is so forgiving that it won't trouble much with its functionality even if the source of HTML is malformed in standards. Thus, it's the best choice to rely on this library instead of writing up the parsing code all by yourself.</br>
</br>
[Subscribe YouTube Channel] (http://bit.ly/2lSE3r6)

## Let's Kick off with HTML Agility Pack :yum:
### :v:	Chapter 2: Learn to Install HTML agility pack and Load an HTML Document
- First, you can install nuget package from the [link](https://nuget.org/packages/HtmlAgilityPack).
- Under the section, **Package Manager** copy the install code. For example, if there is content such as >>> **PM> Install-Package HtmlAgilityPack -Version x.x.x**, then you shall copy the text that follows after PM>.
- After copying the code, now go to your **Visual Studio Application** and click on **Tools menu** in the menu bar.
- From the menu drop down, go to **library manager** → **Package Manager Console**.
- In the lower half of the Application, now you will see the Package Manager Console opened and the cursor blinking.
- You must paste the code that you copied from the site using the help of step:2 by using the combination of hotkeys Ctrl and V :relaxed: .
- After pasting the code hit enter and the application will take care of the installation :smiley:.

#### :point_right: Coding Snippet

```
HtmlWeb web = new HtmlWeb();
HtmlAgilityPack.HtmlDocument doc = new HtmlAgilityPack.HtmlDocument(); 
doc = web.load(“https://technologycrowds.com”);
```

### :v:	Chapter 3: How to Get elements by class in Html Agility Pack C# 

HtmlAgility is a very great tool as we have seen how it can be used to traverse the entire HTML content of webpages in C#, it can also be understood that the HTML content can be manipulated with much ease.

#### :point_right: Coding Snippet

```
using System;
using HtmlAgilityPack;
using System.Collections.Generic;
using System.Linq;

public class Program
{
	public static void Main()
	{
		// declaring & loading dom
		HtmlWeb web = new HtmlWeb();
		HtmlAgilityPack.HtmlDocument doc = new HtmlAgilityPack.HtmlDocument();
		doc = web.Load("https://en.wikipedia.org/wiki/Main_Page");
		
		// filter html elements on the basis of class name
		IEnumerable<HtmlNode> nodes = doc.DocumentNode.Descendants().Where(n => n.HasClass("mw-jump-link"));
		
		foreach(var item in nodes)
		{
			// displaying final output
			Console.WriteLine(item.InnerText);	
		}
	}
}
```

### :v:	Chapter 4: Extract Meta-Information from the website using HTML agility pack

#### Namespace

```
using System.Collections.Generic; using System.Linq;
using System.Text;
using System.Threading.Tasks; using HtmlAgilityPack;
```

#### Load HTML document using HTML Agility Pack

```
HtmlWeb web = new HtmlWeb();
HtmlAgilityPack.HtmlDocument doc = new HtmlAgilityPack.HtmlDocument();
doc = web.Load("http://technologyCrowds.com");
GetMetaInformation(doc, "description");
```

#### :point_right: Creating Methods to Extract Meta Information

```
static void GetMetaInformation(HtmlAgilityPack.HtmlDocument htmldoc, string value)
{
 HtmlNode tcNode = htmldoc.DocumentNode.SelectSingleNode("//meta[@name='" + value + "']");
 string fulldescription = string.Empty;
 if (tcNode != null)
 {
  HtmlAttribute desc;
  desc = tcNode.Attributes["content"];
  Console.ForegroundColor = ConsoleColor.Red;
  Console.Write(desc.Value);
  Console.ReadLine();
 }
}
```
### :v: Chapter 5: Select Nodes using Html Agility Pack
#### SelectNodes()

#### :point_right: Coding Snippet

```
var html = @"
var html = @"<TD>
</TD>
<TD>
<INPUT value=Technology>
<INPUT value=Crowds>
</TD>
var htmlDoc = new HtmlDocument();
htmlDoc.LoadHtml(html);
var node = htmlDoc.DocumentNode.SelectNodes("//td/input");

foreach (var node in nodes)
{
  Console.WriteLine(node.Attributes["value"].Value);
}
```
### Output

- Technology
- Crowds

#### SelectSingleNode(String)
SelectSingleNode is a type of function that takes in an XPath expression and produces a result that contains the first HtmlAgilityPack.HtmlNode. 
The return value could also be null if there are no matching nodes.

#### :point_right: Coding Snippet

```
var html = @"
var html = @"<TD>
</TD>
<TD>
<INPUT value=Technology>
<INPUT value=Crowds>
</TD>
var htmlDoc = new HtmlDocument();
htmlDoc.LoadHtml(html);
var node = htmlDoc.DocumentNode.SelectNodes("//td/input").First()
          .Attributes["value"].Value;
Console.WriteLine(node);
``

### Output
- Technology

[Free Video Library: Learn HTML Agility Pack Step by Step](https://www.youtube.com/playlist?list=PLJufu9snJTv4tHfmsR-6QA4SPYj5vmp87)
