---
title: CompoundCurve | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- dbe-spatial
ms.topic: conceptual
ms.assetid: ae357f9b-e3e2-4cdf-af02-012acda2e466
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1aecfa5c0c46e061c28479ebc244dc8d0c30ca72
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48089441"
---
# <a name="compoundcurve"></a>CompoundCurve
  `CompoundCurve` è una raccolta di zero o più istanze `CircularString` o `LineString` continue di tipo geometry o geography.  
  
> [!IMPORTANT]  
>  Per una descrizione dettagliata ed esempi delle nuove funzionalità spaziali in questa versione, inclusi i `CompoundCurve` sottotipo, scaricare il white paper [nuove funzionalità spaziali in SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=226407).  
  
 È possibile creare un'istanza `CompoundCurve` vuota, ma affinché `CompoundCurve` sia valida è necessario che vengano rispettati i criteri seguenti:  
  
1.  Deve contenere almeno una `CircularString` o `LineString` istanza.  
  
2.  La sequenza degli `CircularString` o `LineString` istanze devono essere continue.  
  
 Se un `CompoundCurve` contiene una sequenza di più `CircularString` e `LineString` istanze, l'endpoint finale per ogni istanza, ad eccezione dell'ultima istanza deve essere l'endpoint iniziale dell'istanza successiva nella sequenza. Ciò significa che se il punto finale di un'istanza precedente nella sequenza è (4 3 7 2), il punto iniziale dell'istanza successiva nella sequenza deve essere (4 3 7 2). Si noti che i valori Z (elevazione) e M (misura) del punto devono essere anch'essi uguali. Nel caso di una differenza nei due punti, viene generata un'eccezione `System.FormatException` . Fa riferimento un `CircularString` non è necessario avere un valore Z o M. Se non sono presenti valori Z o M per il punto finale dell'istanza precedente, il punto iniziale dell'istanza successiva non potrà includere valori Z o M. Se il punto finale della sequenza precedente è (4 3), il punto iniziale della sequenza successiva dovrà essere (4 3). Non potrà essere (4 3 7 2). Tutti i punti in un `CompoundCurve` istanza deve avere alcun valore Z oppure lo stesso valore Z.  
  
## <a name="compoundcurve-instances"></a>Istanze CompoundCurve  
 La figura seguente mostra valida `CompoundCurve` tipi.  
  
 ![](../../database-engine/media/f278742e-b861-4555-8b51-3d972b7602bf.png "f278742e-b861-4555-8b51-3d972b7602bf")  
  
### <a name="accepted-instances"></a>Istanze accettate  
 L'istanza `CompoundCurve` viene accettata se è un'istanza vuota o se soddisfa i criteri seguenti.  
  
1.  Tutte le istanze contenute nell'istanza `CompoundCurve` sono istanze di segmenti di arco circolare accettate. Per altre informazioni sulle istanze di segmenti di arco circolare accettate, vedere [LineString](linestring.md) e [CircularString](circularstring.md).  
  
2.  Tutti i segmenti di arco circolare nel `CompoundCurve` istanza sono connessi. Il primo punto di ogni segmento di arco circolare successivo è uguale all'ultimo punto del segmento di arco circolare precedente.  
  
    > [!NOTE]  
    >  Sono incluse le coordinate Z e M. È quindi necessario che tutte e quattro le coordinate X, Y, Z e M siano uguali.  
  
3.  Nessuna delle istanze contenute è un'istanza vuota.  
  
 Nell'esempio seguente viene accettato `CompoundCurve` istanze.  
  
```  
DECLARE @g1 geometry = 'COMPOUNDCURVE EMPTY';  
DECLARE @g2 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 0, 0 1, -1 0), (-1 0, 2 0))';  
```  
  
 Nell'esempio seguente vengono illustrate le istanze `CompoundCurve` non accettate. Queste istanze generano un'eccezione `System.FormatException`.  
  
```  
DECLARE @g1 geometry = 'COMPOUNDCURVE(CIRCULARSTRING EMPTY)';  
DECLARE @g2 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 0, 0 1, -1 0), (1 0, 2 0))';  
```  
  
### <a name="valid-instances"></a>Istanze valide  
 Oggetto `CompoundCurve` istanza è valida se soddisfa i criteri seguenti.  
  
1.  Il `CompoundCurve` istanza viene accettata.  
  
2.  Tutte le istanze di segmenti di arco circolare contenute nell'istanza `CompoundCurve` sono istanze valide.  
  
 L'esempio seguente mostra valido `CompoundCurve` istanze.  
  
```  
DECLARE @g1 geometry = 'COMPOUNDCURVE EMPTY';  
DECLARE @g2 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 0, 0 1, -1 0), (-1 0, 2 0))';  
DECLARE @g3 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 1, 1 1, 1 1), (1 1, 3 5, 5 4))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();  
  
```  
  
 `@g3` è valida perché l'istanza `CircularString` è valida. Per altre informazioni sulla validità del `CircularString` dell'istanza, vedere [CircularString](circularstring.md).  
  
 Nell'esempio seguente vengono illustrate le istanze `CompoundCurve` non valide.  
  
```  
DECLARE @g1 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 1, 1 1, 1 1), (1 1, 3 5, 5 4, 3 5))';  
DECLARE @g2 geometry = 'COMPOUNDCURVE((1 1, 1 1))';  
DECLARE @g3 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 1, 2 3, 1 1))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();  
```  
  
 `@g1` non è valida perché la seconda istanza non è un'istanza LineString valida. `@g2` non è valida perché l'istanza `LineString` non è valida. `@g3` non è valida perché l'istanza `CircularString` non è valida. Per altre informazioni su validi `CircularString` e `LineString` istanze, vedere [CircularString](circularstring.md) e [LineString](linestring.md).  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-instantiating-a-geometry-instance-with-an-empty-compooundcurve"></a>A. Creazione di un'istanza Geometry con un'istanza CompoundCurve vuota  
 Nell'esempio seguente viene illustrato come creare un'istanza `CompoundCurve` vuota:  
  
```tsql  
DECLARE @g geometry;  
SET @g = geometry::Parse('COMPOUNDCURVE EMPTY');  
```  
  
### <a name="b-declaring-and-instantiating-a-geometry-instance-using-a-compoundcurve-in-the-same-statement"></a>B. Dichiarazione e creazione di un'istanza Geometry utilizzando un'istanza CompoundCurve nella stessa istruzione  
 L'esempio seguente illustra come dichiarare e inizializzare un'istanza `geometry` con un'istanza `CompoundCurve`nella stessa istruzione:  
  
```tsql  
DECLARE @g geometry = 'COMPOUNDCURVE ((2 2, 0 0),CIRCULARSTRING (0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0))';  
```  
  
### <a name="c-instantiating-a-geography-instance-with-a-compoundcurve"></a>C. Creazione di un'istanza Geography con un'istanza CompoundCurve  
 Nell'esempio seguente viene illustrato come dichiarare e inizializzare un'istanza `geography` con un'istanza `CompoundCurve`:  
  
```tsql  
DECLARE @g geography = 'COMPOUNDCURVE(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
```  
  
### <a name="d-storing-a-square-in-a-compoundcurve-instance"></a>D. Archiviazione di un quadrato in un'istanza CompoundCurve  
 Nell'esempio seguente vengono utilizzate due diverse modalità per archiviare un quadrato tramite un'istanza `CompoundCurve` .  
  
```tsql  
DECLARE @g1 geometry, @g2 geometry;  
SET @g1 = geometry::Parse('COMPOUNDCURVE((1 1, 1 3), (1 3, 3 3),(3 3, 3 1), (3 1, 1 1))');  
SET @g2 = geometry::Parse('COMPOUNDCURVE((1 1, 1 3, 3 3, 3 1, 1 1))');  
SELECT @g1.STLength(), @g2.STLength();  
```  
  
 Le lunghezze per `@g1` e `@g2` sono le stesse. Nell'esempio che un `CompoundCurve` istanza può archiviare una o più istanze di `LineString`.  
  
### <a name="e-instantiating-a-geometry-instance-using-a-compoundcurve-with-multiple-circularstrings"></a>E. Creazione di un'istanza Geometry utilizzando un'istanza CompoundCurve con più istanze CircularString  
 Nell'esempio seguente viene illustrato come utilizzare due diverse istanze `CircularString` per creare un'istanza `CompoundCurve`:  
  
```tsql  
DECLARE @g geometry;  
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), CIRCULARSTRING(4 2, 2 4, 0 2))');  
SELECT @g.STLength();  
```  
  
 Viene prodotto l'output seguente:12.566370… equivalente a 4∏. L'istanza `CompoundCurve` riportata nell'esempio consente di archiviare un cerchio con un raggio di 2. In entrambi gli esempi di codice precedenti non è stato necessario utilizzare un'istanza `CompoundCurve`. Per il primo esempio sarebbe stata più semplice un'istanza `LineString` , mentre per il secondo esempio sarebbe stata più semplice un'istanza `CircularString` . Nell'esempio successivo viene tuttavia illustrato in quale punto un'istanza `CompoundCurve` costituisce una migliore alternativa.  
  
### <a name="f-using-a-compoundcurve-to-store-a-semicircle"></a>F. Utilizzo di un'istanza CompoundCurve per archiviare un semicerchio  
 Nell'esempio seguente viene utilizzata un'istanza `CompoundCurve` per archiviare un semicerchio.  
  
```tsql  
DECLARE @g geometry;  
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), (4 2, 0 2))');  
SELECT @g.STLength();  
```  
  
### <a name="g-storing-multiple-circularstring-and-linestring-instances-in-a-compoundcurve"></a>G. Archiviazione di più istanze CircularString e LineString in un'istanza CompoundCurve  
 Nell'esempio seguente viene illustrato come è possibile archiviare più istanze `CircularString` e `LineString` tramite un'istanza `CompoundCurve`.  
  
```tsql  
DECLARE @g geometry  
SET @g = geometry::Parse('COMPOUNDCURVE((3 5, 3 3), CIRCULARSTRING(3 3, 5 1, 7 3), (7 3, 7 5), CIRCULARSTRING(7 5, 5 7, 3 5))');  
SELECT @g.STLength();  
```  
  
### <a name="h-storing-instances-with-z-and-m-values"></a>H. Archiviazione di istanze con valori Z e M  
 Nell'esempio seguente viene illustrato come utilizzare un'istanza `CompoundCurve` per archiviare una sequenza di istanze `CircularString` e `LineString` con valori Z e M.  
  
```tsql  
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(7 5 4 2, 5 7 4 2, 3 5 4 2), (3 5 4 2, 8 7 4 2))');  
```  
  
### <a name="i-illustrating-why-circularstring-instances-must-be-explicitly-declared"></a>I. Descrizione del motivo per cui le istanze CircularString devono essere dichiarate in modo esplicito  
 Nell'esempio seguente viene illustrato il motivo per cui è necessario dichiarare in modo esplicito le istanze `CircularString` . Il programmatore sta tentando di archiviare un cerchio in un'istanza `CompoundCurve` .  
  
```tsql  
DECLARE @g1 geometry;    
DECLARE @g2 geometry;  
SET @g1 = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), (4 2, 2 4, 0 2))');  
SELECT 'Circle One', @g1.STLength() AS Perimeter;  -- gives an inaccurate amount  
SET @g2 = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), CIRCULARSTRING(4 2, 2 4, 0 2))');  
SELECT 'Circle Two', @g2.STLength() AS Perimeter;  -- now we get an accurate amount  
```  
  
 L'output è il seguente:  
  
```  
Circle One11.940039…  
Circle Two12.566370…  
```  
  
 Il perimetro di Circle Two è approssimativamente 4∏, che corrisponde al valore effettivo per il perimetro. Il perimetro per Circle One, tuttavia, è significativamente impreciso. L'istanza `CompoundCurve` di Circle One consente l'archiviazione di un segmento di arco circolare (ABC) e di due segmenti di linea (CD, DA). Tramite l'istanza `CompoundCurve` devono essere archiviati due segmenti di arco circolare (ABC, CDA) per definire un cerchio. Tramite un'istanza `LineString` viene definito il secondo set di punti (4 2, 2 4, 0 2) nell'istanza `CompoundCurve` di Circle One. È necessario dichiarare in modo esplicito un'istanza `CircularString` in un'istanza `CompoundCurve`.  
  
## <a name="see-also"></a>Vedere anche  
 [STIsValid &#40;tipo di dati geometry&#41;](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type)   
 [STLength &#40;tipo di dati geometry&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type)   
 [STStartPoint &#40;tipo di dati geometry&#41;](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type)   
 [STEndpoint &#40;tipo di dati geometry&#41;](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type)   
 [LineString](linestring.md)   
 [CircularString](circularstring.md)   
 [Panoramica dei tipi di dati spaziali](spatial-data-types-overview.md)   
 [Point](point.md)  
  
  
