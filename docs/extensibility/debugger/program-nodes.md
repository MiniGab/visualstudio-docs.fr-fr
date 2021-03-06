---
title: Nœuds du programme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 27007773cfe8d8a8b595ee9b1921f35376bf2231
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39251060"
---
# <a name="program-nodes"></a>Nœuds de programme
Dans l’architecture du débogueur, une *nœud du programme*:  
  
-   Est une description léger d’un programme.  
  
-   Peut identifier lui-même et le processus, dans qu'il est en cours d’exécution. Un nœud de programme peut être associé pour être détaché et décrivent le moteur de débogage (dé) qui l’a créé, le cas échéant.  
  
-   Est représenté par un [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interface, généralement créée par un port ou DE. Nœuds de programme sont ajoutés à un port en appelant [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Lorsqu’un nœud de programme est ajouté à un port, il est ajouté au processus contenant le programme qui représente ce nœud de programme.  
  
 Un certain temps après le démarrage d’une session de débogage, selon l’implémentation du package de débogage, les nœuds de programme sont utilisés pour créer des programmes correspondants. Lorsqu’un processus est interrogé pour ses programmes, les programmes sont énumérées, une pour chaque nœud du programme.  
  
 Avant qu’un programme est associé à, l’IDE doit seulement une légère description du programme. Ces informations peuvent être obtenues à partir du nœud de programme. Une fois que le programme est attaché au, l’IDE affiche des informations plus détaillées, telles qu’une liste de tous les threads en cours d’exécution dans le programme. Ces informations sont obtenues à partir du programme lui-même.  
  
## <a name="see-also"></a>Voir aussi  
 [Programmes](../../extensibility/debugger/programs.md)   
 [Processus](../../extensibility/debugger/processes.md)   
 [Moteur de débogage](../../extensibility/debugger/debug-engine.md)   
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)