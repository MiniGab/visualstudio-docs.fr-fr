---
title: -ResetSkipPkgs (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /ResetSkipPkgs Devenv switch
- Devenv, /ResetSkipPkgs switch
- ResetSkipPkgs switch
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bbf7a601213c3c02cc35f2d9453eee6b1d39c43e
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704497"
---
# <a name="resetskippkgs-devenvexe"></a>/ResetSkipPkgs (devenv.exe)
Efface toutes les options pour ignorer le chargement ajouté aux packages VS par les utilisateurs qui souhaitent éviter de charger les packages VS à problème, puis démarre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="syntax"></a>Syntaxe

```cmd
Devenv /ResetSkipPkgs
```

## <a name="remarks"></a>Notes
 La présence d’une balise SkipLoading désactive le chargement d’un package VS. L’effacement de la balise réactive le chargement du package VS.

## <a name="example"></a>Exemple
 L’exemple suivant efface toutes les balises SkipLoading.

```cmd
Devenv.exe /ResetSkipPkgs
```

## <a name="see-also"></a>Voir aussi

- [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)