---
title: 1030 - StartFaultWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1601fb9-0bc6-4dbe-816f-f24914063d34
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 436a0323fcf4498a1d707f7af9bd8204885fd645
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="1030---startfaultworkitem"></a>1030 - StartFaultWorkItem
## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|ID|1030|  
|Mots clés|WFRuntime|  
|Niveau|Verbose|  
|Canal|Microsoft-Windows-Application Server-Applications/Débogage|  
  
## <a name="description"></a>Description  
 Indique qu'un FaultWorkItem démarre l'exécution.  
  
## <a name="message"></a>Message  
 Début de l’exécution d’un FaultWorkItem pour l’activité '%1', DisplayName : '%2', InstanceId : '%3'.  L'exception a été propagée à partir de l'activité « %4 », DisplayName : « %5 », InstanceId : « %6 ».  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|FaultActivity|xs:string|Nom de type de l'activité d'erreur.|  
|FaultActivityDisplayName|xs:string|Nom complet de l'activité d'erreur.|  
|FaultActivityInstanceId|xs:string|ID d'instance de l'activité d'erreur.|  
|ExceptionActivity|xs:string|Nom de type de l'activité qui a levé l'exception.|  
|ExceptionActivityDisplayName|xs:string|Nom complet de l'activité qui a levé l'exception.|  
|ExceptionActivityInstanceId|xs:string|ID d'instance de l'activité ayant levé l'exception.|  
|Exception|xs:string|Détails de l'exception|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
