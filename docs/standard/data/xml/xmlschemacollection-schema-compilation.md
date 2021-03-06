---
title: "Compilation de schéma XmlSchemaCollection"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 76f28770-7126-428f-9ed5-7b5ae8bad5ee
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c891736534741d1d3d3edb93d75d9f191c2dd573
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="xmlschemacollection-schema-compilation"></a>Compilation de schéma XmlSchemaCollection
La classe **XmlSchemaCollection** est un cache ou une bibliothèque où des schémas XDR (XML-Data Reduced) et des schémas de langage XSD (XML Schema Definition) peuvent être stockés et validés. **XmlSchemaCollection** améliore les performances en mettant les schémas en cache au lieu d'y accéder à partir d'un fichier ou d'une URL.  
  
> [!NOTE]
>  Bien que la classe **XmlSchemaCollection** contienne à la fois des schémas XDR et des schémas XML, toute méthode ou propriété qui prend ou retourne un objet **XmlSchema** ne prend en charge que les schémas XML.  
  
> [!IMPORTANT]
>  La classe <xref:System.Xml.Schema.XmlSchemaCollection> est désormais obsolète et a été remplacée par la classe <xref:System.Xml.Schema.XmlSchemaSet>. Pour plus d’informations sur la classe <xref:System.Xml.Schema.XmlSchemaSet>, consultez [XmlSchemaSet pour la compilation de schémas](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).  
  
## <a name="add-schemas-to-the-collection"></a>Ajout de schémas à la collection  
 Les schémas sont chargés dans la collection à l’aide de la méthode **Add** de la collection **XmlSchemaCollection**. C’est à ce moment-là que le schéma est associé à un URI d’espace de noms. Pour les schémas XML, l'URI d'espace de noms correspond généralement à l'espace de noms cible du schéma. Pour les schémas XDR, l'URI d'espace de noms correspond à l'espace de noms spécifié lors de l'ajout du schéma à la collection.  
  
## <a name="check-for-a-schema-in-the-collection"></a>Recherche d’un schéma dans la collection  
 Vous pouvez vérifier si un schéma se trouve dans la collection à l’aide de la méthode **Contains**. La méthode **Contains** prend soit un objet **XmlSchema** (schémas XML uniquement), soit une chaîne qui représente l'URI d'espace de noms associé au schéma (schémas XDR et schémas XML).  
  
## <a name="retrieve-a-schema-from-the-collection"></a>Extraction d’un schéma à partir de la collection  
 Vous pouvez extraire un schéma à partir de la collection à l’aide de la propriété **Item**. La propriété **Item** prend une chaîne qui représente l'URI d'espace de noms associé au schéma, généralement son espace de noms cible, et retourne un objet **XmlSchema**. La propriété **Item** s'applique uniquement aux schémas XML. La valeur de retour est toujours une référence null pour les schémas XDR car ils n'ont pas de modèle objet disponible.  
  
## <a name="validate-xml-documents-using-xmlschemacollection"></a>Validation des documents XML à l'aide de XmlSchemaCollection  
 Vous pouvez valider un document d’instance XML à l’aide de **XmlSchemaCollection** en créant l’objet **XmlSchemaCollection**, en ajoutant vos schémas à la collection et en définissant la propriété **Schemas** sur **XmlValidatingReader** pour assigner **XmlSchemaCollection** créé à **XmlValidatingReader**.  
  
### <a name="improved-performance"></a>Performances améliorées  
 Si vous procédez à la validation de plusieurs documents par rapport au même schéma, il est recommandé d'utiliser **XmlSchemaCollection** car elle offre de meilleures performances grâce à la mise en cache des schémas.  
  
 L’exemple de code suivant crée l’objet **XmlSchemaCollection**, ajoute des schémas à la collection et définit la propriété **Schemas**.  
  
```vb  
Dim tr as XmlTextReader = new XmlTextReader("Books.xml")  
Dim vr as XmlValidatingReader = new XmlValidatingReader(tr)  
Dim xsc as XmlSchemaCollection = new XmlSchemaCollection  
xsc.Add("urn:bookstore-schema", "Books.xsd")  
vr.Schemas.Add(xsc)  
```  
  
```csharp  
XmlTextReader tr = new XmlTextReader("Books.xml");  
XmlValidatingReader vr = new XmlValidatingReader(tr);  
XmlSchemaCollection xsc = new XmlSchemaCollection();  
xsc.Add("urn:bookstore-schema", "Books.xsd");    
vr.Schemas.Add(xsc);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Validation XDR avec XmlSchemaCollection](../../../../docs/standard/data/xml/xdr-validation-with-xmlschemacollection.md)  
 [Validation de schéma XML (XSD) avec XmlSchemaCollection](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemacollection.md)
