---
title: "Point de terminaison de métadonnées sécurisé personnalisée"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e369e99-ea4a-49ff-aed2-9fdf61091a48
caps.latest.revision: "19"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: b4ec6efa2a2b0993f7088e4424de86b3d3ad6c8b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="custom-secure-metadata-endpoint"></a>Point de terminaison de métadonnées sécurisé personnalisée
Cet exemple montre comment implémenter un service avec un point de terminaison de métadonnées sécurisé qui utilise l’une des liaisons non-metadata exchange et comment configurer [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ou aux clients d’extraire le métadonnées à partir de ce un point de terminaison de métadonnées. Il existe deux liaisons fournies par le système pour exposer des points de terminaison de métadonnées : mexHttpBinding et mexHttpsBinding. mexHttpBinding est utilisé pour exposer un point de terminaison de métadonnées sur HTTP de façon non sécurisée. mexHttpsBinding est utilisé pour exposer un point de terminaison de métadonnées sur HTTPS de façon sécurisée. Cet exemple montre comment exposer un point de terminaison de métadonnées sécurisé à l'aide du <xref:System.ServiceModel.WSHttpBinding>. Cette opération peut être utile lorsque vous souhaitez modifier les paramètres de sécurité de la liaison sans devoir utiliser HTTPS. Si vous utilisez mexHttpsBinding, votre point de terminaison de métadonnées sera sécurisé, mais il n'existe aucun moyen de modifier les paramètres de la liaison.  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
## <a name="service"></a>Service  
 Dans cet exemple, le service dispose de deux points de terminaison. Le point de terminaison d'application sert le contrat `ICalculator` d'une liaison `WSHttpBinding`, `ReliableSession` étant activée et la sécurité `Message` utilisant des certificats. Le point de terminaison de métadonnées utilise également une liaison `WSHttpBinding`, avec les mêmes paramètres de sécurité mais sans `ReliableSession`. Le code suivant contient la configuration requise :  
  
```xml  
<services>   
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
     <!-- use base address provided by host -->  
     <endpoint address=""  
       binding="wsHttpBinding"  
       bindingConfiguration="Binding2"  
       contract="Microsoft.ServiceModel.Samples.ICalculator" />  
     <endpoint address="mex"  
       binding="wsHttpBinding"  
       bindingConfiguration="Binding1"  
       contract="IMetadataExchange" />  
     </service>  
 </services>  
 <bindings>  
   <wsHttpBinding>  
     <binding name="Binding1">  
       <security mode="Message">  
         <message clientCredentialType="Certificate" />  
       </security>  
     </binding>  
     <binding name="Binding2">  
       <reliableSession inactivityTimeout="00:01:00" enabled="true" />  
       <security mode="Message">  
         <message clientCredentialType="Certificate" />  
       </security>  
     </binding>  
   </wsHttpBinding>  
 </bindings>  
```  
  
 Dans de nombreux autres exemples, le point de terminaison de métadonnées utilise la liaison par défaut `mexHttpBinding`, laquelle n'est pas sécurisée. Dans cet exemple, les métadonnées sont sécurisées grâce à l'utilisation conjointe de la liaison `WSHttpBinding` et de la sécurité `Message`. Pour que des clients de métadonnées puissent récupérer ces métadonnées, ils doivent être configurés à l'aide d'une liaison similaire. Cet exemple contient deux clients configurés à l'aide d'une telle liaison.  
  
 Le premier client utilise Svcutil.exe pour extraire les métadonnées et générer le code client ainsi que la configuration pendant la conception. Le service utilisant une liaison non définie par défaut pour les métadonnées, l'outil Svcutil.exe doit être configuré de manière spécifique, c'est-à-dire de sorte à pouvoir obtenir les métadonnées de ce service en utilisant une telle liaison.  
  
 Le deuxième client utilise le `MetadataResolver` pour extraire dynamiquement les métadonnées d'un contrat connu, puis pour appeler des opérations sur le client généré dynamiquement.  
  
## <a name="svcutil-client"></a>Client Svcutil  
 Lorsque la liaison par défaut héberge votre point de terminaison `IMetadataExchange`, vous pouvez exécuter Svcutil.exe en utilisant l'adresse de ce point de terminaison :  
  
```  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 ce qui fonctionnera parfaitement. Cependant, dans cet exemple, le serveur n'utilise pas de point de terminaison défini par défaut pour héberger les métadonnées. Vous devez donc indiquer à l’outil Svcutil.exe quelle liaison il doit utiliser. Pour ce faire, vous pouvez notamment utiliser un fichier Svcutil.exe.config.  
  
 Ce fichier ressemble à un fichier de configuration client standard. Le nom et le contrat de point de terminaison client qui y figurent sont les deux seuls points qui diffèrent :  
  
```xml  
<endpoint name="http"  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"  
          behaviorConfiguration="ClientCertificateBehavior"  
          contract="IMetadataExchange" />  
```  
  
 Le nom de point de terminaison doit correspondre au nom du schéma de l'adresse où sont hébergées les métadonnées et le contrat de point de terminaison doit correspondre à `IMetadataExchange`. Par conséquent, lorsque Svcutil.exe est exécuté à l'aide d'une ligne de commande telle que celle présentée ci-dessous :  
  
```  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 il recherche le point de terminaison nommé « http » et le contrat `IMetadataExchange` pour configurer la liaison et le comportement de l'échange de communication à l'aide du point de terminaison de métadonnées. Le reste du fichier Svcutil.exe.config (dans cet exemple) spécifie la configuration de la liaison et les informations d'identification du comportement de sorte à ce qu'elles correspondent à la configuration du point de terminaison de métadonnées côté serveur.  
  
 Pour que l'outil Svcutil.exe puisse récupérer la configuration spécifiée dans le fichier Svcutil.exe.config, ils doivent tous deux se trouver dans le même répertoire. Vous devez copier l'outil Svcutil.exe depuis son emplacement d'installation vers le répertoire qui contient le fichier Svcutil.exe.config. À partir de ce répertoire, exécutez ensuite la commande suivante :  
  
```  
.\svcutil.exe http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 L’interligne ». \\« garantit que la copie de Svcutil.exe dans ce répertoire (celui qui a un fichier Svcutil.exe.config correspondant) est exécutée.  
  
## <a name="metadataresolver-client"></a>Client MetadataResolver  
 Si le client connaît le contrat et sait comment s'adresser aux métadonnées pendant la conception, il peut trouver dynamiquement la liaison et l'adresse des points de terminaison d'application à l'aide du `MetadataResolver`. Cet exemple de client démontre comme cela est possible en indiquant comment configurer la liaison et les informations d'identification utilisées par `MetadataResolver` en créant et configurant un `MetadataExchangeClient`.  
  
 La liaison ainsi que les informations de certificat apparues dans Svcutil.exe.config peuvent également être spécifiées à l'identique et de manière impérative sur le `MetadataExchangeClient` :  
  
```  
// Specify the Metadata Exchange binding and its security mode  
WSHttpBinding mexBinding = new WSHttpBinding(SecurityMode.Message);  
mexBinding.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
// Create a MetadataExchangeClient for retrieving metadata, and set the // certificate details  
MetadataExchangeClient mexClient = new MetadataExchangeClient(mexBinding);  
mexClient.SoapCredentials.ClientCertificate.SetCertificate(    StoreLocation.CurrentUser, StoreName.My,  
    X509FindType.FindBySubjectName, "client.com");  
mexClient.SoapCredentials.ServiceCertificate.Authentication.    CertificateValidationMode =    X509CertificateValidationMode.PeerOrChainTrust;  
mexClient.SoapCredentials.ServiceCertificate.SetDefaultCertificate(    StoreLocation.CurrentUser, StoreName.TrustedPeople,  
    X509FindType.FindBySubjectName, "localhost");  
```  
  
 Grâce au `mexClient` configuré, nous pouvons énumérer les contrats auxquels nous nous intéressons et utiliser un `MetadataResolver` pour extraire une liste des points de terminaison correspondant à ces contrats :  
  
```  
// The contract we want to fetch metadata for  
Collection<ContractDescription> contracts =    new Collection<ContractDescription>();  
ContractDescription contract =    ContractDescription.GetContract(typeof(ICalculator));  
contracts.Add(contract);  
// Find endpoints for that contract  
EndpointAddress mexAddress = new    EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
ServiceEndpointCollection endpoints =    MetadataResolver.Resolve(contracts, mexAddress, mexClient);  
```  
  
 Enfin, nous pouvons utiliser les informations de ces points de terminaison pour initialiser la liaison et l'adresse de la fabrication `ChannelFactory` utilisée pour créer les canaux assurant la communication avec les points de terminaison d'application.  
  
```  
ChannelFactory<ICalculator> cf = new    ChannelFactory<ICalculator>(endpoint.Binding, endpoint.Address);  
```  
  
 L'objectif premier de cet exemple de client est de démontrer que si vous utilisez un `MetadataResolver` et que vous devez spécifier des liaisons ou comportements personnalisés pour la communication d'échange de métadonnées, vous pouvez utiliser un `MetadataExchangeClient` pour ce faire.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Pour configurer et générer l'exemple  
  
1.  Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer la solution, suivez les instructions de [génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a>Pour exécuter l'exemple sur le même ordinateur  
  
1.  Exécutez Setup.bat à partir du dossier d'installation de l'exemple. Tous les certificats requis à l'exécution de l'exemple sont ainsi installés. Notez que le fichier Setup.bat utilise l’outil FindPrivateKey.exe, qui est installé en exécutant setupCertTool.bat à partir de [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Exécutez l'application cliente à partir du dossier \MetadataResolverClient\bin ou du dossier \SvcutilClient\bin. L'activité du client s'affiche sur son application de console.  
  
3.  Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
4.  Supprimez les certificats en exécutant Cleanup.bat une fois l'exemple terminé. D'autres exemples de sécurité utilisent ces mêmes certificats.  
  
#### <a name="to-run-the-sample-across-machines"></a>Pour exécuter l'exemple sur plusieurs ordinateurs  
  
1.  Sur le serveur, exécutez `setup.bat service`. En cours d’exécution `setup.bat` avec la `service` argument crée un certificat de service portant le nom de domaine complet de l’ordinateur et exporte le certificat de service dans un fichier nommé Service.cer.  
  
2.  Sur le serveur, modifiez Web.config en fonction du nouveau nom de ce certificat. Autrement dit, modifiez le `findValue` d’attribut dans le [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) élément pour le nom de domaine complet de l’ordinateur.  
  
3.  Copiez le fichier Service.cer du répertoire de service dans le répertoire client sur l'ordinateur client.  
  
4.  Sur le client, exécutez `setup.bat client`. En cours d’exécution `setup.bat` avec la `client` argument crée un certificat client appelé Client.com et exporte le certificat client vers un fichier nommé Client.cer.  
  
5.  Dans le fichier App.config du `MetadataResolverClient` de l'ordinateur client, modifiez la valeur d'adresse du point de terminaison mex en fonction de la nouvelle adresse de votre service. Pour ce faire, remplacez localhost par le nom de domaine complet du serveur. Remplacez également l'occurrence de « localhost » dans le fichier metadataResolverClient.cs par le nouveau nom du certificat de service (c'est-à-dire par le nom de domaine complet du serveur). Effectuez la même opération pour l'App.config du projet SvcutilClient.  
  
6.  Copiez le fichier Client.cer du répertoire client dans le répertoire de service sur le serveur.  
  
7.  Sur le client, exécutez `ImportServiceCert.bat`. Cette opération importe le certificat de service du fichier Service.cer dans le magasin CurrentUser - TrustedPeople.  
  
8.  Sur le serveur, exécutez `ImportClientCert.bat`. Cette opération importe le certificat client du fichier Client.cer dans le magasin LocalMachine - TrustedPeople.  
  
9. Sur l'ordinateur de service, générez le projet de service à l'aide de Visual Studio, puis sélectionnez la page d'aide d'un navigateur Web afin de vous assurer que ce projet s'exécute.  
  
10. Sur l'ordinateur client, exécutez le MetadataResolverClient ou le SvcutilClient depuis VS.  
  
    1.  Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Pour procéder au nettoyage après exécution de l'exemple  
  
-   Exécutez Cleanup.bat dans le dossier d'exemples après avoir exécuté l'exemple.  
  
    > [!NOTE]
    >  Ce script ne supprime pas les certificats de service figurant sur le client lorsque l'exemple est exécuté sur plusieurs ordinateurs. Si vous avez exécuté des exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] qui utilisent des certificats sur plusieurs ordinateurs, assurez-vous d'effacer les certificats de service installés dans le magasin CurrentUser - TrustedPeople. Pour ce faire, utilisez la ligne de commande suivante : `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`. Par exemple : `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\CustomMexEndpoint`  
  
## <a name="see-also"></a>Voir aussi
