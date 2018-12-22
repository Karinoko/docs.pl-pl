---
title: Tabela typów całkowitych - C# odwołania
ms.custom: seodec18
description: Omówienie wbudowanego języka C# typy całkowite
ms.date: 08/20/2018
helpviewer_keywords:
- integral types, C#
- Visual C#, integral types
- types [C#], integral types
- ranges of integral types [C#]
ms.assetid: 62e86126-46ff-40b0-9028-e61d7558268c
ms.openlocfilehash: 1815f057e5cf26d64e5ff151f161cc56214efc1b
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237990"
---
# <a name="integral-types-table-c-reference"></a>Tabela typów całkowitych (odwołanie w C#)

W poniższej tabeli przedstawiono rozmiary i zakresy typów całkowitych, które stanowią podzbiór typów prostych.  
  
|Typ|Zakres|Rozmiar|  
|----------|-----------|----------|  
|[sbyte](sbyte.md)|-128 do 127 znaków.|8-bitowa liczba całkowita ze znakiem|  
|[byte](byte.md)|0 do 255|8-bitowa liczba całkowita bez znaku|  
|[char](char.md)|U + 0000 do U + ffff|16-bitowy znak Unicode|  
|[short](short.md)|-32,768 do 32,767.|16-bitową liczbę całkowitą ze znakiem|  
|[ushort](ushort.md)|0 do 65,535.|Liczba całkowita bez znaku 16-bitowych|  
|[int](int.md)|-2,147,483,648 do 2,147,483,647|32-bitowa liczba całkowita ze znakiem|  
|[uint](uint.md)|0 do 4,294,967,295|Liczba całkowita bez znaku 32-bitowy|  
|[long](long.md)|-9,223,372,036,854,775,808 do 9,223,372,036,854,775,807|64-bitowa liczba całkowita ze znakiem|  
|[ulong](ulong.md)|0 do 18,446,744,073,709,551,615|64-bitowa liczba całkowita bez znaku|  

## <a name="remarks"></a>Uwagi
  
Jeśli wartości w postaci literału typu integer przekracza <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, wystąpi błąd kompilatora [CS1021](../../misc/cs1021.md).

Użyj <xref:System.Numerics.BigInteger?displayProperty=nameWithType> klasy do reprezentowania dowolnie dużą całkowita.
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Tabele odwołań dla typów](reference-tables-for-types.md)
- [Tabela typów zmiennoprzecinkowych](floating-point-types-table.md)
- [Tabela wartości domyślnych](default-values-table.md)
- [Formatowanie tabeli wyników liczbowych](formatting-numeric-results-table.md)
- [Tabela typów wbudowanych](built-in-types-table.md)
