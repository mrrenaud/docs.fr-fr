---
title: "ITypeName::GetAssemblyName, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ITypeName.GetAssemblyName
api_location: mscoree.dll
api_type: COM
f1_keywords: GetAssemblyName
helpviewer_keywords:
- ITypeName::GetAssemblyName method [.NET Framework hosting]
- GetAssemblyName method [.NET Framework hosting]
ms.assetid: 97801d99-f5f1-4a30-882f-959827093fac
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 81f801087ffb190dc24b4b752d90c3fb32ed47d4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="itypenamegetassemblyname-method"></a><span data-ttu-id="2f549-102">ITypeName::GetAssemblyName, méthode</span><span class="sxs-lookup"><span data-stu-id="2f549-102">ITypeName::GetAssemblyName Method</span></span>
<span data-ttu-id="2f549-103">Cette m&#233;thode prend en charge l'infrastructure .NET Framework et n'est pas destin&#233;e &#224; &#234;tre utilis&#233;e directement &#224; partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="2f549-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f549-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f549-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyName (  
    [out, retval] BSTR* rgbszAssemblyNames  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="2f549-105">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2f549-105">Requirements</span></span>  
 <span data-ttu-id="2f549-106">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f549-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f549-107">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2f549-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2f549-108">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2f549-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2f549-109">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f549-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f549-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f549-110">See Also</span></span>  
 [<span data-ttu-id="2f549-111">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="2f549-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)