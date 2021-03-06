---
title: "Comment : implémenter une opération de service asynchrone"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3ba82242d0d3d42d4a2e3774186f2a282e279938
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-implement-an-asynchronous-service-operation"></a>Comment : implémenter une opération de service asynchrone
Dans les applications [!INCLUDE[indigo1](../../../includes/indigo1-md.md)], une opération de service peut être implémentée de façon asynchrone ou synchrone sans dicter au client comment l'appeler. Par exemple, les opérations de service asynchrones peuvent être appelées de façon synchrone, et inversement. Pour obtenir un exemple qui montre comment appeler une opération de façon asynchrone dans une application cliente, consultez [Comment : appeler les opérations de Service asynchrone](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md). [!INCLUDE[crabout](../../../includes/crabout-md.md)]opérations synchrones et asynchrones, consultez [concevoir des contrats de Service](../../../docs/framework/wcf/designing-service-contracts.md) et [synchrone et asynchrone des opérations](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md). Cette rubrique décrit la structure de base d'une opération de service asynchrone, le code n'est pas complet. Pour obtenir un exemple complet de côtés le service et le client, consultez [asynchrone](http://msdn.microsoft.com/library/833db946-f511-4f64-a26f-2759a11217c7).  
  
### <a name="implement-a-service-operation-asynchronously"></a>Implémenter une opération de service de façon asynchrone  
  
1.  Dans votre contrat de service, déclarez une paire de méthodes asynchrones conformément aux règles de design asynchrone .NET. La méthode `Begin` prend un paramètre, un objet de rappel et un objet d'état, puis retourne <xref:System.IAsyncResult?displayProperty=nameWithType> et une méthode `End` correspondante qui prend <xref:System.IAsyncResult?displayProperty=nameWithType> et retourne la valeur de retour. Pour plus d’informations sur les appels asynchrones, consultez [Asynchronous Programming Design Patterns](http://go.microsoft.com/fwlink/?LinkId=248221).  
  
2.  Marquez la méthode `Begin` de la paire de méthodes asynchrones avec l'attribut <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> et affectez <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> à la propriété `true`. Par exemple, le code suivant exécute les étapes 1 et 2.  
  
     [!code-csharp[C_SyncAsyncClient#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#6)]
     [!code-vb[C_SyncAsyncClient#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#6)]  
  
3.  Implémentez la paire de méthodes `Begin/End` dans votre classe de service conformément aux règles de design asynchrone. Par exemple, l'exemple de code suivant présente une implémentation dans laquelle une chaîne est écrite dans la console, à la fois dans les parties `Begin` et `End` de l'opération de service asynchrone, et la valeur de retour de l'opération `End` est retournée au client. Pour obtenir un exemple de code complet, consultez la section Exemple.  
  
     [!code-csharp[C_SyncAsyncClient#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#3)]
     [!code-vb[C_SyncAsyncClient#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#3)]  
  
## <a name="example"></a>Exemple  
 Les exemples de code suivants présentent :  
  
1.  Une interface de contrat de service avec :  
  
    1.  Une opération `SampleMethod` synchrone.  
  
    2.  Une opération `BeginSampleMethod` asynchrone.  
  
    3.  Asynchrone `BeginServiceAsyncMethod` / `EndServiceAsyncMethod` paire d’opérations.  
  
2.  Une implémentation de service utilisant un objet <xref:System.IAsyncResult?displayProperty=nameWithType>.  
  
 [!code-csharp[C_SyncAsyncClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#1)]
 [!code-vb[C_SyncAsyncClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#1)]  
  
## <a name="see-also"></a>Voir aussi  
 [Conception de contrats de service](../../../docs/framework/wcf/designing-service-contracts.md)  
 [Opérations synchrones et asynchrones](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)
