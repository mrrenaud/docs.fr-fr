---
title: "IMetaDataAssemblyImport::EnumExportedTypes, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.EnumExportedTypes
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::EnumExportedTypes
helpviewer_keywords:
- EnumExportedTypes method [.NET Framework metadata]
- IMetaDataAssemblyImport::EnumExportedTypes method [.NET Framework metadata]
ms.assetid: e5912ed8-e4ce-438b-8ea3-d9e4c288d109
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 76c73cc3d13089b4a38a47d523d8baa77f6eed12
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyimportenumexportedtypes-method"></a><span data-ttu-id="e3e4b-102">IMetaDataAssemblyImport::EnumExportedTypes, méthode</span><span class="sxs-lookup"><span data-stu-id="e3e4b-102">IMetaDataAssemblyImport::EnumExportedTypes Method</span></span>
<span data-ttu-id="e3e4b-103">Énumère les types exportés référencés dans le manifeste d’assembly dans la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="e3e4b-103">Enumerates the exported types referenced in the assembly manifest in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3e4b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3e4b-104">Syntax</span></span>  
  
```  
HRESULT EnumExportedTypes (  
    [in, out] HCORENUM     *phEnum,   
    [out] mdExportedType   rExportedTypes[],   
    [in]  ULONG            cMax,   
    [out] ULONG            *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e3e4b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e3e4b-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="e3e4b-106">[dans, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="e3e4b-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="e3e4b-107">Cela doit être une valeur null lorsque la valeur du `EnumExportedTypes` méthode est appelée pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="e3e4b-107">This must be a null value when the `EnumExportedTypes` method is called for the first time.</span></span>  
  
 `rExportedTypes`  
 <span data-ttu-id="e3e4b-108">[out] L’énumération des `mdExportedType` des jetons de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="e3e4b-108">[out] The enumeration of `mdExportedType` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e3e4b-109">[in] Le nombre maximal de `mdExportedType` jetons qui peuvent être placées dans le `rExportedTypes` tableau.</span><span class="sxs-lookup"><span data-stu-id="e3e4b-109">[in] The maximum number of `mdExportedType` tokens that can be placed in the `rExportedTypes` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="e3e4b-110">[out] Le nombre de `mdExportedType` jetons placés dans `rExportedTypes`.</span><span class="sxs-lookup"><span data-stu-id="e3e4b-110">[out] The number of `mdExportedType` tokens actually placed in `rExportedTypes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e3e4b-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e3e4b-111">Return Value</span></span>  
  
|<span data-ttu-id="e3e4b-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e3e4b-112">HRESULT</span></span>|<span data-ttu-id="e3e4b-113">Description</span><span class="sxs-lookup"><span data-stu-id="e3e4b-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e3e4b-114">`EnumExportedTypes`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="e3e4b-114">`EnumExportedTypes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e3e4b-115">Il n’existe pas de jetons à énumérer.</span><span class="sxs-lookup"><span data-stu-id="e3e4b-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="e3e4b-116">Dans ce cas, `pcTokens` est définie sur zéro.</span><span class="sxs-lookup"><span data-stu-id="e3e4b-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e3e4b-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e3e4b-117">Requirements</span></span>  
 <span data-ttu-id="e3e4b-118">**Plateforme :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3e4b-118">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3e4b-119">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e3e4b-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e3e4b-120">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e3e4b-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e3e4b-121">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3e4b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3e4b-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3e4b-122">See Also</span></span>  
 [<span data-ttu-id="e3e4b-123">IMetaDataAssemblyImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="e3e4b-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)