---
title: 'Comment : utiliser le journal d’activité | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3b5647a62064857bca6a6352a14fe56eff4386f9
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497994"
---
# <a name="how-to-use-the-activity-log"></a>Comment : utiliser le journal d’activité
Les VSPackages peuvent écrire des messages dans le journal d’activité. Cette fonctionnalité est particulièrement utile pour déboguer les VSPackages dans les environnements de vente au détail.  
  
> [!TIP]
>  Le journal d’activité est toujours activé. Visual Studio conserve un tampon de substitution des 100 dernières entrées, ainsi que les 10 premières entrées, qui présentent des informations de configuration générales.  
  
## <a name="to-write-an-entry-to-the-activity-log"></a>Pour écrire une entrée dans le journal d’activité  
  
1.  Insérez ce code dans le <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> méthode ou dans toute autre méthode sauf dans le constructeur de VSPackage :  
  
    ```csharp  
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log == null) return;  
  
    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,  
        this.ToString(),  
        string.Format(CultureInfo.CurrentCulture,  
        "Called for: {0}", this.ToString()));  
    ```  
  
     Ce code obtient le <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> de service et le caste vers une <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interface. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> écrit une entrée d’information dans le journal d’activité en utilisant le contexte de la culture actuels.  
  
2.  Lorsque le VSPackage est chargé (généralement quand une commande est appelée ou une fenêtre est ouverte), le texte est écrit dans le journal d’activité.  
  
## <a name="to-examine-the-activity-log"></a>Pour examiner le journal d’activité  
  
1.  Exécuter Visual Studio avec le [/Log](../ide/reference/log-devenv-exe.md) commutateur de ligne de commande pour écrire ActivityLog.xml sur le disque pendant votre session.

2.  Après la fermeture de Visual Studio, recherchez le journal d’activité dans le sous-dossier data de Visual Studio : **%AppData%* \Microsoft\VisualStudio\15.0\ActivityLog.xml*.  
  
3.  Ouvrez le journal d’activité avec n’importe quel éditeur de texte. Voici une entrée de type :  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## <a name="robust-programming"></a>Programmation fiable  
 Étant donné que le journal d’activité est un service, le journal d’activité n’est pas disponible dans le constructeur de VSPackage.  
  
 Vous devez obtenir le journal d’activité juste avant l’écriture dans celle-ci. Ne pas mettre en cache ou enregistrer le journal d’activité pour une utilisation ultérieure.  
  
## <a name="see-also"></a>Voir aussi
 [/ Log (devenv.exe)](../ide/reference/log-devenv-exe.md)   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [Dépannage de VSPackages](../extensibility/troubleshooting-vspackages.md)   
 [VSPackages](../extensibility/internals/vspackages.md)
