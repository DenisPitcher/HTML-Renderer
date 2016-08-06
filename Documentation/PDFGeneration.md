**Generate PDF**

IN order to get started, add the following snippet in your main method:

```
class Program
{
    private static void Main(string[] args)
    {
        string html = "<p><h1>Hello World</h1>This is html rendered text</p>";
        PdfDocument pdf = PdfGenerator.GeneratePdf(html, PageSize.A4);
        pdf.Save("document.pdf");
    }
}
```

**Applying CSS**

Adjust your HTML to include a class definition to customize html within your text.

```
string html = "<p><h1>Hello World</h1>This is html rendered text <span class='blue'>with css styling in blue</span></p>";
```

Add a new css definition
```
string css = ".blue { color: blue; }  ";
```

Adjust your GeneratePdf parameters to include style sheet parsing and a margin setting matching the default of 20
```
PdfDocument pdf = PdfGenerator.GeneratePdf(html, PageSize.A4, 20, PdfGenerator.ParseStyleSheet(css));
```

Your code should now look like this
```
class Program
{
    private static void Main(string[] args)
    {
        string html = "<p><h1>Hello World</h1>This is html rendered text <span class='blue'>with css styling in blue</span></p>";
        string css = ".blue { color: blue; }";
        PdfDocument pdf = PdfGenerator.GeneratePdf(html, PageSize.A4, 20, PdfGenerator.ParseStyleSheet(css));
        pdf.Save("document.pdf");
    }
}
```

If you run this code you should now see your sample with some styled text