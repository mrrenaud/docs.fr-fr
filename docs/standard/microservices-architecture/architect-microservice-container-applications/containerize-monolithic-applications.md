---
title: "Mise en conteneur d’applications monolithiques"
description: "Architecture de microservices .NET pour les applications .NET en conteneur | Mise en conteneur d’applications monolithiques"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fc01054e4352a711d2203e694001a1204dedadf9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="containerizing-monolithic-applications"></a>Mise en conteneur d’applications monolithiques

Vous pouvez créer une application ou un service web simple, déployé de façon monolithique, et le déployer en tant que conteneur. L’application elle-même peut ne pas être monolithique en interne, mais structurée sous la forme de plusieurs bibliothèques, de plusieurs composants ou même de plusieurs couches (couche d’application, couche de domaine, couche d’accès aux données, etc.). En externe cependant, il s’agit d’un seul conteneur : un seul processus, une seule application web ou un seul service.

Pour gérer ce modèle, vous déployez un seul conteneur pour représenter l’application. Pour le faire monter en charge, vous ajoutez simplement d’autres copies avec un équilibreur de charge en frontal. Cette simplicité provient de la gestion d’un seul déploiement dans un seul conteneur ou une seule machine virtuelle.

![](./media/image1.png)

**Figure 4-1**. Exemple d’architecture d’une application monolithique en conteneur

Vous pouvez inclure plusieurs composants, bibliothèques ou couches internes dans chaque conteneur, comme illustré dans la figure 4-1. Cependant, ce modèle monolithique peut être en conflit avec le principe des conteneurs, selon lequel « un conteneur fait une chose et la fait dans un seul processus » ; il peut cependant convenir dans certains cas.

L’inconvénient de cette approche devient évident si l’application grandit, nécessitant sa mise à l’échelle. Si l’ensemble de l’application peut être mis à l’échelle, ce n’est pas réellement un problème. Cependant, dans la plupart des cas, seules quelques parties de l’application sont des goulots d’étranglement qui nécessitent une mise à l’échelle, tandis que d’autres composants sont moins utilisés.

Par exemple, dans une application de e-commerce classique, il est probablement nécessaire de mettre à l’échelle le sous-système des informations sur les produits, car bien plus de clients les parcourent que ceux qui les achètent. Plus de clients utilisent leur panier d’achat que ceux qui utilisent le pipeline de paiement. Moins de clients ajoutent des commentaires ou consultent leur historique d’achat. De même, seule une poignée d’employés doivent gérer le contenu et les campagnes marketing. Si vous mettez à l’échelle la conception monolithique, tout le code pour ces différentes tâches est déployé plusieurs fois et est mis à l’échelle au même niveau.

Il existe plusieurs façons de mettre à l’échelle une application : déduplication horizontale, fractionnement des différentes zones de l’application et partitionnement des concepts ou des données métier similaires. Toutefois, en plus du problème de mise à l’échelle de tous les composants, les modifications apportées à un seul composant nécessitent un nouveau test complet de l’application entière, ainsi qu’un redéploiement complet de toutes les instances.

L’approche monolithique est cependant courante, étant donné que le développement de l’application est initialement plus facile que pour les approches avec des microservices. Par conséquent, de nombreuses organisations font des développements avec cette approche architecturale. Si certaines organisations ont obtenu des résultats suffisamment bons, d’autres en ont atteint les limites. De nombreuses organisations ont conçu leurs applications en utilisant ce modèle, car il y a quelques années, les outils et l’infrastructure rendaient trop difficiles la création d’architectures orientées service et, jusqu’à ce que l’application grandisse, elles n’en voyaient pas le besoin.

Du point de vue de l’infrastructure, chaque serveur peut exécuter de nombreuses applications dans le même hôte et avoir un ratio acceptable d’efficacité de l’utilisation des ressources, comme le montre la figure 4-2.

![](./media/image2.png)

**Figure 4-2**. Approche monolithique : hôte exécutant plusieurs applications, chaque application s’exécutant en tant que conteneur

Les applications monolithiques dans Microsoft Azure peuvent être déployées en utilisant des machines virtuelles dédiées pour chaque instance. De plus, avec [Azure VM Scale Sets](https://docs.microsoft.com/azure/virtual-machine-scale-sets/), vous pouvez facilement mettre à l’échelle les machines virtuelles. [Azure App Service](https://azure.microsoft.com/services/app-service/) peut également exécuter des applications monolithiques et facilement mettre à l’échelle des instances sans nécessiter la gestion des machines virtuelles. Depuis 2016, Azure App Service peut également exécuter des instances uniques de conteneurs Docker, ce qui simplifie le déploiement.

Dans un environnement d’assurance qualité ou un environnement de production limité, vous pouvez déployer plusieurs machines virtuelles hôtes de Docker et les équilibrer avec l’équilibreur de charge d’Azure, comme le montre la figure 4-3. Ceci vous permet de gérer la mise à l’échelle avec une approche plus approximative, car la totalité de l’application se trouve dans un même conteneur.

![](./media/image3.png)

**Figure 4-3**. Exemple de plusieurs hôtes effectuant la montée en charge d’une application dans un seul conteneur

Le déploiement sur les différents hôtes peut être géré avec les techniques de déploiement traditionnelles. Les hôtes Docker peuvent être gérés avec des commandes comme `docker run` ou `docker-compose`, effectuées manuellement ou via une automatisation, comme des pipelines de livraison continue.

## <a name="deploying-a-monolithic-application-as-a-container"></a>Déploiement d’une application monolithique en tant que conteneur

L’utilisation de conteneurs pour gérer les déploiements d’applications monolithiques présente des avantages. La mise à l’échelle les instances de conteneur est beaucoup plus rapide et facile que le déploiement de machines virtuelles supplémentaires. Même si vous utilisez des groupes de machines virtuelles identiques, les machines virtuelles prennent du temps pour démarrer. Dans le cas d’un déploiement comme instances d’application traditionnelles au lieu de conteneurs, la configuration de l’application est gérée dans le cadre de la machine virtuelle, ce qui n’est pas idéal.

Le déploiement de mises à jour comme images Docker est beaucoup plus rapide et efficace du point de vue du réseau. Les images Docker démarrent généralement en quelques secondes, ce qui accélère les lancements. La destruction d’une instance d’image Docker se fait simplement en lançant une commande `docker stop` ; cette opération prend généralement moins d’une seconde.

Comme les conteneurs sont immuables par conception, vous ne devez jamais vous inquiéter des machines virtuelles endommagées. En revanche, les scripts de mise à jour pour une machine virtuelle risquent d’omettre de prendre en compte une configuration ou un fichier spécifique restant sur le disque.

Alors que les applications monolithiques peuvent tirer parti de Docker, nous n’en évoquons que les avantages. D’autres avantages de la gestion de conteneurs proviennent du déploiement avec des orchestrateurs de conteneurs, qui gèrent les différentes instances et le cycle de vie de chaque instance de conteneur. La décomposition de l’application monolithique en sous-systèmes qui peuvent être mis à l’échelle, développés et déployés individuellement est votre point d’entrée dans le domaine des microservices.

## <a name="publishing-a-single-container-based-application-to-azure-app-service"></a>Publication d’une application basée sur un seul conteneur sur Azure App Service

Que vous vouliez obtenir la validation d’un conteneur déployé sur Azure ou quand une application est simplement une application avec un seul conteneur, Azure App Service offre un excellent moyen de fournir des services évolutifs basés sur un seul conteneur. L’utilisation d’Azure App Service est simple. Il fournit une intégration étroite avec Git qui permet de prendre facilement votre code, de générer l’application correspondante dans Visual Studio et de la déployer directement sur Azure.

![](./media/image4.png)

**Figure 4-4**. Publication d’une application basée sur un seul conteneur sur Azure App Service à partir de Visual Studio

Sans Docker, si vous aviez besoin d’autres fonctionnalités, frameworks ou dépendances qui ne sont pas pris en charge dans Azure App Service, vous deviez attendre que l’équipe Azure mette à jour ces dépendances dans App Service. Vous pouviez aussi passer à d’autres services, comme Azure Service Fabric, Azure Cloud Services ou même des machines virtuelles, où vous aviez davantage de contrôle et où vous pouviez installer un composant ou un framework nécessaire à votre application.

La prise en charge des conteneurs dans Visual Studio 2017 vous donne la possibilité d’inclure tout ce que vous voulez dans l’environnement de votre application, comme le montre la figure 4-4. Étant donné que vous l’exécutez dans un conteneur, si vous ajoutez une dépendance à votre application, vous pouvez inclure la dépendance dans votre fichier Dockerfile ou dans votre image Docker.

Comme le montre la figure 4-4, le flux de publication pousse (push) une image via un registre de conteneurs. Il peut s’agir d’Azure Container Registry (registre proche de vos déploiements dans Azure, et sécurisé par des comptes et des groupes Azure Active Directory), ou de tout autre registre Docker, comme Docker Hub ou un registre local.


>[!div class="step-by-step"]
[Précédent] (index.md) [Suivant] (docker-application-state-data.md)
