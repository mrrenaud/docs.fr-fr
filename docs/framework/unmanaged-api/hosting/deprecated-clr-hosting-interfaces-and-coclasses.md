---
title: "Interfaces d’hébergement du CLR et coclasses déconseillées"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 1
- .NET Framework 1.1, hosting interfaces
- hosting interfaces [.NET Framework], version 1
- .NET Framework 1.0, hosting interfaces
ms.assetid: 7b3d2755-cbab-4160-bc69-eb85791e38c7
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4714183eb79a25639dae6824a1d27eb1ca6bb009
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="deprecated-clr-hosting-interfaces-and-coclasses"></a><span data-ttu-id="a95f1-102">Interfaces d’hébergement du CLR et coclasses déconseillées</span><span class="sxs-lookup"><span data-stu-id="a95f1-102">Deprecated CLR Hosting Interfaces and Coclasses</span></span>
<span data-ttu-id="a95f1-103">Cette section décrit les interfaces non managées hôtes peuvent utiliser pour intégrer le common language runtime (CLR) dans les versions du .NET Framework 1.0 et 1.1 dans leurs applications.</span><span class="sxs-lookup"><span data-stu-id="a95f1-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the .NET Framework versions 1.0 and 1.1 into their applications.</span></span> <span data-ttu-id="a95f1-104">Ces interfaces fournissent des méthodes pour un ordinateur hôte configurer et charger le runtime dans un processus.</span><span class="sxs-lookup"><span data-stu-id="a95f1-104">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a95f1-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a95f1-105">In This Section</span></span>  
 <span data-ttu-id="a95f1-106">IAppDomainSetup</span><span class="sxs-lookup"><span data-stu-id="a95f1-106">IAppDomainSetup</span></span>  
 <span data-ttu-id="a95f1-107">Fournit des méthodes pour l’hôte de configurer un <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="a95f1-107">Provides methods for the host to configure an <xref:System.AppDomain>.</span></span>  
  
 [<span data-ttu-id="a95f1-108">ICeeFileGen (classe)</span><span class="sxs-lookup"><span data-stu-id="a95f1-108">ICeeFileGen Class</span></span>](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md)  
 <span data-ttu-id="a95f1-109">(Déconseillée) Fournit des fonctionnalités pour la création d’un fichier exécutable portable natif (PE).</span><span class="sxs-lookup"><span data-stu-id="a95f1-109">(Deprecated) Provides functionality for creating a native portable executable (PE) file.</span></span>  
  
 [<span data-ttu-id="a95f1-110">ICorRuntimeHost (Interface)</span><span class="sxs-lookup"><span data-stu-id="a95f1-110">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 <span data-ttu-id="a95f1-111">Fournit des méthodes pour l’hôte configurer les paramètres de CLR.</span><span class="sxs-lookup"><span data-stu-id="a95f1-111">Provides methods for the host to configure CLR settings.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a95f1-112">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="a95f1-112">Related Sections</span></span>  
 [<span data-ttu-id="a95f1-113">Interfaces d’hébergement CLR</span><span class="sxs-lookup"><span data-stu-id="a95f1-113">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="a95f1-114">Contient des rubriques qui décrivent les interfaces d’hébergement fournis avec le .NET Framework version 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="a95f1-114">Contains topics that describe the hosting interfaces provided with the .NET Framework version 2.0 and later versions.</span></span>