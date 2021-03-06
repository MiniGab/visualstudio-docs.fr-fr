---
title: 'CA1017 : Marquer les assemblys avec ComVisibleAttribute'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1017
- MarkAssembliesWithComVisible
helpviewer_keywords:
- MarkAssembliesWithComVisible
- CA1017
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d2e720bf4e0bd613b5f31b82e7c50084b1b6d3c1
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548554"
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017 : Marquer les assemblys avec ComVisibleAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithComVisible|
|CheckId|CA1017|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un assembly n’a pas la <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> attribut appliqué à ce dernier.

## <a name="rule-description"></a>Description de la règle
 Le <xref:System.Runtime.InteropServices.ComVisibleAttribute> attribut détermine comment les clients COM accèdent à du code managé. Un bon design stipule que les assemblys indiquent explicitement la visibilité COM. Visibilité COM peut être définie pour un assembly entier et puis être substituée pour des types et membres de type. Si l’attribut n’est pas présent, le contenu de l’assembly est visible aux clients COM.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, ajoutez l’attribut à l’assembly. Si vous ne souhaitez pas que l’assembly soit visible par les clients COM, appliquez l’attribut et définissez sa valeur sur `false`.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle. Si vous souhaitez que l’assembly soit visible, appliquez l’attribut et définissez sa valeur sur `true`.

## <a name="example"></a>Exemple
 L’exemple suivant montre un assembly qui a le <xref:System.Runtime.InteropServices.ComVisibleAttribute> attribut appliqué pour empêcher les clients COM.

 [!code-cpp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CPP/ca1017-mark-assemblies-with-comvisibleattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/VisualBasic/ca1017-mark-assemblies-with-comvisibleattribute_1.vb)]
 [!code-csharp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CSharp/ca1017-mark-assemblies-with-comvisibleattribute_1.cs)]

## <a name="see-also"></a>Voir aussi

- [Interopération avec du code non managé](/dotnet/framework/interop/index)
- [Qualifier des types .NET pour l'interopérabilité](/dotnet/framework/interop/qualifying-net-types-for-interoperation)