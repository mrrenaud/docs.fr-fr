---
title: "IMetaDataEmit::SetClassLayout, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetClassLayout
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetClassLayout
helpviewer_keywords:
- IMetaDataEmit::SetClassLayout method [.NET Framework metadata]
- SetClassLayout method [.NET Framework metadata]
ms.assetid: 2576c449-388d-4434-a0e1-9f53991e11b6
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5a68d94cbea408bee90b117965f83f760ba7ea5c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsetclasslayout-method"></a><span data-ttu-id="7e7e5-102">IMetaDataEmit::SetClassLayout, méthode</span><span class="sxs-lookup"><span data-stu-id="7e7e5-102">IMetaDataEmit::SetClassLayout Method</span></span>
<span data-ttu-id="7e7e5-103">Exécute la disposition des champs d’une classe qui a été défini par un appel antérieur à [DefineTypeDef, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="7e7e5-103">Completes the layout of fields for a class that has been defined by a prior call to [DefineTypeDef Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e7e5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e7e5-104">Syntax</span></span>  
  
```  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,   
    [in]  DWORD               dwPackSize,   
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],   
    [in]  ULONG               ulClassSize   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7e7e5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7e7e5-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="7e7e5-106">[in] Un `mdTypeDef` jeton qui spécifie la classe doivent être disposées.</span><span class="sxs-lookup"><span data-stu-id="7e7e5-106">[in] An `mdTypeDef` token that specifies the class to be laid out.</span></span>  
  
 `dwPackSize`  
 <span data-ttu-id="7e7e5-107">[in] La taille de compression : 1, 2, 4, 8 ou 16 octets.</span><span class="sxs-lookup"><span data-stu-id="7e7e5-107">[in] The packing size: 1, 2, 4, 8 or 16 bytes.</span></span> <span data-ttu-id="7e7e5-108">La taille de compression est le nombre d’octets entre des champs adjacents.</span><span class="sxs-lookup"><span data-stu-id="7e7e5-108">The packing size is the number of bytes between adjacent fields.</span></span>  
  
 `rFieldOffsets`  
 <span data-ttu-id="7e7e5-109">[in] Un tableau de [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, dont chacun spécifie un champ de la classe et le champ de l’offset dans la classe.</span><span class="sxs-lookup"><span data-stu-id="7e7e5-109">[in] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, each of which specifies a field of the class and the field's offset within the class.</span></span> <span data-ttu-id="7e7e5-110">Terminez le tableau avec `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="7e7e5-110">Terminate the array with `mdTokenNil`.</span></span>  
  
 `ulClassSize`  
 <span data-ttu-id="7e7e5-111">[in] La taille, en octets, de la classe.</span><span class="sxs-lookup"><span data-stu-id="7e7e5-111">[in] The size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e7e5-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="7e7e5-112">Remarks</span></span>  
 <span data-ttu-id="7e7e5-113">La classe est définie initialement en appelant le [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) (méthode) et en spécifiant une des trois dispositions pour les champs de la classe : automatique, séquentielle ou explicite.</span><span class="sxs-lookup"><span data-stu-id="7e7e5-113">The class is initially defined by calling the [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) method, and specifying one of three layouts for the fields of the class: automatic, sequential, or explicit.</span></span> <span data-ttu-id="7e7e5-114">En règle générale, vous utilisez la disposition automatique et permettre au runtime de choisir la meilleure façon de disposer les champs.</span><span class="sxs-lookup"><span data-stu-id="7e7e5-114">Normally, you would use automatic layout and let the runtime choose the best way to lay out the fields.</span></span>  
  
 <span data-ttu-id="7e7e5-115">Toutefois, vous pourriez les champs présentés en fonction de la disposition de code non managé.</span><span class="sxs-lookup"><span data-stu-id="7e7e5-115">However, you might want the fields laid out according to the arrangement that unmanaged code uses.</span></span> <span data-ttu-id="7e7e5-116">Dans ce cas, choisissez une disposition séquentielle ou explicite et appelez `SetClassLayout` pour terminer la disposition des champs :</span><span class="sxs-lookup"><span data-stu-id="7e7e5-116">In this case, choose either sequential or explicit layout and call `SetClassLayout` to complete the layout of the fields:</span></span>  
  
-   <span data-ttu-id="7e7e5-117">Une disposition séquentielle : spécifiez la taille de compression.</span><span class="sxs-lookup"><span data-stu-id="7e7e5-117">Sequential layout: Specify the packing size.</span></span> <span data-ttu-id="7e7e5-118">Un champ est aligné en fonction de sa taille naturelle ou la taille de compression, selon que le résultat dans le plus petit décalage du champ.</span><span class="sxs-lookup"><span data-stu-id="7e7e5-118">A field is aligned according to either its natural size or the packing size, whichever results in the smaller offset of the field.</span></span> <span data-ttu-id="7e7e5-119">Définissez `rFieldOffsets` et `ulClassSize` à zéro.</span><span class="sxs-lookup"><span data-stu-id="7e7e5-119">Set `rFieldOffsets` and `ulClassSize` to zero.</span></span>  
  
-   <span data-ttu-id="7e7e5-120">Une disposition explicite : spécifiez le décalage de chaque champ ou spécifier la taille de la classe et la taille de compression.</span><span class="sxs-lookup"><span data-stu-id="7e7e5-120">Explicit layout: Either specify the offset of each field or specify the class size and the packing size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e7e5-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7e7e5-121">Requirements</span></span>  
 <span data-ttu-id="7e7e5-122">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e7e5-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e7e5-123">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7e7e5-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7e7e5-124">**Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7e7e5-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7e7e5-125">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e7e5-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e7e5-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7e7e5-126">See Also</span></span>  
 [<span data-ttu-id="7e7e5-127">IMetaDataEmit (Interface)</span><span class="sxs-lookup"><span data-stu-id="7e7e5-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="7e7e5-128">IMetaDataEmit2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="7e7e5-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)