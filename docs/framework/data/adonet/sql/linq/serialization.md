---
title: "S&#233;rialisation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a15ae411-8dc2-4ca3-84d2-01c9d5f1972a
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# S&#233;rialisation
Cette rubrique décrit les fonctions de sérialisation de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  Les paragraphes qui suivent fournissent des informations sur l'ajout de la sérialisation pendant la génération de code au moment du design et le comportement de sérialisation à l'exécution de classes [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 Vous pouvez ajouter du code de sérialisation au moment du design selon l'un des méthodes suivantes :  
  
-   Dans le [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)], affectez la valeur **Unidirectional** à la propriété **Serialization Mode**.  
  
-   Sur la ligne de commande SQLMetal, ajoutez l'option **\/serialization**.  Pour plus d'informations, consultez [SqlMetal.exe \(outil de génération de code\)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## Vue d'ensemble  
 Le code généré par [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fournit des fonctions de chargement différé par défaut.  Le chargement différé est très utile au niveau intermédiaire pour le chargement transparent de données à la demande.  Il pose toutefois problème pour la sérialisation car le sérialiseur déclenche un chargement différé, qu'il soit voulu ou non.  En effet, lorsqu'un objet est sérialisé, sa fermeture transitive dans toutes les références à chargement différé en sortie est sérialisée.  
  
 La fonctionnalité de sérialisation de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] traite ce problème, principalement par le biais de deux mécanismes :  
  
-   Un mode <xref:System.Data.Linq.DataContext> pour désactiver le chargement différé \(<xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A>\).  Pour plus d'informations, consultez <xref:System.Data.Linq.DataContext>.  
  
-   Un commutateur de génération de code pour générer des attributs <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=fullName> et <xref:System.Runtime.Serialization.DataMemberAttribute?displayProperty=fullName> sur les entités générées.  Cet aspect, y compris le comportement de chargement différé des classes lors de la sérialisation, est le principal objet de cette rubrique.  
  
### Définitions  
  
-   *Sérialiseur DataContract* : sérialiseur par défaut utilisé par le composant Windows Communication Framework \(WCF\) du .NET Framework 3.0 ou versions ultérieures.  
  
-   *Sérialisation unidirectionnelle* :version sérialisée d'une classe qui contient uniquement une propriété d'association unidirectionnelle \(pour éviter un cycle\).  Par convention, la propriété sur le côté parent d'une relation de clé primaire\-étrangère est marquée pour sérialisation.  L'autre côté d'une association bidirectionnelle n'est pas sérialisé.  
  
     La sérialisation unidirectionnelle est le seul type de sérialisation pris en charge par [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
## Exemple de code  
 Le code suivant utilise les classes `Customer` et `Order` standard de l'exemple de base de données Northwind et montre comment ces classes sont décorées avec les attributs de sérialisation.  
  
 [!code-csharp[DLinqSerialization#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#1)]
 [!code-vb[DLinqSerialization#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#1)]  
  
 [!code-csharp[DLinqSerialization#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#2)]
 [!code-vb[DLinqSerialization#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#2)]  
  
 [!code-csharp[DLinqSerialization#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#3)]
 [!code-vb[DLinqSerialization#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#3)]  
  
 Pour la classe `Order` de l'exemple suivant, seule la propriété d'association inverse correspondant à la classe `Customer` est montrée, par souci de concision.  Elle n'a pas d'attribut `DataMember` pour éviter un cycle.  
  
 [!code-csharp[DLinqSerialization#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#4)]
 [!code-vb[DLinqSerialization#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#4)]  
  
 [!code-csharp[DLinqSerialization#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#5)]
 [!code-vb[DLinqSerialization#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#5)]  
  
### Comment sérialiser les entités  
 Vous pouvez sérialiser les entités dans les codes présentés dans la section précédente \(voir ci\-dessous\).  
  
 [!code-csharp[DLinqSerialization#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/Program.cs#6)]
 [!code-vb[DLinqSerialization#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/Module1.vb#6)]  
  
### Relations auto\-récursives  
 Les relations auto\-récursives suivent le même modèle.  La propriété d'association qui correspond à la clé étrangère n'a pas d'attribut `DataMember`, contrairement à la propriété parente.  
  
 Observez la classe suivante, qui présente deux relations auto\-récursives : Employee.Manager\/Reports et Employee.Mentor\/Mentees.  
  
 [!code-csharp[DLinqSerialization#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#7)]
 [!code-vb[DLinqSerialization#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#7)]  
  
## Voir aussi  
 [Informations générales](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)   
 [SqlMetal.exe \(outil de génération de code\)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)   
 [Procédure : rendre les entités sérialisables](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md)