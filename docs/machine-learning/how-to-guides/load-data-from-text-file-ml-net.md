---
title: Ładowanie danych z pliku tekstowego, machine learning przetwarzania - strukturze ML.NET
description: Dowiedz się, jak załadować dane z pliku tekstowego do użycia w modelu uczenia maszynowego, kompilowania, szkolenia i oceniania za pomocą platformy ML.NET
ms.date: 11/07/2018
ms.custom: mvc,how-to
ms.openlocfilehash: 7b1e8d3fb6047059c14ec3db8450364a84497219
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155457"
---
# <a name="load-data-from-a-text-file-for-machine-learning-processing---mlnet"></a>Ładowanie danych z pliku tekstowego, machine learning przetwarzania - strukturze ML.NET

`TextLoader` Służy do ładowania danych z plików tekstowych. Należy określić kolumny danych, ich typy i ich lokalizacji w pliku tekstowym.

Należy pamiętać, że doskonale dopuszczalne do odczytu niektórych kolumn w pliku lub przeczytaj tę samą kolumnę wiele razy.

[Przykładowy plik](https://github.com/dotnet/machinelearning/blob/master/test/data/adult.tiny.with-schema.txt):
```
Label   Workclass   education   marital-status
0   Private 11th    Never-married
0   Private HS-grad Married-civ-spouse
1   Local-gov   Assoc-acdm  Married-civ-spouse
1   Private Some-college    Married-civ-spouse
```

Aby załadować dane z pliku tekstowego:

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();
TextLoader textLoader;

// Create the reader: define the data columns and where to find them in the text file.
textLoader = mlContext.Data.TextReader(new TextLoader.Arguments()
{
    Separator = ",",
    HasHeader = true,
    Column = new[]
                {
                    new TextLoader.Column("VendorId", DataKind.Text, 0),
                    new TextLoader.Column("RateCode", DataKind.Text, 1),
                    new TextLoader.Column("PassengerCount", DataKind.R4, 2),
                    new TextLoader.Column("TripTime", DataKind.R4, 3),
                    new TextLoader.Column("TripDistance", DataKind.R4, 4),
                    new TextLoader.Column("PaymentType", DataKind.Text, 5),
                    new TextLoader.Column("FareAmount", DataKind.R4, 6)
                }
}
);

// Now read the file (remember though, readers are lazy, so the reading will happen when the data is accessed).
var data = textLoader.Read(dataPath);
```