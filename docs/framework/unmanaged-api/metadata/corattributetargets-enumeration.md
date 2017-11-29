---
title: "CorAttributeTargets, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorAttributeTargets
api_location: mscoree.dll
api_type: COM
f1_keywords: CorAttributeTargets
helpviewer_keywords: CorAttributeTargets enumeration [.NET Framework metadata]
ms.assetid: 694c0fa0-7011-41a9-9dfd-f0e16ea574b5
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ce783c790eeb15c60d8e7699396755a560df7c9c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="corattributetargets-enumeration"></a><span data-ttu-id="09380-102">CorAttributeTargets, énumération</span><span class="sxs-lookup"><span data-stu-id="09380-102">CorAttributeTargets Enumeration</span></span>
<span data-ttu-id="09380-103">Spécifie les éléments de l'application auxquels un attribut peut être appliqué.</span><span class="sxs-lookup"><span data-stu-id="09380-103">Specifies the application elements on which it is valid to apply an attribute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09380-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09380-104">Syntax</span></span>  
  
```  
typedef enum CorAttributeTargets  
{  
    catAssembly            = 0x0001,  
    catModule              = 0x0002,  
    catClass               = 0x0004,  
    catStruct              = 0x0008,  
    catEnum                = 0x0010,  
    catConstructor         = 0x0020,  
    catMethod              = 0x0040,  
    catProperty            = 0x0080,  
    catField               = 0x0100,  
    catEvent               = 0x0200,  
    catInterface           = 0x0400,  
    catParameter           = 0x0800,  
    catDelegate            = 0x1000,  
    catGenericParameter    = 0x4000,  
  
    catAll                 =   
        catAssembly | catModule | catClass | catStruct |   
        catEnum | catConstructor | catMethod | catProperty |   
        catField | catEvent | catInterface | catParameter |   
        catDelegate | catGenericParameter,  
  
    catClassMembers        =   
        catClass | catStruct | catEnum | catConstructor |   
        catMethod | catProperty | catField | catEvent |   
        catDelegate | catInterface  
  
} CorAttributeTargets;  
```  
  
## <a name="members"></a><span data-ttu-id="09380-105">Membres</span><span class="sxs-lookup"><span data-stu-id="09380-105">Members</span></span>  
  
|<span data-ttu-id="09380-106">Membre</span><span class="sxs-lookup"><span data-stu-id="09380-106">Member</span></span>|<span data-ttu-id="09380-107">Description</span><span class="sxs-lookup"><span data-stu-id="09380-107">Description</span></span>|  
|------------|-----------------|  
|`catAssembly`|<span data-ttu-id="09380-108">Attribut peut être appliqué à un assembly.</span><span class="sxs-lookup"><span data-stu-id="09380-108">Attribute can be applied to an assembly.</span></span>|  
|`catModule`|<span data-ttu-id="09380-109">Attribut peut être appliqué à un module (.dll ou .exe) exécutable portable.</span><span class="sxs-lookup"><span data-stu-id="09380-109">Attribute can be applied to a portable executable (.dll or .exe) module.</span></span>|  
|`catClass`|<span data-ttu-id="09380-110">Attribut peut être appliqué à une classe.</span><span class="sxs-lookup"><span data-stu-id="09380-110">Attribute can be applied to a class.</span></span>|  
|`catStruct`|<span data-ttu-id="09380-111">Attribut peut être appliqué à une structure ; Autrement dit, un type valeur.</span><span class="sxs-lookup"><span data-stu-id="09380-111">Attribute can be applied to a structure; that is, a value type.</span></span>|  
|`catEnum`|<span data-ttu-id="09380-112">Attribut peut être appliqué à une énumération.</span><span class="sxs-lookup"><span data-stu-id="09380-112">Attribute can be applied to an enumeration.</span></span>|  
|`catConstructor`|<span data-ttu-id="09380-113">Attribut peut être appliqué à un constructeur.</span><span class="sxs-lookup"><span data-stu-id="09380-113">Attribute can be applied to a constructor.</span></span>|  
|`catMethod`|<span data-ttu-id="09380-114">Attribut peut être appliqué à une méthode.</span><span class="sxs-lookup"><span data-stu-id="09380-114">Attribute can be applied to a method.</span></span>|  
|`catProperty`|<span data-ttu-id="09380-115">Attribut peut être appliqué à une propriété.</span><span class="sxs-lookup"><span data-stu-id="09380-115">Attribute can be applied to a property.</span></span>|  
|`catField`|<span data-ttu-id="09380-116">Attribut peut être appliqué à un champ.</span><span class="sxs-lookup"><span data-stu-id="09380-116">Attribute can be applied to a field.</span></span>|  
|`catEvent`|<span data-ttu-id="09380-117">Attribut peut être appliqué à un événement.</span><span class="sxs-lookup"><span data-stu-id="09380-117">Attribute can be applied to an event.</span></span>|  
|`catInterface`|<span data-ttu-id="09380-118">Attribut peut être appliqué à une interface.</span><span class="sxs-lookup"><span data-stu-id="09380-118">Attribute can be applied to an interface.</span></span>|  
|`catParameter`|<span data-ttu-id="09380-119">Attribut peut être appliqué à un paramètre.</span><span class="sxs-lookup"><span data-stu-id="09380-119">Attribute can be applied to a parameter.</span></span>|  
|`catDelegate`|<span data-ttu-id="09380-120">Attribut peut être appliqué à un délégué.</span><span class="sxs-lookup"><span data-stu-id="09380-120">Attribute can be applied to a delegate.</span></span>|  
|`catGenericParameter`|<span data-ttu-id="09380-121">Attribut peut être appliqué à un paramètre générique.</span><span class="sxs-lookup"><span data-stu-id="09380-121">Attribute can be applied to a generic parameter.</span></span>|  
|`catAll`|<span data-ttu-id="09380-122">Attribut peut être appliqué à n’importe quel élément d’application.</span><span class="sxs-lookup"><span data-stu-id="09380-122">Attribute can be applied to any application element.</span></span>|  
|`catClassMembers`|<span data-ttu-id="09380-123">Attribut peut être appliqué à un membre d’une classe.</span><span class="sxs-lookup"><span data-stu-id="09380-123">Attribute can be applied to a member of a class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09380-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="09380-124">Remarks</span></span>  
 <span data-ttu-id="09380-125">Le `CorAttributeTargets` valeurs d’énumération peuvent être combinées avec une opération OR au niveau du bit pour obtenir la combinaison souhaitée.</span><span class="sxs-lookup"><span data-stu-id="09380-125">The `CorAttributeTargets` enumeration values can be combined with a bitwise OR operation to get the preferred combination.</span></span>  
  
 <span data-ttu-id="09380-126">Le `CorAttributeTargets` correspond managé <xref:System.AttributeTargets?displayProperty=nameWithType> énumération.</span><span class="sxs-lookup"><span data-stu-id="09380-126">The `CorAttributeTargets` parallels the managed <xref:System.AttributeTargets?displayProperty=nameWithType> enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09380-127">Spécifications</span><span class="sxs-lookup"><span data-stu-id="09380-127">Requirements</span></span>  
 <span data-ttu-id="09380-128">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09380-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09380-129">**En-tête :** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="09380-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="09380-130">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09380-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09380-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09380-131">See Also</span></span>  
 [<span data-ttu-id="09380-132">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="09380-132">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)