---
title: "subarray, m&#233;thode (Int32Array) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: deed3bd4-63cb-4ec8-b5d1-ce9ce4a38f54
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# subarray, m&#233;thode (Int32Array)
Obtient une nouvelle vue Int32Array de la mémoire [ArrayBuffer, objet](../../javascript/reference/arraybuffer-object.md) pour ce tableau, spécifiant le premier et le dernier membre du sous\-tableau.  
  
## Syntaxe  
  
```javascript  
var newInt32Array = int32Array.subarray(begin, end);  
```  
  
## Paramètres  
 `newInt32Array`  
 Sous\-tableau retourné par cette méthode.  
  
 `begin`  
 Index du début du tableau.  
  
 `end`  
 Index de la fin du tableau.  Il est non inclusif.  
  
## Notes  
 Si le paramètre `begin` ou `end` est négatif, il fait référence à un index depuis la fin du tableau, par opposition à depuis le début.  Si le paramètre `end` n'est pas spécifié, le sous\-tableau contient tous les éléments depuis `begin` à la fin du tableau typé.  La plage spécifiée par les valeurs `begin` et `end` est ancrée à la plage d'index valide du tableau en cours.  Si la longueur calculée du nouveau tableau typé est négative, elle est ancrée à zéro.  Le tableau retourné est du même type que le tableau sur lequel cette méthode est appelée.  
  
## Exemple  
 L'exemple suivant montre comment obtenir un sous\-tableau comportant deux éléments, en commençant par le premier élément du tableau.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var intArr = new Int32Array(buffer.byteLength / 4);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]