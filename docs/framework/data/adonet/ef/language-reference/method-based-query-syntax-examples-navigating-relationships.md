---
title: "Exemples de syntaxe de requ&#234;te fond&#233;e sur une m&#233;thode&#160;: exploration de relations | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: a0bfa4b1-99e5-4dd1-9912-4b825a9dc25c
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Exemples de syntaxe de requ&#234;te fond&#233;e sur une m&#233;thode&#160;: exploration de relations
Les propriétés de navigation dans [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] sont des propriétés de raccourci utilisées pour rechercher les entités situées aux terminaisons d'une association.  Les propriétés de navigation permettent à un utilisateur de naviguer d'une entité à une autre ou d'une entité à des entités associées par le biais d'un ensemble d'associations.  Cette rubrique fournit des exemples de syntaxe de requête fondée sur une méthode relatifs à la façon d'explorer des relations au moyen de propriétés de navigation dans des requêtes [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].  
  
 Le modèle de vente AdventureWorks Sales Model utilisé dans ces exemples est construit à partir des tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.  
  
 Les exemples de cette rubrique utilisent les instructions `using`\/`Imports` suivantes :  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## Exemple  
 L'exemple suivant de syntaxe de requête fondée sur une méthode utilise la méthode <xref:System.Linq.Queryable.SelectMany%2A> pour obtenir toutes les commandes des contacts dont le nom de famille est « Zhou ».  La propriété de navigation `Contact.SalesOrderHeader` est utilisée pour obtenir la collection des objets `SalesOrderHeader` de chaque contact.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders_mq)]  
  
## Exemple  
 L'exemple suivant de syntaxe de requête fondée sur une méthode utilise la méthode <xref:System.Linq.Queryable.Select%2A> pour obtenir tous les ID de contact et la somme du montant total dû pour chaque contact dont le nom est « Zhou ».  La propriété de navigation `Contact.SalesOrderHeader` est utilisée pour obtenir la collection des objets `SalesOrderHeader` de chaque contact.  La méthode `Sum` utilise la propriété de navigation `Contact.SalesOrderHeader` pour calculer la somme du montant total dû pour l'ensemble des commandes de chaque contact.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2_mq)]  
  
## Exemple  
 L'exemple suivant de syntaxe de requête fondée sur une méthode obtient toutes les commandes des contacts dont le nom de famille est « Zhou ».  La propriété de navigation `Contact.SalesOrderHeader` est utilisée pour obtenir la collection des objets `SalesOrderHeader` de chaque contact.  Le nom et les commandes du contact sont retournés dans un type anonyme.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3_mq)]  
  
## Exemple  
 L'exemple ci\-dessous utilise les propriétés de navigation `SalesOrderHeader.Address` et `SalesOrderHeader.Contact` pour obtenir la collection des objets `Address` et `Contact` associés à chaque commande.  Le nom du contact, l'adresse, le numéro de commande et le montant total dû de chaque commande pour la ville de Seattle sont retournés dans un type anonyme.  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships_mq)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships_mq)]  
  
## Exemple  
 L'exemple ci\-dessous utilise la méthode `Where` pour rechercher des commandes qui ont été passées après le 1er décembre 2003, puis utilise la propriété de navigation `order.SalesOrderDetail` pour obtenir les détails de chaque commande.  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## Voir aussi  
 [Navigation Properties](http://msdn.microsoft.com/fr-fr/41e1e6b9-8a57-467d-99d9-1857d2ca2ea5)   
 [Requêtes dans LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)