---
title: ISymUnmanagedDispose, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDispose
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDispose
helpviewer_keywords: ISymUnmanagedDispose interface [.NET Framework debugging]
ms.assetid: b1d74e83-a200-4d00-8fbd-27918808616d
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 12e0d9c2cec1f9fc8439a9b9434e1eff506f8d7b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddispose-interface"></a><span data-ttu-id="ccad7-102">ISymUnmanagedDispose, interface</span><span class="sxs-lookup"><span data-stu-id="ccad7-102">ISymUnmanagedDispose Interface</span></span>
<span data-ttu-id="ccad7-103">Libère les ressources non managées.</span><span class="sxs-lookup"><span data-stu-id="ccad7-103">Disposes of unmanaged resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ccad7-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="ccad7-104">Methods</span></span>  
  
|<span data-ttu-id="ccad7-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="ccad7-105">Method</span></span>|<span data-ttu-id="ccad7-106">Description</span><span class="sxs-lookup"><span data-stu-id="ccad7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ccad7-107">Destroy (méthode)</span><span class="sxs-lookup"><span data-stu-id="ccad7-107">Destroy Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-destroy-method.md)|<span data-ttu-id="ccad7-108">Provoque l’objet sous-jacent libérer toutes les références internes et retourne un échec sur tous les appels de méthode suivants.</span><span class="sxs-lookup"><span data-stu-id="ccad7-108">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ccad7-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ccad7-109">Requirements</span></span>  
 <span data-ttu-id="ccad7-110">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ccad7-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccad7-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ccad7-111">See Also</span></span>  
 [<span data-ttu-id="ccad7-112">Interfaces du magasin de symboles de Diagnostics</span><span class="sxs-lookup"><span data-stu-id="ccad7-112">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)