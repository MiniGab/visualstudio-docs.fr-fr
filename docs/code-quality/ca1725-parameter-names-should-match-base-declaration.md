---
title: 'CA1725 : Les noms de paramètres doivent correspondre à la déclaration de base'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ParameterNamesShouldMatchBaseDeclaration
- CA1725
helpviewer_keywords:
- CA1725
- ParameterNamesShouldMatchBaseDeclaration
ms.assetid: 9b657ab0-fe81-4f4c-9481-ba746988c922
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b1f7c8a71d91468129703b0d2101f7ab0e7527fa
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550713"
---
# <a name="ca1725-parameter-names-should-match-base-declaration"></a>CA1725 : Les noms de paramètres doivent correspondre à la déclaration de base
|||
|-|-|
|TypeName|ParameterNamesShouldMatchBaseDeclaration|
|CheckId|CA1725|
|Category|Microsoft.Naming|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Le nom d’un paramètre dans une substitution de méthode visible de l’extérieur ne correspond pas au nom du paramètre dans la déclaration de base de la méthode ou le nom du paramètre dans la déclaration d’interface de la méthode.

## <a name="rule-description"></a>Description de la règle
 La désignation cohérente des paramètres dans une hiérarchie de substitution augmente la facilité d'utilisation des substitutions de méthode. Un nom de paramètre dans une méthode dérivée qui diffère du nom dans la déclaration de base peut créer une confusion pour déterminer si la méthode est une substitution de la méthode de base ou une nouvelle surcharge de la méthode.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, renommez le paramètre pour correspondre à la déclaration de base. Le correctif est une modification avec rupture pour les méthodes visibles par COM.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas un avertissement de cette règle à l’exception des méthodes visibles par COM dans les bibliothèques fournies antérieurement.