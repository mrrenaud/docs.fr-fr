---
title: COR_ACTIVE_FUNCTION, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_ACTIVE_FUNCTION
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_ACTIVE_FUNCTION
helpviewer_keywords: COR_ACTIVE_FUNCTION structure [.NET Framework debugging]
ms.assetid: ed86185f-2152-459c-961f-10c06d62e83f
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 85096b607fa2fec9875e497cc1f50167fc482fbd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="coractivefunction-structure"></a><span data-ttu-id="ef8fa-102">COR_ACTIVE_FUNCTION, structure</span><span class="sxs-lookup"><span data-stu-id="ef8fa-102">COR_ACTIVE_FUNCTION Structure</span></span>
<span data-ttu-id="ef8fa-103">Contient des informations sur les fonctions qui sont actuellement actives dans les trames d'un thread.</span><span class="sxs-lookup"><span data-stu-id="ef8fa-103">Contains information about the functions that are currently active in a thread's frames.</span></span> <span data-ttu-id="ef8fa-104">Cette structure est utilisée par le [ICorDebugThread2::GetActiveFunctions](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="ef8fa-104">This structure is used by the [ICorDebugThread2::GetActiveFunctions](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef8fa-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef8fa-105">Syntax</span></span>  
  
```  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="ef8fa-106">Membres</span><span class="sxs-lookup"><span data-stu-id="ef8fa-106">Members</span></span>  
  
|<span data-ttu-id="ef8fa-107">Membre</span><span class="sxs-lookup"><span data-stu-id="ef8fa-107">Member</span></span>|<span data-ttu-id="ef8fa-108">Description</span><span class="sxs-lookup"><span data-stu-id="ef8fa-108">Description</span></span>|  
|------------|-----------------|  
|`pAppDomain`|<span data-ttu-id="ef8fa-109">Pointeur vers le propriétaire du domaine d’application le `ilOffset` champ.</span><span class="sxs-lookup"><span data-stu-id="ef8fa-109">Pointer to the application domain owner of the `ilOffset` field.</span></span>|  
|`pModule`|<span data-ttu-id="ef8fa-110">Pointeur vers le propriétaire du module du `ilOffset` champ.</span><span class="sxs-lookup"><span data-stu-id="ef8fa-110">Pointer to the module owner of the `ilOffset` field.</span></span>|  
|`pFunction`|<span data-ttu-id="ef8fa-111">Pointeur vers le propriétaire de la fonction de la `ilOffset` champ.</span><span class="sxs-lookup"><span data-stu-id="ef8fa-111">Pointer to the function owner of the `ilOffset` field.</span></span>|  
|`ilOffset`|<span data-ttu-id="ef8fa-112">L’offset Microsoft intermediate language (MSIL), de l’image.</span><span class="sxs-lookup"><span data-stu-id="ef8fa-112">The Microsoft intermediate language (MSIL) offset of the frame.</span></span>|  
|`flags`|<span data-ttu-id="ef8fa-113">Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="ef8fa-113">Reserved for future extensibility.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ef8fa-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ef8fa-114">Requirements</span></span>  
 <span data-ttu-id="ef8fa-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef8fa-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef8fa-116">**En-tête :** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="ef8fa-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="ef8fa-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef8fa-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef8fa-118">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef8fa-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef8fa-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef8fa-119">See Also</span></span>  
 [<span data-ttu-id="ef8fa-120">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="ef8fa-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="ef8fa-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="ef8fa-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)