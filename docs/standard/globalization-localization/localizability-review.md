---
title: "Révision de l'adaptabilité"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- world-ready applications, localizability
- application development [.NET Framework], localization
- localizability [.NET Framework]
- international applications [.NET Framework], localizability
- globalization [.NET Framework], localizability
- culture, localizability
- localization [.NET Framework], localizability
- global applications, localizability
- localizing resources
ms.assetid: 3aee2fbb-de47-4e37-8fe4-ddebb9719247
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2aaf7c466c6662611e2b37d5c967a99d050158df
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="localizability-review"></a>Révision de l'adaptabilité
La revue de l’adaptabilité est une étape intermédiaire du développement d’une application mondialisable. Il vérifie qu'une application globalisée est prête pour la localisation et identifie tout code ou tous les aspects de l'interface utilisateur qui nécessitent une gestion spéciale. Cette étape permet également de s'assurer que le processus de localisation n'introduira pas de défauts fonctionnels dans votre application. Lorsque tous les problèmes générés par l'examen de l'adaptabilité ont été traités, votre application est prête pour la localisation. Si la revue de l’adaptabilité est complète, vous n’aurez pas à modifier le code source pendant le processus de localisation.  
  
 La revue de l’adaptabilité inclut les trois contrôles suivants :  
  
-   [Les recommandations de globalisation sont-elles implémentées ?](#global)  
  
-   [Les fonctionnalités dépendantes de la culture sont-elles gérées correctement ?](#culture)  
  
-   [Avez-vous testé votre application avec des données internationales ?](#test)  
  
<a name="global"></a>   
## <a name="implementing-globalization-recommendations"></a>Implémentation des recommandations de globalisation  
 Si vous avez conçu et développé votre application en gardant à l'esprit la localisation, et si vous avez suivi les recommandations décrites dans l'article [Globalisation](../../../docs/standard/globalization-localization/globalization.md), l'examen de l'adaptabilité sera largement un gage d'assurance qualité. Autrement, pendant cette étape vous devez examiner et exécuter les recommandations en termes de [globalisation](../../../docs/standard/globalization-localization/globalization.md), et corriger les erreurs dans le code source qui empêchent la localisation.  
  
<a name="culture"></a>   
## <a name="handling-culture-sensitive-features"></a>Gestion des fonctionnalités dépendantes de la culture  
 .NET Framework ne fournit pas de prise en charge de programmation dans plusieurs éléments qui varient considérablement par la culture. Dans la plupart des cas, vous devez écrire un code personnalisé pour gérer les zones de fonctionnalités telles que les suivantes :  
  
-   Adresses.  
  
-   Numéros de téléphone.  
  
-   Formats de papier.  
  
-   Unités de mesure utilisées pour les longueurs, les poids, les aires, les volumes et les températures. Bien que .NET Framework n'offre pas prise en charge intégrée pour convertir les unités de mesure, vous pouvez utiliser la propriété de <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> pour déterminer si un pays ou une région spécifique utilise le système métrique, comme le montre l'exemple suivant.  
  
     [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
     [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]  
  
<a name="test"></a>   
## <a name="testing-your-application"></a>Test de votre application  
 Avant de localiser votre application, vous devriez la tester à l'aide des données internationales dans les versions internationales du système d'exploitation. Bien que la plupart des interfaces utilisateur ne pourront pas être localisées à ce stade, vous serez en mesure de détecter les problèmes tels que :  
  
-   Les données sérialisées qui ne désérialisent pas correctement sur plusieurs versions du système d'exploitation.  
  
-   Les données numériques qui ne reflètent pas les conventions de la culture actuelle. Par exemple, les nombres peuvent s'afficher avec des séparateurs de groupes, des séparateurs décimaux ou des symboles monétaires inexacts.  
  
-   Les données de date et d'heure qui ne reflètent pas les conventions de la culture actuelle. Par exemple, les chiffres qui représentent le mois et le jour peuvent apparaître dans le désordre, les séparateurs de date peuvent être inexacts ou les informations de fuseau horaire peuvent être inexactes.  
  
-   Les ressources introuvables, car vous n'avez pas identifié de culture par défaut pour votre application.  
  
-   Les chaînes affichées dans un ordre inhabituel pour une culture spécifique.  
  
-   Les comparaisons de chaînes ou les comparaisons d'égalité qui retournent des résultats inattendus.  
  
 Si vous avez suivi les recommandations de globalisation lorsque vous développez votre application, traité correctement les fonctionnalités dépendantes de la culture, et que vous avez identifié et traité les problèmes de localisation qui ont surgi pendant le test, vous pouvez passer à l'étape suivante, à savoir la [localisation](../../../docs/standard/globalization-localization/localization.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Globalisation et localisation](../../../docs/standard/globalization-localization/index.md)  
 [Localisation](../../../docs/standard/globalization-localization/localization.md)  
 [Globalisation](../../../docs/standard/globalization-localization/globalization.md)  
 [Ressources dans des applications de bureau](../../../docs/framework/resources/index.md)
