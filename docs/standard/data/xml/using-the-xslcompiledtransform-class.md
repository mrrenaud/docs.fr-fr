---
title: Utilisation de la classe XslCompiledTransform
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f9b074f6-d6f4-49dd-a093-df510bf0cf7b
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a00ae5a2f54aee3d6ac16d0870f9171fe42ca289
ms.sourcegitcommit: 91691981897cf8451033cb01071d8f5d94017f97
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2018
---
# <a name="using-the-xslcompiledtransform-class"></a>Utilisation de la classe XslCompiledTransform
La classe <xref:System.Xml.Xsl.XslCompiledTransform> est le processeur XSLT dans Microsoft .NET Framework. Cette classe est utilisée pour compiler des feuilles de style et exécuter des transformations XSLT.  
  
> [!NOTE]
>  Bien que les performances globales de la classe <xref:System.Xml.Xsl.XslCompiledTransform> soient meilleures que celles de la classe <xref:System.Xml.Xsl.XslTransform>, la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> de la classe <xref:System.Xml.Xsl.XslCompiledTransform> peut s'exécuter plus lentement que la méthode <xref:System.Xml.Xsl.XslTransform.Load%2A> de la classe <xref:System.Xml.Xsl.XslTransform> la première fois qu'elle est appelée pour une transformation. C'est parce que le fichier XSLT doit être compilé avant d'être chargé. Pour plus d'informations, consultez le billet de blog suivant : [XslCompiledTransform plus lent que XslTransform ?](https://blogs.msdn.microsoft.com/antosha/2006/07/16/xslcompiledtransform-slower-than-xsltransform/).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Entrées dans la classe XslCompiledTransform](../../../../docs/standard/data/xml/inputs-to-the-xslcompiledtransform-class.md)  
 Décrit les options d'entrée XSLT disponibles.  
  
 [Options de sortie de la classe XslCompiledTransform](../../../../docs/standard/data/xml/output-options-on-the-xslcompiledtransform-class.md)  
 Décrit les options de sortie XSLT disponibles.  
  
 [Résolution de ressources externes lors du traitement XSLT](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)  
 Présente l'utilisation de la classe <xref:System.Xml.XmlResolver> pour résoudre des ressources externes.  
  
 [Extension des feuilles de style XSLT](../../../../docs/standard/data/xml/extending-xslt-style-sheets.md)  
 Présente la prise en charge des extensions XSLT.  
  
|||  
|-|-|  
|[Erreurs XSLT récupérables](../../../../docs/standard/data/xml/recoverable-xslt-errors.md)|Répertorie chaque comportement discrétionnaire autorisé par la recommandation du World Wide Web Consortium (W3C) sur XSLT 1.0 et décrit la façon dont ces comportements sont gérés par la classe <xref:System.Xml.Xsl.XslCompiledTransform>.|  
|[Guide pratique pour transformer un fragment de nœud](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md)|Décrit comment transformer un fragment de nœud.|  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Migration depuis la classe XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 Explique comment migrer du code à partir de la classe <xref:System.Xml.Xsl.XslTransform>  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Xml.Xsl.XsltSettings>  
 <xref:System.Xml.Xsl.XsltMessageEncounteredEventArgs>
