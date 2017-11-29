---
title: "Champs explicites : mot clé val (F#)"
description: "En savoir plus sur F # 'val' mot clé, qui est utilisé pour déclarer un emplacement pour stocker une valeur dans un type classe ou structure sans l’initialisation du type."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3bdbc745-436b-407f-bf54-5d11ca829cd0
ms.openlocfilehash: cee53a48f08aec89b0bdd40189ed331cadee877d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="explicit-fields-the-val-keyword"></a><span data-ttu-id="3f88a-104">Champs explicites : mot clé val</span><span class="sxs-lookup"><span data-stu-id="3f88a-104">Explicit Fields: The val Keyword</span></span>

<span data-ttu-id="3f88a-105">Le mot clé `val` est utilisé pour déclarer un emplacement pour stocker une valeur dans un type de classe ou de structure sans l'initialiser.</span><span class="sxs-lookup"><span data-stu-id="3f88a-105">The `val` keyword is used to declare a location to store a value in a class or structure type, without initializing it.</span></span> <span data-ttu-id="3f88a-106">Les emplacements de stockage déclarés de cette manière sont appelés *champs explicites*.</span><span class="sxs-lookup"><span data-stu-id="3f88a-106">Storage locations declared in this manner are called *explicit fields*.</span></span> <span data-ttu-id="3f88a-107">Une autre utilisation du mot clé `val` consiste à l'associer avec le mot clé `member` pour déclarer une propriété implémentée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="3f88a-107">Another use of the `val` keyword is in conjunction with the `member` keyword to declare an auto-implemented property.</span></span> <span data-ttu-id="3f88a-108">Pour plus d’informations sur les propriétés implémentées automatiquement, consultez [propriétés](properties.md).</span><span class="sxs-lookup"><span data-stu-id="3f88a-108">For more information on auto-implemented properties, see [Properties](properties.md).</span></span>


## <a name="syntax"></a><span data-ttu-id="3f88a-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f88a-109">Syntax</span></span>

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a><span data-ttu-id="3f88a-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="3f88a-110">Remarks</span></span>
<span data-ttu-id="3f88a-111">La façon habituelle de définir des champs dans un type de classe ou de structure consiste à utiliser une liaison `let`.</span><span class="sxs-lookup"><span data-stu-id="3f88a-111">The usual way to define fields in a class or structure type is to use a `let` binding.</span></span> <span data-ttu-id="3f88a-112">Toutefois, les liaisons `let` doivent être initialisées dans le cadre du constructeur de classe, ce qui n'est pas toujours possible, nécessaire ou souhaitable.</span><span class="sxs-lookup"><span data-stu-id="3f88a-112">However, `let` bindings must be initialized as part of the class constructor, which is not always possible, necessary, or desirable.</span></span> <span data-ttu-id="3f88a-113">Vous pouvez utiliser le mot clé `val` quand vous voulez un champ qui n'est pas initialisé.</span><span class="sxs-lookup"><span data-stu-id="3f88a-113">You can use the `val` keyword when you want a field that is uninitialized.</span></span>

<span data-ttu-id="3f88a-114">Les champs explicites peuvent être statiques ou non statiques.</span><span class="sxs-lookup"><span data-stu-id="3f88a-114">Explicit fields can be static or non-static.</span></span> <span data-ttu-id="3f88a-115">Le *modificateur d’accès* peut être `public`, `private`, ou `internal`.</span><span class="sxs-lookup"><span data-stu-id="3f88a-115">The *access-modifier* can be `public`, `private`, or `internal`.</span></span> <span data-ttu-id="3f88a-116">Par défaut, les champs explicites sont publics.</span><span class="sxs-lookup"><span data-stu-id="3f88a-116">By default, explicit fields are public.</span></span> <span data-ttu-id="3f88a-117">À la différence des liaisons `let` dans les classes, qui elles sont toujours privées.</span><span class="sxs-lookup"><span data-stu-id="3f88a-117">This differs from `let` bindings in classes, which are always private.</span></span>

<span data-ttu-id="3f88a-118">Le [DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) l’attribut est nécessaire pour les champs explicites dans les types de classe qui ont un constructeur principal.</span><span class="sxs-lookup"><span data-stu-id="3f88a-118">The [DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) attribute is required on explicit fields in class types that have a primary constructor.</span></span> <span data-ttu-id="3f88a-119">Cet attribut spécifie que le champ est initialisé à zéro.</span><span class="sxs-lookup"><span data-stu-id="3f88a-119">This attribute specifies that the field is initialized to zero.</span></span> <span data-ttu-id="3f88a-120">Le type du champ doit prendre en charge l'initialisation à zéro.</span><span class="sxs-lookup"><span data-stu-id="3f88a-120">The type of the field must support zero-initialization.</span></span> <span data-ttu-id="3f88a-121">Un type prend en charge l'initialisation à zéro s'il s'agit d'un type suivant :</span><span class="sxs-lookup"><span data-stu-id="3f88a-121">A type supports zero-initialization if it is one of the following:</span></span>

- <span data-ttu-id="3f88a-122">Type primitif qui a une valeur zéro.</span><span class="sxs-lookup"><span data-stu-id="3f88a-122">A primitive type that has a zero value.</span></span>

- <span data-ttu-id="3f88a-123">Type qui prend en charge une valeur null, en tant que valeur normale, en tant que valeur anormale ou en tant que représentation d'une valeur.</span><span class="sxs-lookup"><span data-stu-id="3f88a-123">A type that supports a null value, either as a normal value, as an abnormal value, or as a representation of a value.</span></span> <span data-ttu-id="3f88a-124">Sont inclus les classes, les tuples, les enregistrements, les fonctions, les interfaces, les types référence .NET, le type `unit` et les types union discriminée.</span><span class="sxs-lookup"><span data-stu-id="3f88a-124">This includes classes, tuples, records, functions, interfaces, .NET reference types, the `unit` type, and discriminated union types.</span></span>

- <span data-ttu-id="3f88a-125">Type valeur .NET.</span><span class="sxs-lookup"><span data-stu-id="3f88a-125">A .NET value type.</span></span>

- <span data-ttu-id="3f88a-126">Structure dont les champs prennent tous en charge une valeur zéro par défaut.</span><span class="sxs-lookup"><span data-stu-id="3f88a-126">A structure whose fields all support a default zero value.</span></span>


<span data-ttu-id="3f88a-127">Par exemple, un champ immuable appelé `someField` a un champ de stockage dans la représentation compilée .NET portant le nom `someField@` et vous accédez à la valeur stockée à l'aide d'une propriété nommée `someField`.</span><span class="sxs-lookup"><span data-stu-id="3f88a-127">For example, an immutable field called `someField` has a backing field in the .NET compiled representation with the name `someField@`, and you access the stored value using a property named `someField`.</span></span>

<span data-ttu-id="3f88a-128">Pour un champ mutable, la représentation compilée .NET est un champ .NET.</span><span class="sxs-lookup"><span data-stu-id="3f88a-128">For a mutable field, the .NET compiled representation is a .NET field.</span></span>


>[!WARNING] 
<span data-ttu-id="3f88a-129">`Note`L’espace de noms .NET Framework `System.ComponentModel` contient un attribut qui porte le même nom.</span><span class="sxs-lookup"><span data-stu-id="3f88a-129">`Note` The .NET Framework namespace `System.ComponentModel` contains an attribute that has the same name.</span></span> <span data-ttu-id="3f88a-130">Pour plus d'informations sur cet attribut, consultez `System.ComponentModel.DefaultValueAttribute`.</span><span class="sxs-lookup"><span data-stu-id="3f88a-130">For information about this attribute, see `System.ComponentModel.DefaultValueAttribute`.</span></span>


<span data-ttu-id="3f88a-131">Le code suivant illustre l'utilisation de champs explicites et, à titre de comparaison, d'une liaison `let` dans une classe qui a un constructeur principal.</span><span class="sxs-lookup"><span data-stu-id="3f88a-131">The following code shows the use of explicit fields and, for comparison, a `let` binding in a class that has a primary constructor.</span></span> <span data-ttu-id="3f88a-132">Notez que le champ lié à `let` `myInt1` est privé.</span><span class="sxs-lookup"><span data-stu-id="3f88a-132">Note that the `let`-bound field `myInt1` is private.</span></span> <span data-ttu-id="3f88a-133">Quand le champ lié à `let` `myInt1` est référencé à partir d'une méthode membre, l'auto-identificateur `this` n'est pas requis.</span><span class="sxs-lookup"><span data-stu-id="3f88a-133">When the `let`-bound field `myInt1` is referenced from a member method, the self identifier `this` is not required.</span></span> <span data-ttu-id="3f88a-134">Mais quand vous référencez les champs explicites `myInt2` et `myString`, l'auto-identificateur est requis.</span><span class="sxs-lookup"><span data-stu-id="3f88a-134">But when you are referencing the explicit fields `myInt2` and `myString`, the self identifier is required.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

<span data-ttu-id="3f88a-135">La sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="3f88a-135">The output is as follows:</span></span>

```
11 12 abc
30 def
```

<span data-ttu-id="3f88a-136">Le code suivant illustre l'utilisation de champs explicites dans une classe qui n'a pas de constructeur principal.</span><span class="sxs-lookup"><span data-stu-id="3f88a-136">The following code shows the use of explicit fields in a class that does not have a primary constructor.</span></span> <span data-ttu-id="3f88a-137">Dans ce cas, l'attribut `DefaultValue` n'est pas requis, mais tous les champs doivent être initialisés dans les constructeurs définis pour le type.</span><span class="sxs-lookup"><span data-stu-id="3f88a-137">In this case, the `DefaultValue` attribute is not required, but all the fields must be initialized in the constructors that are defined for the type.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

<span data-ttu-id="3f88a-138">Le résultat est `35 22`.</span><span class="sxs-lookup"><span data-stu-id="3f88a-138">The output is `35 22`.</span></span>

<span data-ttu-id="3f88a-139">Le code suivant illustre l'utilisation de champs explicites dans une structure.</span><span class="sxs-lookup"><span data-stu-id="3f88a-139">The following code shows the use of explicit fields in a structure.</span></span> <span data-ttu-id="3f88a-140">Comme une structure est un type valeur, elle a automatiquement un constructeur par défaut qui définit les valeurs de ses champs à zéro.</span><span class="sxs-lookup"><span data-stu-id="3f88a-140">Because a structure is a value type, it automatically has a default constructor that sets the values of its fields to zero.</span></span> <span data-ttu-id="3f88a-141">Ainsi, l'attribut `DefaultValue` n'est pas requis.</span><span class="sxs-lookup"><span data-stu-id="3f88a-141">Therefore, the `DefaultValue` attribute is not required.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

<span data-ttu-id="3f88a-142">Le résultat est `11 xyz`.</span><span class="sxs-lookup"><span data-stu-id="3f88a-142">The output is `11 xyz`.</span></span>

<span data-ttu-id="3f88a-143">Les champs explicites n'ont pas vocation à être utilisés dans le cadre d'une routine.</span><span class="sxs-lookup"><span data-stu-id="3f88a-143">Explicit fields are not intended for routine use.</span></span> <span data-ttu-id="3f88a-144">En général, quand cela est possible, vous devez utiliser une liaison `let` dans une classe au lieu d'un champ explicite.</span><span class="sxs-lookup"><span data-stu-id="3f88a-144">In general, when possible you should use a `let` binding in a class instead of an explicit field.</span></span> <span data-ttu-id="3f88a-145">Les champs explicites s'avèrent utiles dans certains scénarios d'interopérabilité, notamment quand vous devez définir une structure qui sera utilisée dans un appel de code non managé à une API native ou dans des scénarios COM interop.</span><span class="sxs-lookup"><span data-stu-id="3f88a-145">Explicit fields are useful in certain interoperability scenarios, such as when you need to define a structure that will be used in a platform invoke call to a native API, or in COM interop scenarios.</span></span> <span data-ttu-id="3f88a-146">Pour plus d’informations, consultez [fonctions externes](../functions/external-functions.md).</span><span class="sxs-lookup"><span data-stu-id="3f88a-146">For more information, see [External Functions](../functions/external-functions.md).</span></span> <span data-ttu-id="3f88a-147">Une autre situation dans laquelle un champ explicite peut s'avérer nécessaire est liée à l'utilisation d'un générateur de code F# qui émet des classes sans constructeur principal.</span><span class="sxs-lookup"><span data-stu-id="3f88a-147">Another situation in which an explicit field might be necessary is when you are working with an F# code generator which emits classes without a primary constructor.</span></span> <span data-ttu-id="3f88a-148">Les champs explicites s'avèrent également utiles pour les variables static de thread ou les constructions similaires.</span><span class="sxs-lookup"><span data-stu-id="3f88a-148">Explicit fields are also useful for thread-static variables or similar constructs.</span></span> <span data-ttu-id="3f88a-149">Pour plus d'informations, consultez `System.ThreadStaticAttribute`.</span><span class="sxs-lookup"><span data-stu-id="3f88a-149">For more information, see `System.ThreadStaticAttribute`.</span></span>

<span data-ttu-id="3f88a-150">Quand les mots clés `member val` apparaissent ensemble dans une définition de type, il s'agit de la définition d'une propriété implémentée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="3f88a-150">When the keywords `member val` appear together in a type definition, it is a definition of an automatically implemented property.</span></span> <span data-ttu-id="3f88a-151">Pour plus d’informations, consultez [propriétés](properties.md).</span><span class="sxs-lookup"><span data-stu-id="3f88a-151">For more information, see [Properties](properties.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="3f88a-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f88a-152">See Also</span></span>
[<span data-ttu-id="3f88a-153">Propriétés</span><span class="sxs-lookup"><span data-stu-id="3f88a-153">Properties</span></span>](properties.md)

[<span data-ttu-id="3f88a-154">Membres</span><span class="sxs-lookup"><span data-stu-id="3f88a-154">Members</span></span>](index.md)

[<span data-ttu-id="3f88a-155">Liaisons `let` dans des classes</span><span class="sxs-lookup"><span data-stu-id="3f88a-155">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)