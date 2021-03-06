---
title: Interrogation de DataSets (LINQ to DataSet)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 21c4b2a37dfc9a7c570b39fa164267f90fa7055d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="querying-datasets-linq-to-dataset"></a>Interrogation de DataSets (LINQ to DataSet)
Une fois qu'un objet <xref:System.Data.DataSet> a été rempli avec des données, vous pouvez commencer de l'interroger. La formulation de requêtes avec [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] est semblable à l'utilisation de [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] sur d'autres sources de données [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]. N’oubliez pas, toutefois, que lorsque vous utilisez [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] des requêtes sur un <xref:System.Data.DataSet> objet que vous interrogez une énumération de <xref:System.Data.DataRow> des objets, au lieu d’une énumération d’un type personnalisé. Cela signifie que vous pouvez utiliser un des membres de la <xref:System.Data.DataRow> classe dans votre [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] des requêtes. Vous pouvez ainsi créer des requêtes riches et complexes.  
  
 Comme avec d’autres implémentations de [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], vous pouvez créer [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] requêtes sous deux formes différentes : syntaxe d’expression et la syntaxe de requête fondée sur une méthode de requête. Pour plus d’informations sur ces deux formes, consultez [mise en route de LINQ](http://msdn.microsoft.com/library/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9). Vous pouvez utiliser une syntaxe d'expression de requête ou une syntaxe de requête fondée sur une méthode sur des tables uniques d'un <xref:System.Data.DataSet>, sur plusieurs tables sur un <xref:System.Data.DataSet>, ou sur les tables d'un <xref:System.Data.DataSet> typé.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Requêtes de table unique](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 Explique comment exécuter des requêtes d'analyse unique.  
  
 [Requêtes de table croisée](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 Explique comment exécuter des requêtes d'analyse croisée.  
  
 [Interrogation de DataSets typés](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 Explique comment interroger des objets <xref:System.Data.DataSet> typés.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [Chargement de données dans un DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
