---
title: "Exemple de compensation personnalis&#233;e | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 385920da-9284-44bf-9fe9-0d87c7478ec5
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# Exemple de compensation personnalis&#233;e
Cet exemple montre comment utiliser <xref:System.Activities.Statements.CompensableActivity> et son gestionnaire de compensation pour définir une logique de compensation personnalisée.Le scénario modélisé de cet exemple est une agence de location de camions.  
  
## Détails de l'exemple  
 Les étapes simulées sont les suivantes :  
  
1.  L'utilisateur demande des devis de location de camion pour une date donnée.  
  
2.  Trois sociétés de camions sont contactées et les trois devis sont fournis.  
  
3.  L'utilisateur sélectionne un devis pour un camion et effectue la commande par carte de crédit.  
  
4.  L'application annule les deux autres devis de camion.  
  
5.  L'application facture des frais de service qui ne sont pas remboursables pour les comptes non Premium en cas d'annulation 10 jours ou moins avant la date de réservation.  
  
6.  L'application facture le prix de location du camion.  
  
7.  L'application attend jusqu'à la date de réservation ou jusqu'à ce que le client ait décidé d'annuler la réservation, selon ce qui se produit en premier.  
  
8.  Si le client annule la réservation, la logique de compensation personnalisée <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> s'exécute d'après la logique suivante :  
  
    1.  Si le client dispose d'un compte non Premium et qu'il reste moins que 10 jours avant la date de réservation, les frais de service restent facturés ; sinon, l'application rembourse les frais de service.  
  
    2.  Le reste des activités compensables \(commande de camion \+ frais de commande du camion\) sont exécutées d'après la logique de compensation par défaut, laquelle consiste à compenser dans l'ordre inverse de l'exécution.  
  
#### Pour configurer, générer et exécuter l'exemple  
  
1.  À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez la solution CustomCompensation.sln.Elle se trouve dans le répertoire \\WF\\Basic\\Compensation\\CustomCompensation.  
  
2.  Appuyez sur Ctrl\+Maj\+B pour générer la solution.  
  
3.  Appuyez sur CTRL\+F5 pour exécuter l'application.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\Compensation\CustomCompensation`  
  
## Voir aussi