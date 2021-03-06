---
title: Explorateur de performances | Microsoft Docs
ms.custom: ''
ms.date: 06/19/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance
- vs.performance.wizard.website
helpviewer_keywords:
- performance tools [Visual Studio ALM]
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 450681f03bcb9bd24272d7bcdc7da34ed015587a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="performance-explorer"></a>Explorateur de performances

Grâce aux outils de profilage de Visual Studio, les développeurs peuvent mesurer, évaluer et cibler les problèmes de performances de leur code. Ces outils sont totalement intégrés à l'environnement de développement intégré (IDE) pour fournir une expérience utilisateur conviviale et accessible.

Le profilage d'une application est simple. Vous commencez par créer une session de performance. Dans l'édition Visual Studio Team System Development, vous pouvez utiliser l'Assistant Création d'une nouvelle session de performance pour créer une session de performance. À la fin de la session de performance, les données rassemblées lors du profilage sont enregistrées dans un fichier .vsp. Vous pouvez afficher le fichier .vsp dans l'interface IDE. Plusieurs vues de rapport sont disponibles pour vous aider à visualiser et à détecter les problèmes de performances provenant des données collectées.

Les outils de profilage peuvent également être utilisés à partir de la ligne de commande. Cela offre aux utilisateurs la souplesse nécessaire pour exécuter ces outils à partir de la ligne de commande ou les utiliser pour automatiser les tâches qui utilisent des scripts.

Pour plus d'informations sur les rubriques actuelles et avancées relatives aux performances et au profilage, effectuez une recherche sur MSDN (Microsoft Developer Network) et dans les blogs Microsoft. Utilisez les mots clés Enterprise, Performance, Outils, Team.

## <a name="common-tasks"></a>Tâches courantes

|Tâche|Contenu associé|
|----------|---------------------|
|**Techniques pour Windows 8 et ultérieur**|[Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)|
|**Comprendre les concepts de profilage :** découvrez les concepts et les termes que vous allez utiliser lors de la collecte, de l’affichage et de l’analyse des performances de code à l’aide des outils de profilage.|[Vues d’ensemble](../profiling/overviews-performance-tools.md)|
|**Se lancer et le faire :** apprenez les procédures de base que vous allez utiliser lors de la collecte, de l’affichage et de l’analyse des performances de code à l’aide des outils de profilage. Essayez par vous-même en suivant une procédure pas à pas.|[Prise en main](../profiling/getting-started-with-performance-tools.md)|
|**Configurer une session de profilage :** découvrez des méthodes avancées permettant de spécifier les projets ou les fichiers binaires à profiler, de sélectionner une méthode de profilage, de choisir les données de performance à collecter, ainsi que de définir d’autres options de la session de profilage.|[Configuration de sessions de performances](../profiling/configuring-performance-sessions.md)|
|**Contrôler les données collectées par le profileur :** apprenez à utiliser les propriétés d’une session de performance et les procédures interactives permettant de démarrer et d’arrêter le profilage, ainsi qu’à limiter les données de performance collectées aux informations souhaitées.|[Contrôle de la collecte de données](../profiling/controlling-data-collection.md)|
|**Identifier les problèmes de performances :** apprenez à afficher et à analyser les données de performances collectées dans la fenêtre d’affichage Rapport des outils de profilage.|[Analyse des données des outils d’analyse des performances](../profiling/analyzing-performance-tools-data.md)|
|**Analyser les modifications de performance :** apprenez à comparer deux fichiers de données du profileur pour analyser l’évolution des performances.|[Comparaison des fichiers de données de performances](../profiling/comparing-performance-data-files.md)|
|**Enregistrer et partager vos résultats :** apprenez à enregistrer les données de profilage pour l’archivage ou le partage.|[Enregistrement et exportation des données des outils d’analyse des performances](../profiling/saving-and-exporting-performance-tools-data.md)|
|**Automatiser le profilage :** apprenez à utiliser les outils de profilage à partir de l’invite de commandes.|[Profilage à partir de la ligne de commande](../profiling/using-the-profiling-tools-from-the-command-line.md)|
|**Contrôler le profilage par programmation :** apprenez à utiliser les API managées et natives des outils de profilage pour contrôler la collecte de données directement à partir du code source.|[API des outils de profilage](../profiling/profiling-tools-apis.md)|
|**Résoudre les problèmes de profilage**|[Résolution des problèmes liés aux outils d’analyse des performances](../profiling/troubleshooting-performance-tools-issues.md)|

## <a name="see-also"></a>Voir aussi

[Outils de profilage](../profiling/profiling-tools.md)