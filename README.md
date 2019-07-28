# LearnHTMLAgilityPack
Scrape websites using HTML Agility Pack C#

// How to Get elements by class in Html Agility Pack C# 

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
