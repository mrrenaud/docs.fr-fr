---
title: "ICorProfilerCallback::ManagedToUnmanagedTransition, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ManagedToUnmanagedTransition
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ManagedToUnmanagedTransition
helpviewer_keywords:
- ManagedToUnmanagedTransition method [.NET Framework profiling]
- ICorProfilerCallback::ManagedToUnmanagedTransition method [.NET Framework profiling]
ms.assetid: ef3cd619-912d-40c5-a449-03ba02a39ee7
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9da8dd44d5b87cd1c65b8b8837c9dd378039d332
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a><span data-ttu-id="c33db-102">ICorProfilerCallback::ManagedToUnmanagedTransition, méthode</span><span class="sxs-lookup"><span data-stu-id="c33db-102">ICorProfilerCallback::ManagedToUnmanagedTransition Method</span></span>
<span data-ttu-id="c33db-103">Notifie le profileur qu’une transition du code managé au code non managé s’est produite.</span><span class="sxs-lookup"><span data-stu-id="c33db-103">Notifies the profiler that a transition from managed code to unmanaged code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c33db-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c33db-104">Syntax</span></span>  
  
```  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c33db-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c33db-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="c33db-106">[in] L’ID de la fonction est appelée.</span><span class="sxs-lookup"><span data-stu-id="c33db-106">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="c33db-107">[in] Une valeur de la [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) énumération qui indique si la transition s’est produite en raison d’un appel de code non managé à partir du code managé ou en raison d’un retour d’une fonction managée appelée par un objet non managé.</span><span class="sxs-lookup"><span data-stu-id="c33db-107">[in] A value of the [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into unmanaged code from managed code, or because of a return from a managed function called by an unmanaged one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c33db-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="c33db-108">Remarks</span></span>  
 <span data-ttu-id="c33db-109">Si la valeur de `reason` est COR_PRF_TRANSITION_CALL, l’ID de fonction est que de la fonction non managée, qui n’ont jamais été compilée à l’aide du compilateur juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="c33db-109">If the value of `reason` is COR_PRF_TRANSITION_CALL, the function ID is that of the unmanaged function, which will never have been compiled using the just-in-time compiler.</span></span> <span data-ttu-id="c33db-110">Fonctions non managées ont des informations de base associées, telles qu’un nom et des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="c33db-110">Unmanaged functions have basic information associated with them, such as a name and some metadata.</span></span> <span data-ttu-id="c33db-111">Si la fonction non managée a été appelée à l’aide de plate-forme implicite code non managé (PInvoke), le runtime ne peut pas déterminer la destination de l’appel et la valeur de `functionId` sera null.</span><span class="sxs-lookup"><span data-stu-id="c33db-111">If the unmanaged function was called by using implicit platform invoke (PInvoke), the runtime cannot determine the destination of the call and the value of `functionId` will be null.</span></span> <span data-ttu-id="c33db-112">Pour plus d’informations sur un PInvoke implicite, consultez [à l’aide du interopérabilité C++ (PInvoke implicite)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).</span><span class="sxs-lookup"><span data-stu-id="c33db-112">For more information on implicit PInvoke, see [Using C++ Interop (Implicit PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c33db-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c33db-113">Requirements</span></span>  
 <span data-ttu-id="c33db-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c33db-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c33db-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c33db-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c33db-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c33db-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c33db-117">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c33db-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c33db-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c33db-118">See Also</span></span>  
 [<span data-ttu-id="c33db-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="c33db-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="c33db-120">UnmanagedToManagedTransition (méthode)</span><span class="sxs-lookup"><span data-stu-id="c33db-120">UnmanagedToManagedTransition Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)  
 [<span data-ttu-id="c33db-121">Utilisation d’un PInvoke explicite en C++ (attribut DllImport)</span><span class="sxs-lookup"><span data-stu-id="c33db-121">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)