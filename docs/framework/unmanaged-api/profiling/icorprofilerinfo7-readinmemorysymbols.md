---
title: ICorProfilerInfo7::ReadInMemorySymbols
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name:
- ICorProfilerInfo7.ReadInMemorySymbols
api_location:
- CorProf.idl
- CorProf.h
- CorGuids.lib
api_type:
- COM
ms.assetid: 1745a0b9-8332-4777-a670-b549bff3b901
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5851f73cc899ef21d8a5dcfd8f03617641a6625a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a>ICorProfilerInfo7::ReadInMemorySymbols
[Prise en charge dans [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] et versions ultérieures]  
  
 Lit les octets à partir d’un flux de symbole de mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `moduleId`  
 [in] Identificateur du module contenant le flux de données en mémoire.  
  
 `symbolsReadOffset`  
 [in] Offset dans le flux en mémoire à partir duquel commencer la lecture des octets.  
  
 `pSymbolBytes`  
 [out] Pointeur vers la mémoire tampon à laquelle les données seront copiées. La mémoire tampon doit avoir `countSymbolBytes` d’espace disponible.  
  
 `countSymbolBytes`  
 [in] Le nombre d’octets à copier.  
  
 `pCountSymbolBytesRead`  
 [out] Lorsque la méthode est retournée, contient le nombre réel d’octets lus.  
  
## <a name="return-value"></a>Valeur de retour  
 `S_OK`, si un nombre d’octets qui ont été lus.  
  
 `CORPROF_E_MODULE_IS_DYNAMIC`, si le module a été créé à l’aide de <xref:System.Reflection.Emit>.  
  
## <a name="remarks"></a>Notes  
 Le `ReadInMemorySymbols` méthode tente de lire `countSymbolBytes` de données, en commençant au décalage `symbolsReadOffset` dans le flux en mémoire. Les données sont copiées à `pSymbolBytes`, qui est censé avoir `countSymbolBytes` d’espace disponible.     `pCountSymbolsBytesRead`contient le nombre réel d’octets lus, ce qui peut être inférieure à `countSymbolBytes` si la fin du flux est atteinte.  
  
> [!NOTE]
>  L’implémentation actuelle ne prend pas en charge Reflection.Emit. Si le module a été créé à l’aide de Reflection.Emit, la méthode retourne `CORPROF_E_MODULE_IS_DYNAMIC`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorProfilerInfo7, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
