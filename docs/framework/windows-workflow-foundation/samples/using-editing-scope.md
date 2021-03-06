---
title: "Utilisation de la portée d'édition"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 79306f9e-318b-4687-9863-8b93d1841716
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d6f20ff0577e43106886f5910b8f6a69578d1b3e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="using-editing-scope"></a>Utilisation de la portée d'édition
Cet exemple montre comment traiter par lot un ensemble de modifications afin qu'elles puissent être annulées dans une unité atomique unique. Par défaut, les actions effectuées par un auteur de concepteur d'activités sont automatiquement intégrées dans le système d'annulation/de rétablissement.  
  
## <a name="demonstrates"></a>Démonstrations  
 Portée d'édition et annulation/rétablissement.  
  
## <a name="discussion"></a>Discussion  
 Cet exemple montre comment traiter par lot un ensemble de modifications apportées à l'arborescence <xref:System.Activities.Presentation.Model.ModelItem> dans une unité de travail unique. Notez que, lors de la liaison à des valeurs <xref:System.Activities.Presentation.Model.ModelItem> directement à partir d'un concepteur WPF, les modifications sont appliquées automatiquement. Cet exemple montre ce qui doit être fait lorsque plusieurs modifications qui doivent être traitées par lot sont apportées via du code impératif, plutôt que par une modification unique.  
  
 Dans cet exemple, trois activités sont ajoutées. Lorsque la modification commence, <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> est appelé sur une instance de <xref:System.Activities.Presentation.Model.ModelItem>. Les modifications apportées à l'arborescence <xref:System.Activities.Presentation.Model.ModelItem> dans cette portée d'édition sont traitées par lot. La commande <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> retourne un <xref:System.Activities.Presentation.Model.EditingScope>, qui peut être utilisé pour contrôler cette instance. <xref:System.Activities.Presentation.Model.EditingScope.OnComplete%2A> ou <xref:System.Activities.Presentation.Model.EditingScope.OnRevert%2A> peut être appelé pour valider ou rétablir la portée d'édition.  
  
 Vous pouvez également imbriquer des objets <xref:System.Activities.Presentation.Model.EditingScope>, ce qui permet de suivre de plusieurs ensembles de modifications dans le cadre d'une plus grande portée d'édition et de les contrôler individuellement. Un scénario qui peut utiliser cette fonctionnalité consisterait en des modifications apportées dans plusieurs boîtes de dialogue qui doivent être validées ou rétablies séparément, avec toutes les modifications traitées en tant qu'opération atomique unique. Dans cet exemple, les portées d'édition sont empilées à l'aide d'un <xref:System.Collections.ObjectModel.ObservableCollection%601> de type <xref:System.Activities.Presentation.Model.ModelEditingScope>. <xref:System.Collections.ObjectModel.ObservableCollection%601> est utilisé afin que la profondeur de l'imbrication puisse être observée sur l'aire du concepteur.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Générez et exécutez l'exemple, puis utilisez les boutons situés à gauche pour modifier le workflow.  
  
2.  Cliquez sur **ouvrir la portée d’édition**.  
  
    1.  Cette commande appelle <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> qui crée une portée d'édition et le place sur la pile d'édition.  
  
    2.  Trois activités sont ensuite ajoutées au <xref:System.Activities.Presentation.Model.ModelItem> sélectionné. Notez que si la portée d'édition n'avait pas été ouverte avec <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A>, trois nouvelles activités apparaitraient sur la zone de conception. Étant donné que cette opération est toujours en attente dans <xref:System.Activities.Presentation.Model.EditingScope>, le concepteur n'est pas encore mis à jour.  
  
3.  Appuyez sur **fermer la portée d’édition** pour valider la portée d’édition. Trois activités apparaissent dans le concepteur.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\UsingEditingScope`
