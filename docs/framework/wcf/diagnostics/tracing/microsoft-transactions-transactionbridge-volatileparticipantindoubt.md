---
title: Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e8fc825-9f22-47e7-9c16-d64ef291c932
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0dbfd04ed20a92a2ecf827ef3d6aa4f378eb6a15
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="microsofttransactionstransactionbridgevolatileparticipantindoubt"></a>Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt
Le service du protocole WS-AT a reçu un message Prepared ou Replay d'un participant volatil non reconnu. Une faute a été renvoyée au participant, qui déclarera que le résultat de la transaction est douteux.  
  
## <a name="description"></a>Description  
 Suivi généré lorsque le gestionnaire de transactions local reçoit un message Prepared ou Replay d'une inscription volatile qu'il a déjà oubliée.  
  
## <a name="troubleshooting"></a>Résolution des problèmes  
 Recherchez les causes potentielles de retard des messages qui viennent du participant volatil.  
  
## <a name="see-also"></a>Voir aussi  
 [Suivi](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Utilisation du suivi pour résoudre les problèmes posés par votre application](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administration et diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)
