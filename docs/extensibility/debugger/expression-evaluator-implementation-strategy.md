---
title: Stratégie d’implémentation évaluateur expression | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a0b60a82b9451dfa43f5cd231fd38dd32b1729ed
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39233046"
---
# <a name="expression-evaluator-implementation-strategy"></a>Stratégie d’implémentation évaluateur expression
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’expression managé](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Pour créer rapidement un évaluateur d’expression (EE) consiste à implémenter tout d’abord le code minimal nécessaire pour afficher les variables locales dans le **variables locales** fenêtre. Il est utile à l’esprit que chaque ligne dans le **variables locales** fenêtre affiche le nom, le type et la valeur d’une variable locale, et que toutes les trois sont représentées par un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objet. Le nom, le type et la valeur d’une variable locale est obtenue à partir d’un `IDebugProperty2` objet en appelant son [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) (méthode). Pour plus d’informations sur l’affichage des variables locales dans le **variables locales** fenêtre, consultez [variables locales affichage](../../extensibility/debugger/displaying-locals.md).  
  
## <a name="discussion"></a>Discussion  
 Une séquence d’implémentation possibles commence par implémentation [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). Le [analyser](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) et [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) méthodes doivent être implémentées pour afficher les variables locales. Appel `IDebugExpressionEvaluator::GetMethodProperty` retourne un `IDebugProperty2` objet qui représente une méthode : autrement dit, un [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) objet. Méthodes eux-mêmes ne sont pas affichés dans le **variables locales** fenêtre.  
  
 Le [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) méthode doit être implémentée ensuite. Le moteur de débogage (dé) appelle cette méthode pour obtenir une liste des variables locales et des arguments en passant `IDebugProperty2::EnumChildren` un `guidFilter` argument de `guidFilterLocalsPlusArgs`. `IDebugProperty2::EnumChildren` appels [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) et [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), combinant les résultats dans une seule énumération. Consultez [afficher les variables locales](../../extensibility/debugger/displaying-locals.md) pour plus d’informations.  
  
## <a name="see-also"></a>Voir aussi  
 [Implémenter un évaluateur d’expression](../../extensibility/debugger/implementing-an-expression-evaluator.md)   
 [Variables locales d’affichage](../../extensibility/debugger/displaying-locals.md)