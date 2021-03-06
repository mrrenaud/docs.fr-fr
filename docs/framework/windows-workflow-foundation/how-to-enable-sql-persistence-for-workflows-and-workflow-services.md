---
title: "Procédure : activer la persistance SQL pour les workflows et les services de workflow"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ca7bf77f-3e5d-4b23-b17a-d0b60f46411d
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 60fac3cba4da35b5146f777abd912ad15f0f29eb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-sql-persistence-for-workflows-and-workflow-services"></a>Procédure : activer la persistance SQL pour les workflows et les services de workflow
Cette rubrique décrit comment configurer la fonctionnalité de magasin d’instances de workflow SQL pour activer la persistance pour vos workflows et services de workflow à la fois par programmation et en utilisant un fichier de configuration.  
  
 Windows Server AppFabric simplifie le processus de configuration de la persistance. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Configuration de persistance AppFabric](http://go.microsoft.com/fwlink/?LinkId=201204)  
  
 Avant d’utiliser la fonctionnalité de magasin d’instances de workflow SQL, créez une base de données que la fonctionnalité utilise pour rendre les instances de workflow persistantes. Le programme d'installation de [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] copie les fichiers de script SQL associés à la fonctionnalité de magasin d'instances de workflow SQL dans le dossier %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN. Exécutez ces fichiers de script sur une base de données SQL Server 2005 ou SQL Server 2008 que le magasin d'instances de workflow SQL doit utiliser pour rendre les instances de workflow persistantes. Exécutez d'abord le fichier SqlWorkflowInstanceStoreSchema.sql, puis le fichier SqlWorkflowInstanceStoreLogic.sql.  
  
> [!NOTE]
>  Pour nettoyer la base de données de persistance afin d'en avoir une nouvelle, exécutez les scripts dans %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN dans l'ordre suivant.  
>   
>  1.  SqlWorkflowInstanceStoreSchema.sql  
> 2.  SqlWorkflowInstanceStoreLogic.sql  
  
> [!IMPORTANT]
>  Si vous ne créez pas de base de données de persistance, la fonctionnalité de magasin d'instances de workflow SQL lève une exception semblable à la suivante lorsqu'un hôte essaie de rendre des workflows persistants.  
>   
>  System.Data.SqlClient.SqlException : Impossible de trouver la procédure stockée « System.Activities.DurableInstancing.CreateLockOwner »  
  
 Les sections suivantes décrivent comment activer la persistance pour les workflows et les services de workflow à l'aide du magasin d'instances de workflow SQL. [!INCLUDE[crabout](../../../includes/crabout-md.md)]Propriétés du magasin d’instances de Workflow SQL, consultez [propriétés du magasin d’Instance de Workflow SQL](../../../docs/framework/windows-workflow-foundation/properties-of-sql-workflow-instance-store.md).  
  
## <a name="enabling-persistence-for-self-hosted-workflows-that-use-workflowapplication"></a>Activation de la persistance pour les workflows auto-hébergés qui utilisent WorkflowApplication  
 Vous pouvez activer la persistance pour les workflows auto-hébergés qui utilisent <xref:System.Activities.WorkflowApplication> par programmation à l'aide du modèle d'objet <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>. La procédure suivante contient les étapes pour effectuer cette opération.  
  
#### <a name="to-enable-persistence-for-self-hosted-workflows"></a>Pour activer la persistance pour les workflows auto-hébergés  
  
1.  Ajoutez une référence à System.Activites.DurableInstancing.dll.  
  
2.  Ajoutez l'instruction suivante en haut du fichier source après les instructions « using » existantes.  
  
    ```csharp  
    using System.Activities.DurableInstancing;  
    ```  
  
3.  Construisez un <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> et affectez-le au <xref:System.Activities.WorkflowApplication.InstanceStore%2A> du <xref:System.Activities.WorkflowApplication>, comme illustré dans l'exemple de code suivant.  
  
    ```csharp  
    SqlWorkflowInstanceStore store =   
        new SqlWorkflowInstanceStore("Server=.\\SQLEXPRESS;Initial Catalog=Persistence;Integrated Security=SSPI");  
  
    WorkflowApplication wfApp =  
        new WorkflowApplication(new Workflow1());  
  
    wfApp.InstanceStore = store;  
    ```  
  
    > [!NOTE]
    >  Selon votre édition de SQL Server, le nom du serveur de chaîne de connexion peut être différent.  
  
4.  Appelez la méthode <xref:System.Activities.WorkflowApplication.Persist%2A> sur l'objet <xref:System.Activities.WorkflowApplication> pour rendre un workflow persistant ou la méthode <xref:System.Activities.WorkflowApplication.Unload%2A> pour rendre persistant et décharger un workflow. Vous pouvez également gérer l'événement <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> déclenché par l'objet <xref:System.Activities.WorkflowApplication> et retourner un membre approprié (<xref:System.Activities.PersistableIdleAction.Persist> ou <xref:System.Activities.PersistableIdleAction.Unload>) de <xref:System.Activities.PersistableIdleAction>.  
  
    ```csharp  
    wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)  
    {  
        return PersistableIdleAction.Persist;  
    };  
    ```  
  
> [!NOTE]
>  Consultez le [persistance d’une Application de Workflow](../../../docs/framework/windows-workflow-foundation/samples/persisting-a-workflow-application.md) sample à [persistance](../../../docs/framework/windows-workflow-foundation/samples/persistence.md) pour obtenir un exemple d’activation de la persistance pour les workflows à l’aide de la <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>et le [Comment : créer et exécuter un Long Flux de travail en cours d’exécution](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md) étape de la [Getting Started Tutorial](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) pour obtenir des instructions étape par étape.  
  
## <a name="enabling-persistence-for-self-hosted-workflow-services-that-use-the-workflowservicehost"></a>Activation de la persistance pour les services de workflow auto-hébergés qui utilisent WorkflowServiceHost  
 Vous pouvez activer la persistance pour les services de workflow auto-hébergés qui utilisent <xref:System.ServiceModel.WorkflowServiceHost> par programmation à l'aide de la classe <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> ou <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A>.  
  
### <a name="using-the-sqlworkflowinstancestorebehavior-class"></a>Utilisation de la classe SqlWorkflowInstanceStoreBehavior  
 La procédure suivante contient les étapes pour utiliser la classe <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> afin d'activer la persistance pour les services de workflow auto-hébergés.  
  
##### <a name="to-enable-persistence-using-sqlworkflowinstancestorebehavior"></a>Pour activer la persistance à l'aide de SqlWorkflowInstanceStoreBehavior  
  
1.  Ajoutez une référence à System.ServiceModel.dll.  
  
2.  Ajoutez l'instruction suivante en haut du fichier source après les instructions « using » existantes.  
  
    ```csharp  
    using System.ServiceModel.Activities.Description;  
    ```  
  
3.  Créez une instance du `WorkflowServiceHost` et ajoutez des points de terminaison pour le service de workflow.  
  
    ```  
    WorkflowServiceHost host = new WorkflowServiceHost(new CountingWorkflow(), new Uri(hostBaseAddress));  
    host.AddServiceEndpoint("ICountingWorkflow", new BasicHttpBinding(), "");  
    ```  
  
4.  Construisez un objet `SqlWorkflowInstanceStoreBehavior` et définissez les propriétés de l'objet de comportement.  
  
    ```csharp  
    SqlWorkflowInstanceStoreBehavior instanceStoreBehavior = new SqlWorkflowInstanceStoreBehavior(connectionString);  
    instanceStoreBehavior.HostLockRenewalPeriod = new TimeSpan(0, 0, 5);  
    instanceStoreBehavior.InstanceCompletionAction = InstanceCompletionAction.DeleteAll;  
    instanceStoreBehavior.InstanceLockedExceptionAction = InstanceLockedExceptionAction.AggressiveRetry;  
    instanceStoreBehavior.InstanceEncodingOption = InstanceEncodingOption.GZip;  
    instanceStoreBehavior.RunnableInstancesDetectionPeriod = new TimeSpan("00:00:02");  
    host.Description.Behaviors.Add(instanceStoreBehavior);  
    ```  
  
5.  Ouvrez l'hôte de service de workflow.  
  
    ```vb  
    host.Open();  
    ```  
  
> [!IMPORTANT]
>  Consultez le [Configuration intégrée](../../../docs/framework/windows-workflow-foundation/samples/built-in-configuration.md) sample à [persistance](../../../docs/framework/windows-workflow-foundation/samples/persistence.md) pour obtenir un exemple d’activation de la persistance pour les services de flux de travail à l’aide de la `SqlWorkflowInstanceStoreBehavior` classe.  
  
### <a name="using-the-durableinstancingoptions-property"></a>Utilisation de la propriété DurableInstancingOptions  
 Lorsque le `SqlWorkflowInstanceStoreBehavior` est appliqué, le `DurableInstancingOptions.InstanceStore` sur le `WorkflowServiceHost` a pour valeur l'objet `SqlWorkflowInstanceStore` créé à l'aide des valeurs de configuration. Vous pouvez effectuer la même opération par programmation pour définir la propriété <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> du `WorkflowServiceHost` sans utiliser la classe `SqlWorkflowInstanceStoreBehavior`, comme illustré dans l'exemple de code suivant.  
  
```  
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;  
```  
  
## <a name="enabling-persistence-for-was-hosted-workflow-services-that-use-the-workflowservicehost-using-a-configuration-file"></a>Activation de la persistance pour les services de workflow hébergés par le service d'activation de processus Windows qui utilisent WorkflowServiceHost à l'aide d'un fichier de configuration  
 Vous pouvez activer la persistance pour les services de workflow auto-hébergés ou hébergés par le service d'activation des processus Windows (WAS) à l'aide d'un fichier de configuration. Un service de workflow hébergé par le service d'activation de processus Windows utilise WorkflowServiceHost de la même façon que les services de workflow auto-hébergés.  
  
 Le `SqlWorkflowInstanceStoreBehavior`, un comportement de service qui vous permet de modifier aisément les [magasin d’instances de flux de travail de SQL](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md) propriétés via la configuration XML. Pour les services de workflow hébergés par le service d'activation de processus Windows, utilisez le fichier Web.config. L'exemple de configuration suivant indique comment configurer le magasin d'instances de workflow SQL en utilisant l'élément de comportement `sqlWorkflowInstanceStore` dans un fichier de configuration.  
  
```xml  
<serviceBehaviors>  
    <behavior name="">  
        <sqlWorkflowInstanceStore   
                    connectionString="Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true"  
                    instanceEncodingOption="GZip | None"  
                    instanceCompletionAction="DeleteAll | DeleteNothing"  
                    instanceLockedExceptionAction="NoRetry | BasicRetry |AggressiveRetry"  
                    hostLockRenewalPeriod="00:00:30"   
                    runnableInstancesDetectionPeriod="00:00:05">  
  
        <sqlWorkflowInstanceStore/>  
    </behavior>  
</serviceBehaviors>  
```  
  
 Si vous ne définissez pas de valeurs pour la propriété `connectionString` ou `connectionStringName`, le magasin d'instances de workflow SQL utilise la chaîne de connexion `DefaultSqlWorkflowInstanceStoreConnectionString` nommée par défaut.  
  
 Lorsque le `SqlWorkflowInstanceStoreBehavior` est appliqué, le `DurableInstancingOptions.InstanceStore` sur le `WorkflowServiceHost` a pour valeur l'objet `SqlWorkflowInstanceStore` créé à l'aide des valeurs de configuration. Vous pouvez effectuer la même opération par programmation pour utiliser le `SqlWorkflowInstanceStore` avec `WorkflowServiceHost` sans utiliser l'élément de comportement de service.  
  
```  
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;  
```  
  
> [!IMPORTANT]
>  Il est recommandé de ne pas stocker d'informations sensibles, telles que les noms d'utilisateur et mots de passe, dans le fichier Web.config. Si vous stockez des informations sensibles dans le fichier Web.config, vous devez sécuriser l'accès au fichier Web.config à l'aide des listes de contrôle d'accès (ACL) du système de fichiers. En outre, vous pouvez également sécuriser les valeurs de configuration dans un fichier de configuration comme indiqué dans [chiffrement Configuration des informations à l’aide de Configuration protégée](http://go.microsoft.com/fwlink/?LinkId=178419).  
  
### <a name="machineconfig-elements-related-to-the-sql-workflow-instance-store-feature"></a>Éléments Machine.config liés à la fonctionnalité de magasin d’instances de workflow SQL  
 L'installation de [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] ajoute les éléments suivants liés à la fonctionnalité de magasin d'instances de workflow SQL au fichier Machine.config :  
  
-   Ajoute l'élément d'extension de comportement suivant au fichier Machine.config afin que vous puissiez utiliser l'élément de comportement du service <`sqlWorkflowInstanceStore`> dans le fichier de configuration pour configurer la persistance pour vos services.  
  
    ```xml  
    <configuration>  
        <system.serviceModel>  
            <extensions>  
                <behaviorExtensions>  
                    <add name="sqlWorkflowInstanceStore" type="System.Activities.DurableInstancing.SqlWorkflowInstanceStoreElement, System.Activities.DurableInstancing, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />  
                </behaviorExtensions>  
            </extensions>  
        <system.serviceModel>  
    <configuration>  
    ```
