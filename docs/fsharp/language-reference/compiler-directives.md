---
title: Directives de compilateur (F#)
description: "En savoir plus sur F # language les directives de préprocesseur, directives de compilation conditionnelle, directives de ligne et les directives du compilateur."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 93aef07a-6747-4ce4-a10f-a05168978af6
ms.openlocfilehash: c7ec056f407f3af34528205a5abb1cdef7d43fef
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2018
---
# <a name="compiler-directives"></a>Directives de compilateur

Cette rubrique décrit les directives de processeur et de compilateur.


## <a name="preprocessor-directives"></a>Directives de préprocesseur
Une directive de préprocesseur est précédée du symbole # et s'affiche toute seule sur une ligne. Elle est interprétée par le préprocesseur, qui s'exécute avant le compilateur lui-même.

Le tableau suivant répertorie les directives de préprocesseur disponibles en F#.


|Directive|Description|
|---------|-----------|
|`#if` *symbol*|Prend en charge la compilation conditionnelle. Le code dans la section après le `#if` est inclus si le *symbole* est défini.|
|`#else`|Prend en charge la compilation conditionnelle. Marque une section de code à inclure si le symbole utilisé avec le `#if` précédent n'est pas défini.|
|`#endif`|Prend en charge la compilation conditionnelle. Marque la fin d'une section conditionnelle de code.|
|`#`[ligne] *int*,<br/>`#`[line] *int* *string*,<br/>`#`[line] *int* *verbatim-string*|Indique la ligne et le nom de fichier du code source d'origine, à des fins de débogage. Cette fonctionnalité est fournie pour les outils qui génèrent du code source F#.|
|`#nowarn` *warningcode*|Désactive un ou plusieurs avertissements du compilateur. Pour désactiver un avertissement, trouvez son numéro dans la sortie du compilateur et incluez-le entre guillemets. Omettez le préfixe « FS ». Pour désactiver plusieurs numéros d'avertissement sur la même ligne, incluez chaque nombre entre guillemets, puis séparez chaque chaîne par un espace. Exemple :

`#nowarn "9" "40"`


L’effet de la désactivation d’un message d’avertissement s’applique à l’intégralité du fichier, y compris les parties du fichier qui précèdent la directive. |

## <a name="conditional-compilation-directives"></a>Directives de compilation conditionnelle
Code qui est désactivé par l’une de ces directives apparaît grisé dans l’éditeur de StudioCode Visual.


>[!NOTE] 
Le comportement des directives de compilation conditionnelle n'est pas le même que dans les autres langages. Par exemple, vous ne pouvez pas utiliser des expressions booléennes qui impliquent des symboles et `true` et `false` n'ont aucune signification spéciale. Les symboles que vous utilisez dans la directive `if` doivent être définis par la ligne de commande ou dans les paramètres du projet ; il n'existe aucune directive de préprocesseur `define`.


Le code suivant illustre l'utilisation des directives `#if`, `#else` et `#endif`. Dans cet exemple, le code contient deux versions de la définition de `function1`. Lors de la `VERSION1` est défini à l’aide de la [-définir l’option du compilateur](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04), le code entre les `#if` la directive et le `#else` est activé. Sinon, le code entre `#else` et `#endif` est activé.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7301.fs)]

Il n'existe aucune directive de préprocesseur `#define` en F#. Vous devez utiliser l'option du compilateur ou les paramètres du projet pour définir les symboles utilisés par la directive `#if`.

Les directives de compilation conditionnelle peuvent être imbriquées. Le retrait n'est pas significatif pour les directives de préprocesseur.


## <a name="line-directives"></a>Directives de ligne
Lors de la génération, le compilateur signale les erreurs dans le code F# en référençant les numéros de ligne où chaque erreur se produit. Ces numéros de ligne commencent à 1 pour la première ligne dans un fichier. Toutefois, si vous générez du code source F# à partir d'un autre outil, les numéros de ligne du code généré n'ont en général aucun intérêt, car les erreurs dans le code F# généré proviennent très probablement d'une autre source. La directive `#line` offre un moyen aux auteurs d'outils qui génèrent du code source F# de transmettre des informations sur les numéros de ligne et fichiers sources d'origine au code F# généré.

Quand vous utilisez la directive `#line`, vous devez placer les noms de fichiers entre guillemets. À moins que le jeton textuel (`@`) ne s'affiche devant la chaîne, vous devez utiliser deux barres obliques inverses en tant que caractères d'espacement au lieu d'une pour les utiliser dans le chemin d'accès. Les jetons de ligne valides sont les suivants : Dans ces exemples, supposons que le fichier d'origine `Script1` produit un fichier de code F# généré automatiquement quand il est exécuté par l'intermédiaire d'un outil et que le code situé à l'emplacement de ces directives est généré à partir de jetons à la ligne 25 du fichier `Script1`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7303.fs)]

Ces jetons indiquent que le code F# généré à cet emplacement dérive de certaines constructions situées à ou près de la ligne `25` dans `Script1`.


## <a name="compiler-directives"></a>Directives de compilateur
Les directives de compilateur ressemblent aux directives de préprocesseur, car elles sont précédées d'un signe #, mais au lieu d'être interprétées par le préprocesseur, elles sont laissées au compilateur pour ce qui est de leur interprétation et des actions qu'elles entraînent.

Le tableau suivant répertorie la directive de compilateur disponible en F#.


|Directive|Description|
|---------|-----------|
|`#light` ["on"&#124;"off"]|Active ou désactive la syntaxe simplifiée, à des fins de compatibilité avec d'autres versions de ML. Par défaut, la syntaxe simplifiée est activée. La syntaxe détaillée est toujours activée. Par conséquent, vous pouvez utiliser la syntaxe simplifiée et la syntaxe détaillée. La directive `#light` en elle-même équivaut à `#light "on"`. Si vous spécifiez `#light "off"`, vous devez utiliser la syntaxe détaillée pour toutes les constructions de langage. La syntaxe présentée dans la documentation de F# part du principe que vous utilisez la syntaxe simplifiée. Pour plus d’informations, consultez [syntaxe détaillée](verbose-syntax.md).|
Pour les directives d’interpréteur (fsi.exe), consultez [de programmation Interactive avec F #](../tutorials/fsharp-interactive/index.md).


## <a name="see-also"></a>Voir aussi
[Informations de référence du langage F#](index.md)

[Options du compilateur](compiler-options.md)

