---
title: "Empaquetage et déploiement des extensions My (Visual Basic) personnalisé"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 94a9ea977d0add14ae9f0c9a889b008b94610ee0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="packaging-and-deploying-custom-my-extensions-visual-basic"></a>Empaquetage et déploiement des extensions My (Visual Basic) personnalisé
Visual Basic fournit un moyen simple pour vous permettre de déployer votre personnalisé `My` extensions de l’espace de noms à l’aide de modèles Visual Studio. Si vous créez un modèle de projet pour lequel votre `My` extensions font partie intégrante du nouveau type de projet, vous pouvez simplement inclure votre personnalisé `My` code d’extension avec le projet lorsque vous exportez le modèle. Pour plus d’informations sur l’exportation de modèles de projet, consultez [Comment : créer des modèles de projet](/visualstudio/ide/how-to-create-project-templates).  
  
 Si votre personnalisé `My` extension est dans un seul fichier de code, vous pouvez exporter le fichier en tant que modèle d’élément que les utilisateurs peuvent ajouter à tout type de projet Visual Basic. Vous pouvez ensuite personnaliser le modèle d’élément pour activer des fonctionnalités supplémentaires et comportement pour votre personnalisé `My` extension dans un projet Visual Basic. Ces fonctionnalités sont les suivantes :  
  
-   Ce qui permet aux utilisateurs de gérer vos `My` extension à partir de la **Extensions My** page du Concepteur de projets Visual Basic.  
  
-   Ajout automatique de vos `My` extension lorsqu’une référence à un assembly spécifié est ajoutée à un projet.  
  
-   Le masquage du `My` modèle d’élément extension dans le **ajouter un élément** boîte de dialogue afin qu’il n’est pas inclus dans la liste des éléments de projet.  
  
 Cette rubrique explique comment empaqueter une personnalisée `My` extension en tant que modèle d’élément caché pouvant être gérés à partir de la **Extensions My** page du Concepteur de projets Visual Basic. Personnalisé `My` extension peut également être ajoutée automatiquement lorsqu’une référence à un assembly spécifié est ajoutée à un projet.  
  
## <a name="create-a-my-namespace-extension"></a>Créer une extension de l’espace de noms My  
 La première étape de création d’un package de déploiement personnalisé `My` extension consiste à créer l’extension comme un fichier de code unique. Pour plus d’informations et des conseils sur la création d’un personnalisé `My` extension, consultez [étendre le Namespace My dans Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).  
  
## <a name="export-a-my-namespace-extension-as-an-item-template"></a>Exporter une extension de l’espace de noms My comme un modèle d’élément  
 Une fois que vous disposez d’un fichier de code qui inclut votre `My` extension de l’espace de noms, vous pouvez exporter le fichier de code comme un modèle d’élément Visual Studio. Pour obtenir des instructions sur l’exportation d’un fichier comme un modèle d’élément Visual Studio, consultez [Comment : créer des modèles d’élément](/visualstudio/ide/how-to-create-item-templates).  
  
> [!NOTE]
>  Si votre `My` extension de l’espace de noms a une dépendance sur un assembly particulier, vous pouvez personnaliser votre modèle d’élément pour installer automatiquement votre `My` extension d’espace de noms lors de l’ajout d’une référence à cet assembly. Par conséquent, vous devez exclure cette référence d’assembly lorsque vous exportez le fichier de code comme un modèle d’élément Visual Studio.  
  
## <a name="customize-the-item-template"></a>Personnaliser le modèle d’élément  
 Vous pouvez activer votre modèle d’élément à partir de la **Extensions My** page du Concepteur de projets Visual Basic. Vous pouvez également activer le modèle d’élément à ajouter automatiquement lorsqu’une référence à un assembly spécifié est ajoutée à un projet. Pour activer ces personnalisations, vous serez ajouter un nouveau fichier, appelé le fichier CustomData, à votre modèle et puis ajoutez un nouvel élément au XML dans votre fichier .vstemplate.  
  
### <a name="add-the-customdata-file"></a>Ajouter le fichier CustomData  
 Le fichier CustomData est un fichier texte qui a l’extension de nom de fichier. CustomData (le nom de fichier vous pouvez définir une valeur explicite pour votre modèle) et qui contient du code XML. Le XML du fichier CustomData demande à Visual Basic d’inclure votre `My` extension lorsque les utilisateurs utilisent le **Extensions My** page du Concepteur de projets Visual Basic. Vous pouvez éventuellement ajouter le <`AssemblyFullName>` d’attribut à votre fichier XML CustomData. Cela fait en sorte que Visual Basic pour installer automatiquement votre personnalisé `My` extension lorsqu’une référence à un assembly particulier est ajoutée au projet. Vous pouvez utiliser n’importe quel éditeur de texte ou un éditeur XML pour créer le fichier CustomData et puis l’ajouter au dossier de votre modèle d’élément compressé (fichier .zip).  
  
 Par exemple, le code XML suivant montre le contenu d’un fichier CustomData qui ajoute l’élément de modèle dans le dossier Extensions My d’un projet Visual Basic lorsqu’une référence à l’assembly Microsoft.VisualBasic.PowerPacks.Vs.dll est ajouté au projet.  
  
```xml  
<VBMyExtensionTemplate   
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"   
    Version="1.0.0.0"  
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"  
/>  
```  
  
 Le fichier CustomData contient un <`VBMyExtensionTemplate>` élément qui possède les attributs comme indiqué dans le tableau suivant.  
  
|Attribut|Description|  
|---|---|  
|`ID`|Obligatoire. Identificateur unique pour l’extension. Si l’extension qui possède cet ID a déjà été ajoutée au projet, l’utilisateur ne sera pas invité à ajouter à nouveau.|  
|`Version`|Obligatoire. Un numéro de version du modèle d’élément.|  
|`AssemblyFullName`|Facultatif. Nom d'assembly Lorsqu’une référence à cet assembly est ajoutée au projet, l’utilisateur sera invité à ajouter le `My` extension à partir de ce modèle d’élément.|  
  
### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a>Ajouter le \<CustomDataSignature > élément dans le fichier .vstemplate  
 Pour identifier votre modèle d’élément Visual Studio en tant qu’un `My` extension de l’espace de noms, vous devez également modifier le fichier .vstemplate pour votre modèle d’élément. Vous devez ajouter un `<CustomDataSignature>` élément à la `<TemplateData>` élément. Le `<CustomDataSignature>` élément doit contenir le texte `Microsoft.VisualBasic.MyExtension`, comme illustré dans l’exemple suivant.  
  
```xml  
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>  
```  
  
 Vous ne pouvez pas modifier directement les fichiers dans un dossier compressé (fichier .zip). Vous devez copier le fichier .vstemplate à partir du dossier compressé, le modifier et puis remplacez le fichier .vstemplate dans le dossier compressé par votre copie mise à jour.  
  
 L’exemple suivant montre le contenu d’un fichier .vstemplate a la `<CustomDataSignature>` élément ajouté.  
  
```xml  
<VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">  
  <TemplateData>  
    <DefaultName>MyCustomExtensionModule.vb</DefaultName>  
    <Name>MyPrinterInfo</Name>  
    <Description>Custom My Extensions Item Template</Description>  
    <ProjectType>VisualBasic</ProjectType>  
    <SortOrder>10</SortOrder>  
    <Icon>__TemplateIcon.ico</Icon>  
    <CustomDataSignature      >Microsoft.VisualBasic.MyExtension</CustomDataSignature>  
  </TemplateData>  
  <TemplateContent>  
    <References />  
    <ProjectItem SubType="Code"   
                 TargetFileName="$fileinputname$.vb"  
                 ReplaceParameters="true"  
     >MyCustomExtensionModule.vb</ProjectItem>  
  </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="install-the-template"></a>Installer le modèle  
 Pour installer le modèle, vous pouvez copier le dossier compressé (fichier .zip) dans le dossier de modèles d’élément Visual Basic (par exemple, Mes Documents\Visual Studio 2008\Templates\Item Templates\Visual Basic). Vous pouvez également publier le modèle dans un fichier de programme d’installation de Visual Studio (.vsi).  
  
## <a name="see-also"></a>Voir aussi  
 [Étendre la My Namespace en Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)  
 [Extension du modèle d’application Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)  
 [Personnalisation de la disponibilité ou non des objets dans My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)  
 [Extensions My, Page du Concepteur de projets](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
