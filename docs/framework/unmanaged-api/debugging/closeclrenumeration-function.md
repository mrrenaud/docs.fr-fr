---
title: Fonction CloseCLREnumeration
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CloseCLREnumeration
api_location: dbgshim.dll
api_type: COM
f1_keywords: CloseCLREnumeration
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CloseCLR Enumeration function
ms.assetid: 5e3c3958-80bb-43b1-a96b-dd3e6dbd9cd7
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d9f14b851795c92c3ce0c1e7536a4ff78fbdf927
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="closeclrenumeration-function"></a><span data-ttu-id="fc610-102">Fonction CloseCLREnumeration</span><span class="sxs-lookup"><span data-stu-id="fc610-102">CloseCLREnumeration Function</span></span>
<span data-ttu-id="fc610-103">Ferme tout valide common language runtime (CLR) événements continue-startup situés dans un tableau de handles retourné par le [fonction EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)et libère la mémoire pour les tableaux de chemin d’accès de handles et de chaînes.</span><span class="sxs-lookup"><span data-stu-id="fc610-103">Closes any valid common language runtime (CLR) continue-startup events located in an array of handles returned by the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc610-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc610-104">Syntax</span></span>  
  
```  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fc610-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fc610-105">Parameters</span></span>  
 `pHandleArray`  
 <span data-ttu-id="fc610-106">[in] Pointeur vers le tableau de handles d’événement retourné par la [fonction EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span><span class="sxs-lookup"><span data-stu-id="fc610-106">[in] Pointer to the array of event handles returned from the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span></span>  
  
 `pStringArray`  
 <span data-ttu-id="fc610-107">[in] Pointeur vers le tableau de chemins d’accès de la chaîne CLR retournée à partir de la [fonction EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span><span class="sxs-lookup"><span data-stu-id="fc610-107">[in] Pointer to the array of CLR string paths returned from the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span></span>  
  
 `dwArrayLength`  
 <span data-ttu-id="fc610-108">[in] Valeur DWORD contenant la taille (longueur) de `pHandleArray` ou de `pStringArray` (ils sont identiques).</span><span class="sxs-lookup"><span data-stu-id="fc610-108">[in] DWORD that contains the size (length) of either `pHandleArray` or `pStringArray` (they are the same).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc610-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="fc610-109">Return Value</span></span>  
 <span data-ttu-id="fc610-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fc610-110">S_OK</span></span>  
 <span data-ttu-id="fc610-111">Handles ouverts par le [fonction EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md) sont fermés, et de la mémoire allouée pour les tableaux de handles et de chaînes est libérée.</span><span class="sxs-lookup"><span data-stu-id="fc610-111">Handles opened by the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md) are closed, and memory allocated for the handle and string arrays is freed.</span></span>  
  
 <span data-ttu-id="fc610-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="fc610-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="fc610-113">La longueur de `pHandleArray` ne correspond pas à la longueur passée dans `dwArrayLength`.</span><span class="sxs-lookup"><span data-stu-id="fc610-113">The length of `pHandleArray` does not match the length that is passed in `dwArrayLength`.</span></span>  
  
 <span data-ttu-id="fc610-114">E_FAIL (ou autres codes de retour E_)</span><span class="sxs-lookup"><span data-stu-id="fc610-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="fc610-115">La fonction ne peut pas libérer la mémoire pour `pHandleArray` et `pStringArray`.</span><span class="sxs-lookup"><span data-stu-id="fc610-115">The function is unable to free the memory for `pHandleArray` and `pStringArray`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc610-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="fc610-116">Requirements</span></span>  
 <span data-ttu-id="fc610-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc610-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc610-118">**En-tête :** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="fc610-118">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="fc610-119">**Bibliothèque :** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="fc610-119">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="fc610-120">**Versions du .NET framework :** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="fc610-120">**.NET Framework Versions:** 3.5 SP1</span></span>