---
title: "Gérer des exceptions dans des expressions de requête"
description: "Comment gérer des exceptions dans des expressions de requête."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 2bf0c397-13fb-4f68-bc2b-531c6c88a167
ms.openlocfilehash: 376bd461bfeb51653471fd374a2215aa15872976
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="handle-exceptions-in-query-expressions"></a>Gérer des exceptions dans des expressions de requête

Dans le contexte d’une expression de requête, vous pouvez utiliser n’importe quelle méthode. Toutefois, nous vous recommandons d’éviter d’appeler une méthode dans une expression de requête susceptible de créer un effet secondaire, tel que la modification du contenu de la source de données ou la levée d’une exception. Cet exemple montre comment éviter la levée d’exceptions lorsque vous appelez des méthodes dans une expression de requête, en respectant les directives générales du .NET Framework relatives à la gestion des exceptions. Selon ces directives, il est acceptable d’intercepter une exception si vous comprenez pourquoi elle est levée dans un contexte donné. Pour plus d’informations, consultez les [Bonnes pratiques pour les exceptions](../../standard/exceptions/best-practices-for-exceptions.md).  
  
 Le dernier exemple montre comment gérer les cas où vous devez lever une exception pendant l’exécution d’une requête.  
  
## <a name="example"></a>Exemple  

 L’exemple suivant montre comment déplacer du code de gestion des exceptions en dehors d’une expression de requête. Ceci est possible uniquement lorsque la méthode ne dépend pas des variables locales de la requête.  
  
 [!code-csharp[csProgGuideLINQ#10](../../../samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_1.cs)]  
  
## <a name="example"></a>Exemple 

 Dans certains cas, la meilleure réponse à la levée d’une exception à l’intérieur d’une requête consiste à arrêter immédiatement l’exécution de la requête. L’exemple suivant montre comment gérer les exceptions pouvant être levées dans le corps d’une requête. Supposons que `SomeMethodThatMightThrow` puisse provoquer la levée d’une exception qui nécessite l’arrêt de l’exécution de la requête.  
  
 Notez que le bloc `try` englobe la boucle `foreach` et non la requête. Ceci s’explique par le fait que c’est au niveau de la boucle `foreach` que la requête est exécutée. Pour plus d’informations, consultez [Introduction aux requêtes LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 [!code-csharp[csProgGuideLINQ#12](../../../samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_2.cs)]  
  

## <a name="see-also"></a>Voir aussi  
 [Expressions de requête LINQ](index.md)
