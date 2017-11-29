---
title: "IMetaDataTables::GetBlob, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetBlob
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetBlob
helpviewer_keywords:
- GetBlob method [.NET Framework metadata]
- IMetaDataTables::GetBlob method [.NET Framework metadata]
ms.assetid: 94667c1c-6d58-4aa7-b74e-530b11e2a276
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c777396c5020e738c3aade0217bc400aa595dd30
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgetblob-method"></a><span data-ttu-id="9dc5e-102">IMetaDataTables::GetBlob, méthode</span><span class="sxs-lookup"><span data-stu-id="9dc5e-102">IMetaDataTables::GetBlob Method</span></span>
<span data-ttu-id="9dc5e-103">Obtient un pointeur vers l’objet binaire volumineux (BLOB) à l’index de la colonne spécifiée.</span><span class="sxs-lookup"><span data-stu-id="9dc5e-103">Gets a pointer to the binary large object (BLOB) at the specified column index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9dc5e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9dc5e-104">Syntax</span></span>  
  
```  
HRESULT GetBlob (  
    [in]  ULONG          ixBlob,  
    [out] ULONG          *pcbData,  
    [out] const void     **ppData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9dc5e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9dc5e-105">Parameters</span></span>  
 `ixBlob`  
 <span data-ttu-id="9dc5e-106">[in] L’adresse mémoire à partir duquel obtenir `ppData`.</span><span class="sxs-lookup"><span data-stu-id="9dc5e-106">[in] The memory address from which to get `ppData`.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="9dc5e-107">[out] Un pointeur vers la taille, en octets, de `ppData`.</span><span class="sxs-lookup"><span data-stu-id="9dc5e-107">[out] A pointer to the size, in bytes, of `ppData`.</span></span>  
  
 `ppData`  
 <span data-ttu-id="9dc5e-108">[out] Un pointeur vers un pointeur vers les données binaires récupérées.</span><span class="sxs-lookup"><span data-stu-id="9dc5e-108">[out] A pointer to a pointer to the binary data retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9dc5e-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9dc5e-109">Requirements</span></span>  
 <span data-ttu-id="9dc5e-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9dc5e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9dc5e-111">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9dc5e-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9dc5e-112">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9dc5e-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9dc5e-113">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9dc5e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dc5e-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9dc5e-114">See Also</span></span>  
 [<span data-ttu-id="9dc5e-115">IMetaDataTables (Interface)</span><span class="sxs-lookup"><span data-stu-id="9dc5e-115">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="9dc5e-116">IMetaDataTables2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="9dc5e-116">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)