---
title: "Refactorisation à l’aide d’une méthode d’extension (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: c5fc123d-af10-4a2f-b8e4-db921efb2639
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 52972d1fbc951a379b4ce754a47143a15c672cfb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="refactoring-using-an-extension-method-c"></a>Refactorisation à l’aide d’une méthode d’extension (C#)
Cet exemple se base sur l’exemple précédent, [Récupération du texte des paragraphes (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), en refactorisant la concaténation de chaînes à l’aide d’une fonction pure implémentée en tant que méthode d’extension.  
  
 L'exemple précédent utilisait l'opérateur de requête standard <xref:System.Linq.Enumerable.Aggregate%2A> pour concaténer plusieurs chaînes dans une chaîne. Toutefois, il est plus commode d'écrire une méthode d'extension pour cela, car la requête résultante est plus petite et plus simple.  
  
## <a name="example"></a>Exemple  
 Cet exemple traite un document WordprocessingML, récupère les paragraphes, le style de chaque paragraphe et le texte de chaque paragraphe. Cet exemple se base sur les exemples précédents de ce didacticiel.  
  
 L'exemple contient plusieurs surcharges de la méthode `StringConcatenate`.  
  
 Vous trouverez des instructions pour créer le document source utilisé dans cet exemple dans [Création du document Office Open XML source (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
 Cet exemple utilise des classes de l'assembly WindowsBase. Il utilise des types dans l'espace de noms <xref:System.IO.Packaging?displayProperty=nameWithType>.  
  
```csharp  
public static class LocalExtensions  
{  
    public static string StringConcatenate(this IEnumerable<string> source)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item));  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate(this IEnumerable<string> source, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s).Append(separator);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item)).Append(separator);  
        return sb.ToString();  
    }  
}  
```  
  
## <a name="example"></a>Exemple  
 Il existe quatre surcharges de la méthode `StringConcatenate`. Une surcharge prend simplement une collection de chaînes et retourne une seule chaîne. Une autre surcharge prend une collection d'un type quelconque et un délégué qui projette depuis un singleton de la collection vers une chaîne. Il existe deux surcharges supplémentaires qui vous permettent de spécifier une chaîne de séparation.  
  
 Le code suivant utilise les quatre surcharges.  
  
```csharp  
string[] numbers = { "one", "two", "three" };  
  
Console.WriteLine("{0}", numbers.StringConcatenate());  
Console.WriteLine("{0}", numbers.StringConcatenate(":"));  
  
int[] intNumbers = { 1, 2, 3 };  
Console.WriteLine("{0}", intNumbers.StringConcatenate(i => i.ToString()));  
Console.WriteLine("{0}", intNumbers.StringConcatenate(i => i.ToString(), ":"));  
```  
  
 Cet exemple génère la sortie suivante :  
  
```  
onetwothree  
one:two:three:  
123  
1:2:3:  
```  
  
## <a name="example"></a>Exemple  
 À présent, l’exemple peut être modifié pour tirer parti de la nouvelle méthode d’extension :  
  
```csharp  
public static class LocalExtensions  
{  
    public static string StringConcatenate(this IEnumerable<string> source)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item));  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate(this IEnumerable<string> source, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s).Append(separator);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item)).Append(separator);  
        return sb.ToString();  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        const string fileName = "SampleDoc.docx";  
  
        const string documentRelationshipType =  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
        const string stylesRelationshipType =  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";  
        const string wordmlNamespace =  
          "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
        XNamespace w = wordmlNamespace;  
  
        XDocument xDoc = null;  
        XDocument styleDoc = null;  
  
        using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.Read))  
        {  
            PackageRelationship docPackageRelationship =  
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();  
            if (docPackageRelationship != null)  
            {  
                Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative),  
                  docPackageRelationship.TargetUri);  
                PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
                //  Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
  
                //  Find the styles part. There will only be one.  
                PackageRelationship styleRelation =  
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();  
                if (styleRelation != null)  
                {  
                    Uri styleUri =  
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);  
                    PackagePart stylePart = wdPackage.GetPart(styleUri);  
  
                    //  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
                }  
            }  
        }  
  
        string defaultStyle =  
            (string)(  
                from style in styleDoc.Root.Elements(w + "style")  
                where (string)style.Attribute(w + "type") == "paragraph" &&  
                      (string)style.Attribute(w + "default") == "1"  
                select style  
            ).First().Attribute(w + "styleId");  
  
        // Find all paragraphs in the document.  
        var paragraphs =  
            from para in xDoc  
                         .Root  
                         .Element(w + "body")  
                         .Descendants(w + "p")  
            let styleNode = para  
                            .Elements(w + "pPr")  
                            .Elements(w + "pStyle")  
                            .FirstOrDefault()  
            select new  
            {  
                ParagraphNode = para,  
                StyleName = styleNode != null ?  
                    (string)styleNode.Attribute(w + "val") :  
                    defaultStyle  
            };  
  
        // Retrieve the text of each paragraph.  
        var paraWithText =  
            from para in paragraphs  
            select new  
            {  
                ParagraphNode = para.ParagraphNode,  
                StyleName = para.StyleName,  
                Text = para  
                       .ParagraphNode  
                       .Elements(w + "r")  
                       .Elements(w + "t")  
                       .StringConcatenate(e => (string)e)  
            };  
  
        foreach (var p in paraWithText)  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);  
    }  
}  
```  
  
 Quand il est appliqué au document décrit dans [Création du document Office Open XML source (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md), cet exemple produit la sortie suivante.  
  
```  
StyleName:Heading1 >Parsing WordprocessingML with LINQ to XML<  
StyleName:Normal ><  
StyleName:Normal >The following example prints to the console.<  
StyleName:Normal ><  
StyleName:Code >using System;<  
StyleName:Code ><  
StyleName:Code >class Program {<  
StyleName:Code >    public static void (string[] args) {<  
StyleName:Code >        Console.WriteLine("Hello World");<  
StyleName:Code >    }<  
StyleName:Code >}<  
StyleName:Normal ><  
StyleName:Normal >This example produces the following output:<  
StyleName:Normal ><  
StyleName:Code >Hello World<  
```  
  
 Notez que cette refactorisation est une variante de la refactorisation dans une fonction pure. La rubrique suivante présente le concept de factorisation dans des fonctions pures de manière plus détaillée.  
  
## <a name="next-steps"></a>Étapes suivantes  
 L'exemple suivant montre comment refactoriser ce code d'une autre manière, à l'aide de fonctions pures :  
  
-   [Refactorisation à l’aide d’une fonction pure (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/refactoring-using-a-pure-function.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel : Manipulation de contenu dans un document WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)  
 [Refactorisation dans des fonctions pures (C#)](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md)
