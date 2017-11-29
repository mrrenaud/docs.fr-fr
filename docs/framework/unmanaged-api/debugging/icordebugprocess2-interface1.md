---
title: ICorDebugProcess2 Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess2
helpviewer_keywords: ICorDebugProcess2 interface [.NET Framework debugging]
ms.assetid: 73332138-5fea-441f-b893-61af87d45a42
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ca1a73874f6ca2f839639cbaf731a59721b2aede
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocess2-interface1"></a><span data-ttu-id="89591-102">ICorDebugProcess2 Interface1</span><span class="sxs-lookup"><span data-stu-id="89591-102">ICorDebugProcess2 Interface1</span></span>
<span data-ttu-id="89591-103">Extension logique de l’interface ICorDebugProcess, qui représente un processus en cours d’exécution du code managé.</span><span class="sxs-lookup"><span data-stu-id="89591-103">A logical extension of the ICorDebugProcess interface, which represents a process running managed code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="89591-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="89591-104">Methods</span></span>  
  
|<span data-ttu-id="89591-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="89591-105">Method</span></span>|<span data-ttu-id="89591-106">Description</span><span class="sxs-lookup"><span data-stu-id="89591-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="89591-107">ClearUnmanagedBreakpoint (méthode)</span><span class="sxs-lookup"><span data-stu-id="89591-107">ClearUnmanagedBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)|<span data-ttu-id="89591-108">Supprime un point d’arrêt à l’offset spécifié qui a été défini par un appel précédent à `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="89591-108">Removes a breakpoint at the specified offset that was set by an earlier call to `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span></span>|  
|[<span data-ttu-id="89591-109">GetDesiredNGENCompilerFlags (méthode)</span><span class="sxs-lookup"><span data-stu-id="89591-109">GetDesiredNGENCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getdesiredngencompilerflags-method.md)|<span data-ttu-id="89591-110">Obtient les indicateurs qui doivent être définis pour le common language runtime (CLR) pour charger l’image dans le processus référencé par ce `ICorDebugProcess2`.</span><span class="sxs-lookup"><span data-stu-id="89591-110">Gets the flags that must be set for the common language runtime (CLR) to load the image into the process referenced by this `ICorDebugProcess2`.</span></span>|  
|[<span data-ttu-id="89591-111">GetReferenceValueFromGCHandle (méthode)</span><span class="sxs-lookup"><span data-stu-id="89591-111">GetReferenceValueFromGCHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getreferencevaluefromgchandle-method.md)|<span data-ttu-id="89591-112">Obtient un pointeur de référence à l’objet managé spécifié qui a un garbage collection à gérer.</span><span class="sxs-lookup"><span data-stu-id="89591-112">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>|  
|[<span data-ttu-id="89591-113">GetThreadForTaskID (méthode)</span><span class="sxs-lookup"><span data-stu-id="89591-113">GetThreadForTaskID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getthreadfortaskid-method.md)|<span data-ttu-id="89591-114">Obtient le thread sur lequel s’exécute la tâche avec l’identificateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="89591-114">Gets the thread upon which the task with the specified identifier is executing.</span></span>|  
|[<span data-ttu-id="89591-115">GetVersion (méthode)</span><span class="sxs-lookup"><span data-stu-id="89591-115">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getversion-method.md)|<span data-ttu-id="89591-116">Obtient la version du CLR sur laquelle le processus en cours de débogage s’exécute.</span><span class="sxs-lookup"><span data-stu-id="89591-116">Gets the version of the CLR upon which the process being debugged is running.</span></span>|  
|[<span data-ttu-id="89591-117">SetDesiredNGENCompilerFlags (méthode)</span><span class="sxs-lookup"><span data-stu-id="89591-117">SetDesiredNGENCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md)|<span data-ttu-id="89591-118">Définit les indicateurs qui sont requis pour le compilateur juste-à-temps (JIT) charger une image dans le processus en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="89591-118">Sets the flags that are required for the just-in-time (JIT) compiler to load an image into the process being debugged.</span></span>|  
|[<span data-ttu-id="89591-119">SetUnmanagedBreakpoint (méthode)</span><span class="sxs-lookup"><span data-stu-id="89591-119">SetUnmanagedBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)|<span data-ttu-id="89591-120">Définit un point d’arrêt non managé à l’offset d’image native spécifié.</span><span class="sxs-lookup"><span data-stu-id="89591-120">Sets an unmanaged breakpoint at the specified native image offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89591-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="89591-121">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="89591-122">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="89591-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89591-123">Spécifications</span><span class="sxs-lookup"><span data-stu-id="89591-123">Requirements</span></span>  
 <span data-ttu-id="89591-124">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89591-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89591-125">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="89591-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="89591-126">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89591-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89591-127">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89591-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89591-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89591-128">See Also</span></span>  
 [<span data-ttu-id="89591-129">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="89591-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)