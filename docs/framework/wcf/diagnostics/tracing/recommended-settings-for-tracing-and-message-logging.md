---
title: Paramètres recommandés pour le suivi et l'enregistrement des messages
ms.date: 03/30/2017
ms.assetid: c6aca6e8-704e-4779-a9ef-50c46850249e
ms.openlocfilehash: dff4b20547cccca628ac76afc890a2817e838907
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585209"
---
# <a name="recommended-settings-for-tracing-and-message-logging"></a>Paramètres recommandés pour le suivi et l'enregistrement des messages
Cette rubrique décrit les paramètres de suivi et d'enregistrement des messages recommandés pour différents environnements d'exploitation.  
  
## <a name="recommended-settings-for-a-production-environment"></a>Paramètres recommandés pour un environnement de production  
 Pour un environnement de production, si vous utilisez les sources de suivi WCF, affectez à `switchValue` la valeur Warning. Si vous utilisez la source de suivi WCF `System.ServiceModel`, affectez à l'attribut `switchValue` la valeur `Warning` et à l'attribut `propagateActivity` la valeur `true`. Si vous utilisez une source de suivi définie par l'utilisateur, affectez à l'attribut `switchValue` la valeur `Warning, ActivityTracing`. Procéder manuellement à l’aide de la [l’outil Éditeur de Configuration (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md). Si vous ne prévoyez pas d‘augmentation des performances, vous pouvez affecter la valeur `switchValue` à l‘attribut `Information` dans tous les cas mentionnés précédemment, ce qui génère une quantité assez élevée de données de suivi. L'exemple suivant illustre ces paramètres recommandés.  
  
```xml  
<configuration>  
 <system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel"  
            switchValue="Warning"  
            propagateActivity="true" >  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
    <source name="myUserTraceSource"  
            switchValue="Warning, ActivityTracing">  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="xml"  
         type="System.Diagnostics.XmlWriterTraceListener"  
               initializeData="C:\logs\Traces.svclog" />  
  </sharedListeners>  
 </system.diagnostics>  
  
<system.serviceModel>  
  <diagnostics wmiProviderEnabled="true">  
  </diagnostics>  
 </system.serviceModel>  
</configuration>  
```  
  
## <a name="recommended-settings-for-deployment-or-debugging"></a>Paramètres recommandés pour le déploiement ou le débogage  
 Pour l'environnement de déploiement ou de débogage , choisissez `Information` ou `Verbose`, avec `ActivityTracing` pour une source de suivi `System.ServiceModel` ou définie par l'utilisateur. Pour améliorer le débogage, vous devez également ajouter une source de suivi supplémentaire (`System.ServiceModel.MessageLogging`) à la configuration afin d'activer l'enregistrement des messages. Remarquez que l'attribut `switchValue` n'a aucun impact sur cette source de suivi.  
  
 L'exemple suivant illustre les paramètres recommandés, à l'aide d'un écouteur partagé qui utilise le `XmlWriterTraceListener`.  
  
```xml  
<configuration>  
 <system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel"  
            switchValue="Information, ActivityTracing"  
            propagateActivity="true" >  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
    <source name="System.ServiceModel.MessageLogging">  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
    <source name="myUserTraceSource"  
            switchValue="Information, ActivityTracing">  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="xml"  
         type="System.Diagnostics.XmlWriterTraceListener"  
               initializeData="C:\logs\Traces.svclog" />  
  </sharedListeners>  
 </system.diagnostics>  
  
 <system.serviceModel>  
  <diagnostics wmiProviderEnabled="true">  
      <messageLogging   
           logEntireMessage="true"   
           logMalformedMessages="true"  
           logMessagesAtServiceLevel="true"   
           logMessagesAtTransportLevel="true"  
           maxMessagesToLog="3000"   
       />  
  </diagnostics>  
 </system.serviceModel>  
</configuration>  
```  
  
## <a name="using-wmi-to-modify-settings"></a>Utilisation de WMI pour modifier des paramètres  
 Vous pouvez utiliser WMI pour modifier des paramètres de configuration pendant l'exécution (en activant l'attribut `wmiProviderEnabled` dans la configuration, comme cela est indiqué dans l'exemple de configuration précédent). Par exemple, vous pouvez utiliser WMI dans le CIM Studio pour modifier les niveaux de source de suivi de Warning à Information au moment de l'exécution. Vous devez savoir que le coût de performance du débogage en direct de cette manière peut être très élevé. Pour plus d’informations sur l’utilisation de WMI, consultez le [à l’aide de Windows Management Instrumentation pour les Diagnostics](../../../../../docs/framework/wcf/diagnostics/wmi/index.md) rubrique.  
  
## <a name="enable-correlated-events-in-aspnet-tracing"></a>Activer des événements corrélés dans le suivi ASP.NET  
 Les événements ASP.NET ne définissent pas l'ID de corrélation (ActivityID), sauf si le suivi de l'élément ASP.NET est activé. Pour afficher correctement les événements en corrélation, vous devez activer des événements ASP.NET suivi à l’aide de la commande suivante dans la console de commande, qui peut être appelée en accédant à **Démarrer**, **exécuter** et type **cmd** ,  
  
```  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 Pour désactiver le suivi des événements ASP.NET, utilisez la commande suivante,  
  
```  
logman stop mytrace -ets  
```  
  
## <a name="see-also"></a>Voir aussi
- [Utilisation de Windows Management Instrumentation pour les diagnostics](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)
