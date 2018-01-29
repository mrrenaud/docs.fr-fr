---
title: "Guide pratique pour analyser des chaînes à l’aide de String.Split (Guide C#)"
description: "String.Split retourne un tableau de chaînes fractionnées à partir d’un ensemble de délimiteurs. Il s’agit d’un moyen simple pour analyser des chaînes."
ms.date: 01/03/2018
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
author: BillWagner
ms.author: wiwagn
ms.custom: mvc
ms.openlocfilehash: fc1032f2cdf6706ec933323643dbf6ecff3e9f6f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-parse-strings-using-stringsplit-c-guide"></a><span data-ttu-id="32b76-104">Guide pratique pour analyser des chaînes à l’aide de String.Split (Guide C#)</span><span class="sxs-lookup"><span data-stu-id="32b76-104">How to: Parse Strings Using String.Split (C# Guide)</span></span>

<span data-ttu-id="32b76-105">La méthode <xref:System.String.Split%2A?displayProperty=nameWithType> crée un tableau de sous-chaînes en fractionnant la chaîne d’entrée en fonction d’un ou plusieurs délimiteurs.</span><span class="sxs-lookup"><span data-stu-id="32b76-105">The <xref:System.String.Split%2A?displayProperty=nameWithType> method creates an array of substrings by splitting the input string based on one or more delimiters.</span></span> <span data-ttu-id="32b76-106">C’est souvent le moyen le plus simple pour séparer une chaîne sur des limites de mots.</span><span class="sxs-lookup"><span data-stu-id="32b76-106">It is often the easiest way to separate a string on word boundaries.</span></span> <span data-ttu-id="32b76-107">Elle sert également à fractionner des chaînes sur d’autres caractères ou chaînes spécifiques.</span><span class="sxs-lookup"><span data-stu-id="32b76-107">It is also used to split strings on other specific characters or strings.</span></span>

<span data-ttu-id="32b76-108">Le code suivant fractionne une expression commune en un tableau de chaînes pour chaque mot.</span><span class="sxs-lookup"><span data-stu-id="32b76-108">The following code splits a common phrase into an array of strings for each word.</span></span>
<span data-ttu-id="32b76-109">Essayez par vous-même en appuyant sur le bouton *Run*.</span><span class="sxs-lookup"><span data-stu-id="32b76-109">Try it yourself by pressing the *Run* button.</span></span>

[!code-csharp-interactive[split strings on word boundaries](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#1)]

<span data-ttu-id="32b76-110">Chaque instance d’un caractère de séparation génère une valeur dans le tableau retourné.</span><span class="sxs-lookup"><span data-stu-id="32b76-110">Every instance of a separator character produces a value in the returned array.</span></span> <span data-ttu-id="32b76-111">Les caractères de séparation consécutifs produisent une chaîne vide comme valeur dans le tableau retourné.</span><span class="sxs-lookup"><span data-stu-id="32b76-111">Consecutive separator characters produce the empty string as a value in the returned array.</span></span>  <span data-ttu-id="32b76-112">Vous pouvez l’observer dans l’exemple suivant, qui utilise l’espace comme séparateur :</span><span class="sxs-lookup"><span data-stu-id="32b76-112">You can see this in the following example, which uses space as a separator:</span></span>

[!code-csharp-interactive[split strings with repeated separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#2)]

<span data-ttu-id="32b76-113">Ce comportement facilite l’utilisation de formats tels que les fichiers CSV (valeurs séparées par des virgules) représentant des données tabulaires.</span><span class="sxs-lookup"><span data-stu-id="32b76-113">This behavior makes it easier for formats like comma separated values (CSV) files representing tabular data.</span></span> <span data-ttu-id="32b76-114">Les virgules consécutives représentent une colonne vide.</span><span class="sxs-lookup"><span data-stu-id="32b76-114">Consecutive commas represent a blank column.</span></span>

<span data-ttu-id="32b76-115">Vous pouvez passer un paramètre <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=fullName> facultatif pour exclure toutes les chaînes vides dans le tableau retourné.</span><span class="sxs-lookup"><span data-stu-id="32b76-115">You can pass an optional <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=fullName> parameter to exclude any empty strings in the returned array.</span></span> <span data-ttu-id="32b76-116">Pour un traitement plus complexe de la collection retournée, vous pouvez utiliser [LINQ](../programming-guide/concepts/linq/index.md) pour manipuler la séquence de résultat.</span><span class="sxs-lookup"><span data-stu-id="32b76-116">For more complicated processing of the returned collection, you can use [LINQ](../programming-guide/concepts/linq/index.md) to manipulate the result sequence.</span></span>    

<span data-ttu-id="32b76-117"><xref:System.String.Split%2A?displayProperty=nameWithType> peut utiliser plusieurs caractères de séparation.</span><span class="sxs-lookup"><span data-stu-id="32b76-117"><xref:System.String.Split%2A?displayProperty=nameWithType> can use multiple separator characters.</span></span> <span data-ttu-id="32b76-118">L’exemple suivant utilise des caractères de séparation (espaces, virgules, points, deux-points et onglets) qui sont tous passés dans un tableau à <xref:System.String.Split%2A>.</span><span class="sxs-lookup"><span data-stu-id="32b76-118">The following example uses spaces, commas, periods, colons, and tabs, all passed in an array containing these separating characters, to <xref:System.String.Split%2A>.</span></span>  <span data-ttu-id="32b76-119">La boucle en bas du code affiche chacun des mots dans le tableau retourné.</span><span class="sxs-lookup"><span data-stu-id="32b76-119">The loop at the bottom of the code displays each of the words in the returned array.</span></span>  

[!code-csharp-interactive[split strings using multiple separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#3)]

<span data-ttu-id="32b76-120">Les instances consécutives d’un séparateur produisent une chaîne vide dans le tableau de sortie :</span><span class="sxs-lookup"><span data-stu-id="32b76-120">Consecutive instances of any separator produce the empty string in the output array:</span></span>

[!code-csharp-interactive[split strings using multiple consecutive separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#4)]

<span data-ttu-id="32b76-121"><xref:System.String.Split%2A?displayProperty=nameWithType> peut accepter un tableau de chaînes (séquences de caractères, à la place de caractères uniques, qui agissent comme séparateurs lors de l’analyse de la chaîne cible).</span><span class="sxs-lookup"><span data-stu-id="32b76-121"><xref:System.String.Split%2A?displayProperty=nameWithType> can take an array of strings (character sequences that act as separators for parsing the target string, instead of single characters).</span></span>  
  
[!code-csharp-interactive[split strings using strings as separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#5)]

<span data-ttu-id="32b76-122">Vous pouvez essayer ces exemples en examinant le code dans notre [dépôt GitHub](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings).</span><span class="sxs-lookup"><span data-stu-id="32b76-122">You can try these samples by looking at the code in our [GitHub repository](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings)</span></span>

## <a name="see-also"></a><span data-ttu-id="32b76-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="32b76-123">See Also</span></span>  
 [<span data-ttu-id="32b76-124">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="32b76-124">C# Programming Guide</span></span>](../programming-guide/index.md)  
 [<span data-ttu-id="32b76-125">Chaînes</span><span class="sxs-lookup"><span data-stu-id="32b76-125">Strings</span></span>](../programming-guide/strings/index.md)  
 [<span data-ttu-id="32b76-126">.NET Framework (expressions régulières)</span><span class="sxs-lookup"><span data-stu-id="32b76-126">.NET Framework Regular Expressions</span></span>](https://msdn.microsoft.com/library/hs600312)