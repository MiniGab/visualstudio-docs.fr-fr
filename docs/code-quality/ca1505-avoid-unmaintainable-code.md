---
title: 'CA1505 : Éviter le code impossible à maintenir'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9aae34f6e999bcf74fdfbae4597b22529863e34f
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546913"
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505 : Éviter le code impossible à maintenir

|||
|-|-|
|TypeName|AvoidUnmantainableCode|
|CheckId|CA1505|
|Category|Microsoft.Maintainability|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type ou une méthode a une faible valeur d'indice de maintenabilité.

## <a name="rule-description"></a>Description de la règle
 L’indice de maintenabilité est calculé en utilisant les métriques suivantes : lignes de code, volume de programme et complexité cyclomatique. Volume de programme est une mesure de la difficulté de compréhension d’un type ou une méthode qui est basé sur le nombre d’opérateurs et d’opérandes dans le code. Complexité cyclomatique est une mesure de la complexité structurelle du type ou de méthode. Plus d’informations sur la métrique du code à [mesure la complexité et la facilité de maintenance du Code managé](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md).

 Un faible indice de maintenabilité indique qu’un type ou une méthode est probablement difficile à maintenir et serait un bon candidat pour modifier la conception.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour résoudre cette violation, reconcevez le type ou la méthode et essayez de diviser en plus petites et plus ciblées des types ou méthodes.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Exclure cet avertissement lorsqu’une méthode ou type est considéré comme plus facile à gérer en dépit de sa grande taille ou de la méthode ou le type ne peut pas être fractionnée.

## <a name="see-also"></a>Voir aussi

- [Avertissements liés à la facilité de maintenance](../code-quality/maintainability-warnings.md)
- [Mesures de la complexité et de la facilité de maintenance du code managé](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)