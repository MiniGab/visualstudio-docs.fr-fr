---
title: Guide pratique pour attacher le profileur à un service .NET et collecter des statistiques d’application en utilisant la ligne de commande | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a0046c47-26c8-4bec-96a0-81da05e5104a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 3ca8187518379452b8227fffd0db5f8ef16c6793
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766563"
---
# <a name="how-to-attach-the-profiler-to-a-net-service-to-collect-application-statistics-by-using-the-command-line"></a>Guide pratique pour attacher le profileur à un service .NET et collecter des statistiques d’application en utilisant la ligne de commande
Cet article explique comment utiliser les outils en ligne de commande des Outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour attacher le profileur à un service .NET Framework et collecter des statistiques de performances à l’aide de la méthode d’échantillonnage.  
  
> [!NOTE]
>  Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications UWP nécessitent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
>   
>  Les outils en ligne de commande des Outils de profilage se trouvent dans le sous-répertoire *\Team Tools\Performance Tools* du répertoire d’installation de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Les versions 64 bits et 32 bits des outils sont disponibles sur les ordinateurs 64 bits. Pour utiliser les outils en ligne de commande du profileur, vous devez ajouter le chemin des outils à la variable d’environnement PATH dans la fenêtre d’invite de commandes ou bien l’ajouter à la commande elle-même. Pour plus d’informations, consultez [Spécifier le chemin des outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  Pour ajouter des données d’interaction de couche à une exécution de profilage, vous devez utiliser des procédures spécifiques avec les outils de profilage en ligne de commande. Consultez [Collecter les données d’interaction de couche](../profiling/adding-tier-interaction-data-from-the-command-line.md).  
  
 Pour collecter des données de performances auprès d’une application .NET Framework, vous devez utiliser l’outil [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) pour initialiser les variables d’environnement appropriées. Vous devez ensuite redémarrer l’ordinateur qui héberge le service et configurer cet ordinateur pour le profilage. Vous attachez ensuite le profileur au processus du service. Quand le profileur est attaché au service, vous pouvez suspendre et reprendre la collecte de données.  
  
 Pour mettre fin à une session de profilage, vous devez détacher le profileur du service et l’arrêter explicitement. Dans la plupart des cas, nous vous recommandons de désactiver les variables d’environnement de profilage à la fin d’une session.  
  
## <a name="attach-the-profiler"></a>Attacher le profileur  
  
#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>Pour attacher le profileur à un service .NET Framework  
  
1.  Installez le service.  
  
2.  Ouvrez une fenêtre d’invite de commandes.  
  
3.  Initialisez les variables d’environnement de profilage. Type :  
  
     **VSPerfClrEnv /globalsampleon** [**/samplelineoff**]  
  
    -   **/globalsampleon** permet l’échantillonnage.  
  
    -   **/samplelineoff** désactive l’assignation des données collectées à des lignes de code source spécifiques. Lorsque cette option est spécifiée, les données sont assignées uniquement aux fonctions.  
  
4.  Redémarrez l'ordinateur.  
  
5.  Ouvrez une fenêtre d’invite de commandes.  
  
6.  Démarrez le profileur. Type :  
  
     **VSPerfCmd**  [/start](../profiling/start.md) **:sample**  [/output](../profiling/output.md) **:** `OutputFile` [`Options`]  
  
    -   L’option **/start:sample** initialise le profileur.  
  
    -   L’option **/output:**`OutputFile` est nécessaire avec **/start**. `OutputFile` spécifie le nom et l’emplacement du fichier de données profilage (.vsp).  
  
     Vous pouvez utiliser l’une des options suivantes avec l’option **/start:sample**.  
  
    > [!NOTE]
    >  Les options **/user** et **/crosssession** sont généralement nécessaires pour les services.  
  
    |Option|Description|  
    |------------|-----------------|  
    |[/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Spécifie le nom de domaine et d’utilisateur du compte propriétaire du processus profilé. Cette option n’est nécessaire que si le processus s’exécute sous le compte d’un utilisateur autre que celui connecté. Le propriétaire du processus est répertorié dans la colonne Nom d’utilisateur, sous l’onglet Processus du gestionnaire des tâches de Windows.|  
    |[/crosssession](../profiling/crosssession.md)|Active le profilage des processus dans d’autres sessions. Cette option est nécessaire si le service s’exécute dans une autre session. L’ID de session est répertorié dans la colonne ID de session, sous l’onglet Processus du gestionnaire des tâches de Windows. **/CS** peut être spécifié comme abréviation de **/crosssession**.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Spécifie le compteur de performances Windows dont les données doivent être collectées au cours du profilage.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|À utiliser avec **/wincounter** uniquement. Spécifie le nombre de millisecondes écoulées entre les événements de collecte du compteur de performances Windows. La valeur par défaut est de 500 ms.|  
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Spécifie l’événement du Suivi d’événements pour Windows (ETW) qui doit être collecté au cours du profilage. Les événements ETW sont collectés dans un fichier séparé (.etl).|  
  
7.  Si nécessaire, démarrez le service.  
  
8.  Attachez le profileur au service. Type :  
  
     **VSPerfCmd**  [/attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [`Sample Event`] [[/targetclr](../profiling/targetclr.md)**:**`Version`]  
  
    -   Spécifiez l’ID (`PID`) ou le nom de processus (ProcName) du service. Vous pouvez afficher les ID et les noms de processus de tous les processus en cours d’exécution dans le Gestionnaire des tâches de Windows.  
  
     Par défaut, les données de performances sont échantillonnées tous les 10 000 000 cycles d’horloge ininterrompus du processeur. Ceci représente environ 100 échantillons par seconde sur un processeur 1 GHz. Vous pouvez spécifier l’une des options suivantes pour modifier l’intervalle de cycle d’horloge ou pour spécifier un autre événement d’échantillonnage.  
  
    |Événement d’échantillonnage|Description|  
    |------------------|-----------------|  
    |[/timer](../profiling/timer.md) **:** `Interval`|Remplace l’intervalle d’échantillonnage par le nombre de cycles d’horloge sans interruption spécifié par `Interval`.|  
    |[/pf](../profiling/pf.md)[**:**`Interval`]|Remplace l’événement d’échantillonnage par les erreurs de page. Si `Interval` est spécifié, définit le nombre d’erreurs de page entre chaque échantillon. La valeur par défaut est 10.|  
    |[/sys](../profiling/sys-vsperfcmd.md)[`:``Interval`]|Remplace l’événement d’échantillonnage par des appels système du processus vers le noyau du système d’exploitation (syscalls). Si `Interval` est spécifié, définit le nombre d’appels entre chaque échantillon. La valeur par défaut est 10.|  
    |[/counter](../profiling/counter.md) **:** `Config`|Remplace l’événement et l’intervalle d’échantillonnage par le compteur de performances du processeur et l’intervalle spécifiés dans `Config`.|  
  
    -   **targetclr** : `Version` spécifie la version du common language runtime (CLR) à profiler lorsque plusieurs versions du runtime sont chargées dans une application. Facultative.  
  
## <a name="control-data-collection"></a>Contrôler la collecte des données  
 Quand le service s’exécute, vous pouvez utiliser les options de *VSPerfCmd.exe* pour démarrer et arrêter l’écriture des données dans le fichier de données du profileur. Le fait de pouvoir contrôler la collecte vous permet de collecter des données pour une phase spécifique de l’exécution du programme, telle que le démarrage ou l’arrêt de l’application.  
  
#### <a name="to-start-and-stop-data-collection"></a>Pour démarrer et arrêter la collecte de données  
  
-   Les paires d’options **VSPerfCmd** suivantes permettent de démarrer et d’arrêter la collecte des données. Spécifiez chaque option sur une ligne de commande distincte. Vous pouvez activer et désactiver la collecte de données à plusieurs reprises.  
  
    |Option|Description|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Démarre (**/globalon**) ou arrête (**/globaloff**) la collecte des données pour tous les processus.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Démarre (**/processon**) ou arrête (**/processoff**) la collecte des données pour le processus spécifié par l’ID de processus (`PID`).|  
    |**/attach:**{`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[:{`PID`&#124;`ProcName`}]|**/attach** commence à collecter des données pour le processus spécifié par l’ID ou le nom de processus. **/detach** arrête la collecte des données pour le processus spécifié ou pour tous les processus, si aucun processus n’est spécifié.|  
  
## <a name="end-the-profiling-session"></a>Arrêter la session de profilage  
 Pour que vous puissiez mettre fin à une session de profilage, le profileur ne doit plus être attaché à un processus profilé et doit être arrêté explicitement. Vous pouvez détacher le profileur d’une application profilée avec la méthode d’échantillonnage en fermant l’application ou en appelant l’option **VSPerfCmd /detach**. Vous devez alors appeler l’option **VSPerfCmd /shutdown** pour désactiver le profileur et fermer le fichier de données de profilage.  
  
 La commande **VSPerfClrEnv /globaloff** efface les variables d’environnement de profilage. Toutefois, la configuration du système n’est pas réinitialisée tant que l’ordinateur n’a pas été redémarré.  
  
#### <a name="to-end-a-profiling-session"></a>Pour terminer une session de profilage  
  
1.  Effectuez une des opérations suivantes pour détacher le profileur de l’application cible :  
  
    -   Arrêtez le service.  
  
         - ou -  
  
    -   Tapez **VSPerfCmd /detach**  
  
2.  Fermez le profileur. Type :  
  
     **VSPerfCmd /shutdown**  
  
3.  (Facultatif) Effacez les variables d’environnement de profilage. Type :  
  
     **VSPerfClrEnv /globaloff**  
  
4.  Redémarrez l'ordinateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Profiler des services](../profiling/command-line-profiling-of-services.md)   
 [Vues de données de la méthode d’échantillonnage](../profiling/profiler-sampling-method-data-views.md)