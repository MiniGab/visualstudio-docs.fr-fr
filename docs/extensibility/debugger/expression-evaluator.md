---
title: Évaluateur d’expression | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f27ef612fffa380bcec3bd252fb4a4601bf07e8e
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231618"
---
# <a name="expression-evaluator"></a>Évaluateur d’expression
Évaluateurs d’expression (EE) examiner la syntaxe d’une langue pour analyser et évaluer des variables et expressions en cours d’exécution, ce qui leur permet d’être affiché par l’utilisateur lors de l’IDE est en mode arrêt.  
  
## <a name="use-expression-evaluators"></a>Utiliser les évaluateurs d’expression  
 Les expressions sont créées à l’aide de la [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) méthode, comme suit :  
  
1.  Le moteur de débogage (dé) implémente la [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interface.  
  
2.  Obtient le package de débogage un `IDebugExpressionContext2` de l’objet à partir d’un [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interface, puis appelle la `IDebugStackFrame2::ParseText` méthode dessus pour obtenir un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objet.  
  
3.  Les appels de package de débogage la [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) méthode ou le [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) méthode pour obtenir la valeur de l’expression. `IDebugExpression2::EvaluateAsync` est appelée à partir de la fenêtre de commande/exécution. Tous les autres composants d’interface utilisateur appellent `IDebugExpression2::EvaluateSync`.  
  
4.  Le résultat de l’évaluation de l’expression est un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objet qui contient le nom, le type et la valeur du résultat de l’évaluation d’expression.  
  
 Lors de l’évaluation d’expression, le EE requiert des informations à partir du composant de fournisseur de symboles. Le fournisseur de symboles fournit des informations sur les symboles utilisées pour identifier et comprendre l’expression analysée.  
  
 Lors de l’évaluation de l’expression asynchrone se termine, un événement asynchrone est envoyé par le DE via le Gestionnaire de session de débogage (SDM) pour informer l’IDE que l’évaluation de l’expression est terminée. Et, le résultat de l’évaluation est ensuite retourné à partir de l’appel à la `IDebugExpression2::EvaluateSync` (méthode).  
  
## <a name="implementation-notes"></a>Remarques d'implémentation  
 Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] attendent des moteurs de débogage discuter avec l’évaluateur d’expression à l’aide des interfaces du Common Language Runtime (CLR). Par conséquent, un évaluateur d’expression qui fonctionne avec le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] moteurs de débogage doivent prendre en charge le CLR (vous trouverez une liste complète des CLR toutes les interfaces de débogage dans debugref.doc, qui fait partie de la [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]).  
  
## <a name="see-also"></a>Voir aussi  
 [Composants du débogueur](../../extensibility/debugger/debugger-components.md)