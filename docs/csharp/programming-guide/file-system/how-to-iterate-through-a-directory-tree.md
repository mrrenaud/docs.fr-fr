---
title: "Guide pratique pour itérer au sein d’une arborescence de répertoires (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- iterating through folders [C#]
- file iteration [C#]
ms.assetid: c4be4a75-6b1b-46a7-9d38-bab353091ed7
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7f45bdc4a08922842b079be3ef9d112693ca5d7a
ms.sourcegitcommit: 75a180acb5d8a2dbd4a52915ce8e980749fb1d05
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2018
---
# <a name="how-to-iterate-through-a-directory-tree-c-programming-guide"></a>Guide pratique pour itérer au sein d’une arborescence de répertoires (Guide de programmation C#)
L’expression « itérer au sein d’une arborescence de répertoires » signifie accéder à chaque fichier dans chaque sous-répertoire imbriqué sous un dossier racine spécifié, à n’importe quelle profondeur. Vous ne devez pas nécessairement ouvrir chaque fichier. Vous pouvez simplement récupérer le nom du fichier ou du sous-répertoire sous forme de `string`, ou vous pouvez récupérer des informations supplémentaires sous la forme d’un objet <xref:System.IO.FileInfo?displayProperty=nameWithType> ou <xref:System.IO.DirectoryInfo?displayProperty=nameWithType>.  
  
> [!NOTE]
>  Dans Windows, les termes « répertoire » et « dossier » sont utilisés indifféremment. La plus grande partie de la documentation et du texte d’interface utilisateur utilise le terme « dossier », mais la bibliothèque de classes [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] utilise le terme « répertoire ».  
  
 Dans le cas le plus simple, où vous êtes sûr de disposer des autorisations d’accès à tous les répertoires situés sous une racine spécifiée, vous pouvez utiliser l’indicateur `System.IO.SearchOption.AllDirectories`. Cet indicateur retourne tous les sous-répertoires imbriqués qui correspondent au modèle spécifié. L’exemple suivant montre comment utiliser cet indicateur.  
  
```csharp  
root.GetDirectories("*.*", System.IO.SearchOption.AllDirectories);  
```  
  
 La faiblesse de cette approche est que si l’un des sous-répertoires sous la racine spécifiée provoque une exception <xref:System.IO.DirectoryNotFoundException> ou <xref:System.UnauthorizedAccessException>, la totalité de la méthode échoue et ne retourne pas de répertoire. Il en va de même quand vous utilisez la méthode <xref:System.IO.DirectoryInfo.GetFiles%2A>. Si vous devez gérer ces exceptions dans des sous-dossiers spécifiques, vous devez parcourir manuellement l’arborescence de répertoires, comme illustré dans les exemples suivants.  
  
 Quand vous parcourez manuellement une arborescence de répertoires, vous pouvez gérer d’abord les sous-répertoires (*balayage pré-ordre*), ou d’abord les fichiers (*balayage post-ordre*). Si vous effectuez un balayage pré-ordre, vous parcourez l’arborescence entière sous le dossier actif avant d’itérer au sein des fichiers qui sont directement dans le dossier lui-même. Les exemples fournis plus loin dans ce document effectuent un balayage post-ordre, mais vous pouvez les modifier facilement pour effectuer un balayage pré-ordre.  
  
 Une autre option consiste à utiliser la récurrence ou un balayage de pile. Les exemples fournis plus loin dans ce document illustrent les deux approches.  
  
 Si vous devez effectuer diverses opérations sur des fichiers et des dossiers, vous pouvez modulariser ces exemples en refactorisant l’opération dans des fonctions distinctes que vous pouvez appeler à l’aide d’un délégué unique.  
  
> [!NOTE]
>  Les systèmes de fichiers NTFS peuvent contenir des *points d’analyse* sous la forme de *points de jonction*, de *liens symboliques* et de *liens physiques*. Les méthodes .NET Framework telles que <xref:System.IO.DirectoryInfo.GetFiles%2A> et <xref:System.IO.DirectoryInfo.GetDirectories%2A> ne retournent pas de sous-répertoires situés sous un point d’analyse. Ce comportement vous protège contre le risque d’entrer dans une boucle infinie quand deux points d’analyse se référencent l’un l’autre. En général, lors de l’utilisation de points d’analyse vous devez faire attention à ne pas involontairement modifier ou supprimer des fichiers. Si vous avez besoin d’un contrôle précis sur les points d’analyse, utilisez du code natif ou un appel de code non managé pour appeler directement les méthodes de système de fichiers Win32 appropriées.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment parcourir une arborescence de répertoires à l’aide de la récurrence. L’approche récursive est élégante, mais susceptible de provoquer une exception de dépassement de capacité de la pile si l’arborescence de répertoires est volumineuse et profondément imbriquée.  
  
 Les exceptions particulières gérées et les actions qui sont effectuées sur chaque fichier ou dossier sont fournies à titre d’exemple uniquement. Vous devez modifier ce code pour répondre à vos besoins spécifiques. Pour plus d’informations, consultez les commentaires du code.  
  
 [!code-csharp[csFilesandFolders#1](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-iterate-through-a-directory-tree_1.cs)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment itérer au sein des fichiers et des dossiers dans une arborescence de répertoires sans utiliser la récurrence. Cette technique utilise le type de collection <xref:System.Collections.Generic.Stack%601> générique, qui est une pile LIFO (dernier entré, premier sorti).  
  
 Les exceptions particulières gérées et les actions qui sont effectuées sur chaque fichier ou dossier sont fournies à titre d’exemple uniquement. Vous devez modifier ce code pour répondre à vos besoins spécifiques. Pour plus d’informations, consultez les commentaires du code.  
  
 [!code-csharp[csFilesandFolders#2](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-iterate-through-a-directory-tree_2.cs)]  
  
 Cela prend généralement trop de temps de tester chaque dossier pour déterminer si votre application est autorisée à l’ouvrir. Par conséquent, l’exemple de code englobe simplement cette partie de l’opération dans un bloc `try/catch`. Vous pouvez modifier le bloc `catch` pour que, quand l’accès à un dossier vous est refusé, vous essayiez d’élever vos autorisations et d’y accéder à nouveau. En règle générale, vous devez intercepter uniquement les exceptions que vous pouvez gérer sans laisser votre application dans un état inconnu.  
  
 Si vous devez stocker le contenu d’une arborescence de répertoires en mémoire ou sur disque, la meilleure option consiste à stocker uniquement la propriété <xref:System.IO.FileSystemInfo.FullName%2A> (de type `string`) pour chaque fichier. Vous pouvez ensuite utiliser cette chaîne pour créer un objet <xref:System.IO.FileInfo> ou <xref:System.IO.DirectoryInfo>, si nécessaire, ou ouvrir les fichiers qui nécessitent un traitement supplémentaire.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Tout code d’itération de fichiers fiable doit tenir compte de nombreuses complexités du système de fichiers. Pour plus d’informations sur le système de fichiers Windows, consultez [Référence technique sur NTFS](https://technet.microsoft.com/library/81cc8a8a-bd32-4786-a849-03245d68d8e4).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IO>  
 [LINQ et répertoires de fichiers](../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)  
 [Système de fichiers et Registre (Guide de programmation C#)](../../../csharp/programming-guide/file-system/index.md)
