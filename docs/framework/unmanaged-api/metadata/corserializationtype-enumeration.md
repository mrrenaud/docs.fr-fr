---
title: "CorSerializationType, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorSerializationType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSerializationType
helpviewer_keywords:
- CorSerializationType enumeration [.NET Framework metadata]
ms.assetid: 6b1fcd11-c7fb-4be2-8910-abc862d4caf4
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e43151b1611f5b9b8218d30ba46a9143f463c193
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="corserializationtype-enumeration"></a>CorSerializationType, énumération
Spécifie la façon dont un objet est sérialisé par le common language runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorSerializationType {  
  
    SERIALIZATION_TYPE_UNDEFINED     = 0,  
    SERIALIZATION_TYPE_BOOLEAN       = ELEMENT_TYPE_BOOLEAN,  
    SERIALIZATION_TYPE_CHAR          = ELEMENT_TYPE_CHAR,  
    SERIALIZATION_TYPE_I1            = ELEMENT_TYPE_I1,  
    SERIALIZATION_TYPE_U1            = ELEMENT_TYPE_U1,  
    SERIALIZATION_TYPE_I2            = ELEMENT_TYPE_I2,  
    SERIALIZATION_TYPE_U2            = ELEMENT_TYPE_U2,  
    SERIALIZATION_TYPE_I4            = ELEMENT_TYPE_I4,  
    SERIALIZATION_TYPE_U4            = ELEMENT_TYPE_U4,  
    SERIALIZATION_TYPE_I8            = ELEMENT_TYPE_I8,  
    SERIALIZATION_TYPE_U8            = ELEMENT_TYPE_U8,  
    SERIALIZATION_TYPE_R4            = ELEMENT_TYPE_R4,  
    SERIALIZATION_TYPE_R8            = ELEMENT_TYPE_R8,  
    SERIALIZATION_TYPE_STRING        = ELEMENT_TYPE_STRING,  
    SERIALIZATION_TYPE_SZARRAY       = ELEMENT_TYPE_SZARRAY,  
    SERIALIZATION_TYPE_TYPE          = 0x50,  
    SERIALIZATION_TYPE_TAGGED_OBJECT = 0x51,  
    SERIALIZATION_TYPE_FIELD         = 0x53,  
    SERIALIZATION_TYPE_PROPERTY      = 0x54,  
    SERIALIZATION_TYPE_ENUM          = 0x55  
  
} CorSerializationType;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`SERIALIZATION_TYPE_UNDEFINED`|Sérialisation de l’objet n’est pas définie.|  
|`SERIALIZATION_TYPE_BOOLEAN`|L’objet est sérialisé comme un type Boolean|  
|`SERIALIZATION_TYPE_CHAR`|Objet est sérialisé comme un type de caractère.|  
|`SERIALIZATION_TYPE_I1`|Objet est sérialisé comme un entier signé de 1 octet.|  
|`SERIALIZATION_TYPE_U1`|Objet est sérialisé en tant qu’entier non signé sur 1 octet.|  
|`SERIALIZATION_TYPE_I2`|Objet est sérialisé comme un entier signé de 2 octets.|  
|`SERIALIZATION_TYPE_U2`|Objet est sérialisé en tant qu’entier non signé de 2 octets.|  
|`SERIALIZATION_TYPE_I4`|Objet est sérialisé comme un entier signé de 4 octets.|  
|`SERIALIZATION_TYPE_U4`|Objet est sérialisé en tant qu’entier non signé de 4 octets.|  
|`SERIALIZATION_TYPE_I8`|Objet est sérialisé comme un entier signé de 8 octets.|  
|`SERIALIZATION_TYPE_U8`|Objet est sérialisé en tant qu’entier non signé de 8 octets.|  
|`SERIALIZATION_TYPE_R4`|Objet est sérialisé en tant qu’un virgule flottante de 4 octets.|  
|`SERIALIZATION_TYPE_R8`|Objet est sérialisé en tant qu’une virgule flottante de 8 octets.|  
|`SERIALIZATION_TYPE_STRING`|Objet est sérialisé en tant que type System.String.|  
|`SERIALIZATION_TYPE_SZARRAY`|L’objet est sérialisé en tant qu’une seule dimension, un tableau de limite inférieure à zéro.|  
|`SERIALIZATION_TYPE_TYPE`|Objet est sérialisé comme un type générique.|  
|`SERIALIZATION_TYPE_TAGGED_OBJECT`|Objet est sérialisé en tant qu’objet avec balises.|  
|`SERIALIZATION_TYPE_FIELD`|L’objet est sérialisé en tant que champ.|  
|`SERIALIZATION_TYPE_PROPERTY`|L’objet est sérialisé en tant que propriété.|  
|`SERIALIZATION_TYPE_ENUM`|L’objet est sérialisé en tant qu’énumération.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorHdr.h  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
