---
title: "ICorDebugHeapEnum::Next, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapEnum::Next
helpviewer_keywords:
- ICorDebugHeapEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 2221fd06-9e27-4113-972e-2530db8c3594
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a15637f925401f23f9da34e33583c9bc5c014dd3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugheapenumnext-method"></a><span data-ttu-id="25266-102">ICorDebugHeapEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="25266-102">ICorDebugHeapEnum::Next Method</span></span>
<span data-ttu-id="25266-103">Obtient le nombre spécifié de [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances qui contiennent des informations sur les objets sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="25266-103">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25266-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25266-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],   
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="25266-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="25266-105">Parameters</span></span>  
 <span data-ttu-id="25266-106">celt</span><span class="sxs-lookup"><span data-stu-id="25266-106">celt</span></span>  
 <span data-ttu-id="25266-107">[in] Nombre d'objets à récupérer.</span><span class="sxs-lookup"><span data-stu-id="25266-107">[in] The number of objects to be retrieved.</span></span>  
  
 <span data-ttu-id="25266-108">objets</span><span class="sxs-lookup"><span data-stu-id="25266-108">objects</span></span>  
 <span data-ttu-id="25266-109">[out] Un tableau de pointeurs, chacun pointant vers un [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objet qui fournit des informations sur un objet sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="25266-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) object that provides information about an object on the managed heap.</span></span>  
  
 <span data-ttu-id="25266-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="25266-110">pceltFetched</span></span>  
 <span data-ttu-id="25266-111">[out] Un pointeur vers le nombre de [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) réellement retournés dans des objets `objects`.</span><span class="sxs-lookup"><span data-stu-id="25266-111">[out] A pointer to the number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects actually returned in `objects`.</span></span> <span data-ttu-id="25266-112">Cette valeur peut être `null` si `celt` est égal à 1.</span><span class="sxs-lookup"><span data-stu-id="25266-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25266-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="25266-113">Remarks</span></span>  
 <span data-ttu-id="25266-114">Le champ `COR_HEAPOBJECT.type` est l'identificateur d'une interface COM imbriquée avec comptage des références.</span><span class="sxs-lookup"><span data-stu-id="25266-114">The `COR_HEAPOBJECT.type` field is the identifier of a nested reference-counted COM interface.</span></span> <span data-ttu-id="25266-115">Cette référence doit être libérée par l'appelant d'`ICorDebugHeapEnum::Next`.</span><span class="sxs-lookup"><span data-stu-id="25266-115">This reference must be released by the caller of `ICorDebugHeapEnum::Next`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25266-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="25266-116">Requirements</span></span>  
 <span data-ttu-id="25266-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25266-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25266-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="25266-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25266-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25266-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25266-120">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25266-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25266-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25266-121">See Also</span></span>  
 [<span data-ttu-id="25266-122">ICorDebugHeapEnum (Interface)</span><span class="sxs-lookup"><span data-stu-id="25266-122">ICorDebugHeapEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
 [<span data-ttu-id="25266-123">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="25266-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)