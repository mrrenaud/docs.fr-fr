---
title: "ICorProfilerCallback::AssemblyLoadStarted, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.AssemblyLoadStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::AssemblyLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadStarted method [.NET Framework profiling]
- AssemblyLoadStarted method [.NET Framework profiling]
ms.assetid: 67e8209d-a0ca-4118-a6e6-c1ee0abc2221
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 654cc5fb445184bd07d145701898239bee3e9c8b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackassemblyloadstarted-method"></a><span data-ttu-id="56218-102">ICorProfilerCallback::AssemblyLoadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="56218-102">ICorProfilerCallback::AssemblyLoadStarted Method</span></span>
<span data-ttu-id="56218-103">Notifie le profileur qu’un assembly est chargé.</span><span class="sxs-lookup"><span data-stu-id="56218-103">Notifies the profiler that an assembly is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56218-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56218-104">Syntax</span></span>  
  
```  
HRESULT AssemblyLoadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="56218-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="56218-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="56218-106">[in] Identifie l’assembly est chargé.</span><span class="sxs-lookup"><span data-stu-id="56218-106">[in] Identifies the assembly that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56218-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="56218-107">Remarks</span></span>  
 <span data-ttu-id="56218-108">La valeur de `assemblyId` n’est pas valide pour une demande d’informations jusqu'à ce que le [ICorProfilerCallback::AssemblyLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md) méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="56218-108">The value of `assemblyId` is not valid for an information request until the [ICorProfilerCallback::AssemblyLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56218-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="56218-109">Requirements</span></span>  
 <span data-ttu-id="56218-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56218-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56218-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="56218-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="56218-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56218-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56218-113">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56218-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56218-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56218-114">See Also</span></span>  
 [<span data-ttu-id="56218-115">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="56218-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)