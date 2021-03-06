---
title: Kolekcje schematów OLE DB
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: 1ab6426875b73b400a59b7e4cf155615d7472d05
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514492"
---
# <a name="ole-db-schema-collections"></a>Kolekcje schematów OLE DB
W tej sekcji omówiono Obsługa kolekcję schematu dla dostawcy OLE DB dla programu Microsoft SQL Server, Oracle i Microsoft Jet.  
  
## <a name="microsoft-sql-server-ole-db-provider"></a>Dostawca programu Microsoft SQL Server OLE DB  
 Sterownik firmy Microsoft SQL Server OLE DB obsługuje następujące kolekcje z określonego schematu, oprócz Typowe kolekcje schematów:  
  
-   Tabele  
  
-   Kolumny  
  
-   Procedury  
  
-   ProcedureParameters  
  
-   Wykaz  
  
-   Indeksy  
  
### <a name="tables"></a>Tabele  
  
|NazwaKolumny|Typ danych|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|TABLE_TYPE|String|  
|TABLE_GUID|Identyfikator GUID|  
|OPIS ELEMENTU|String|  
|TABLE_PROPID|Int64|  
|DATE_CREATED|DataGodzina|  
|DATE_MODIFIED|DataGodzina|  
  
### <a name="columns"></a>Kolumny  
  
|NazwaKolumny|Typ danych|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|COLUMN_NAME|String|  
|COLUMN_GUID|Identyfikator GUID|  
|COLUMN_PROPID|Int64|  
|ORDINAL_POSITION|Int64|  
|COLUMN_HASDEFAULT|Boolean|  
|COLUMN_DEFAULT|String|  
|COLUMN_FLAGS|Int64|  
|IS_NULLABLE|Boolean|  
|DATA_TYPE|Int32|  
|TYPE_GUID|Identyfikator GUID|  
|CHARACTER_MAXIMUM_LENGTH|Int64|  
|CHARACTER_OCTET_LENGTH|Int64|  
|NUMERIC_PRECISION|Int32|  
|NUMERIC_SCALE|Int16|  
|DATETIME_PRECISION|Int64|  
|CHARACTER_SET_CATALOG|String|  
|CHARACTER_SET_SCHEMA|String|  
|CHARACTER_SET_NAME|String|  
|COLLATION_CATALOG|String|  
|COLLATION_SCHEMA|String|  
|COLLATION_NAME|String|  
|DOMAIN_CATALOG|String|  
|DOMAIN_SCHEMA|String|  
|DOMAIN_NAME|String|  
|OPIS ELEMENTU|String|  
|COLUMN_LCID|Int32|  
|COLUMN_COMPFLAGS|Int32|  
|COLUMN_SORTID|Int32|  
|COLUMN_TDSCOLLATION|Byte[]|  
|IS_COMPUTED|Boolean|  
  
### <a name="procedures"></a>Procedury  
  
|NazwaKolumny|Typ danych|  
|----------------|--------------|  
|PROCEDURE_CATALOG|String|  
|PROCEDURE_SCHEMA|String|  
|PROCEDURE_NAME|String|  
|PROCEDURE_TYPE|Int16|  
|PROCEDURE_DEFINITION|String|  
|OPIS ELEMENTU|String|  
|DATE_CREATED|DataGodzina|  
|DATE_MODIFIED|DataGodzina|  
  
### <a name="procedureparameters"></a>ProcedureParameters  
  
|NazwaKolumny|Typ danych|  
|----------------|--------------|  
|PROCEDURE_CATALOG|String|  
|PROCEDURE_SCHEMA|String|  
|PROCEDURE_NAME|String|  
|PARAMETER_NAME|String|  
|ORDINAL_POSITION|Int32|  
|TYP_PARAMETRU|Int32|  
|PARAMETER_HASDEFAULT|Boolean|  
|PARAMETER_DEFAULT|String|  
|IS_NULLABLE|Boolean|  
|DATA_TYPE|Int32|  
|CHARACTER_MAXIMUM_LENGTH|Int64|  
|CHARACTER_OCTET_LENGTH|Int64|  
|NUMERIC_PRECISION|Int32|  
|NUMERIC_SCALE|Int16|  
|OPIS ELEMENTU|String|  
|TYPE_NAME|String|  
|LOCAL_TYPE_NAME|String|  
  
### <a name="catalog"></a>Wykaz  
  
|NazwaKolumny|Typ danych|  
|----------------|--------------|  
|CATALOG_NAME|String|  
|OPIS ELEMENTU|String|  
  
### <a name="indexes"></a>Indeksy  
  
|NazwaKolumny|Typ danych|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|INDEX_CATALOG|String|  
|INDEX_SCHEMA|String|  
|INDEX_NAME|String|  
|PRIMARY_KEY|Boolean|  
|UNIQUE|Boolean|  
|CLUSTERED|Boolean|  
|TYP|Int32|  
|FILL_FACTOR|Int32|  
|INITIAL_SIZE|Int32|  
|NULL — Wartości|Int32|  
|SORT_BOOKMARKS|Boolean|  
|AUTO_UPDATE|Boolean|  
|NULL_COLLATION|Int32|  
|ORDINAL_POSITION|Int64|  
|COLUMN_NAME|String|  
|COLUMN_GUID|Identyfikator GUID|  
|COLUMN_PROPID|Int64|  
|SORTOWANIE|Int16|  
|KARDYNALNOŚĆ|Wartość dziesiętna|  
|STRONY|Int32|  
|FILTER_CONDITION|String|  
|ZINTEGROWANE|Boolean|  
  
## <a name="microsoft-oracle-ole-db-provider"></a>Dostawca programu Microsoft Oracle OLE DB  
 Sterownik firmy Microsoft Oracle OLE DB obsługuje następujące kolekcje z określonego schematu, oprócz Typowe kolekcje schematów:  
  
-   Tabele  
  
-   Kolumny  
  
-   Procedury  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   Widoki  
  
-   Indeksy  
  
### <a name="tables"></a>Tabele  
  
|NazwaKolumny|Typ danych|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|TABLE_TYPE|String|  
|TABLE_GUID|Identyfikator GUID|  
|OPIS ELEMENTU|String|  
|TABLE_PROPID|Int64|  
|DATE_CREATED|DataGodzina|  
|DATE_MODIFIED|DataGodzina|  
  
### <a name="columns"></a>Kolumny  
  
|NazwaKolumny|Typ danych|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|COLUMN_NAME|String|  
|COLUMN_GUID|Identyfikator GUID|  
|COLUMN_PROPID|Int64|  
|ORDINAL_POSITION|Int64|  
|COLUMN_HASDEFAULT|Boolean|  
|COLUMN_DEFAULT|String|  
|COLUMN_FLAGS|Int64|  
|IS_NULLABLE|Boolean|  
|DATA_TYPE|Int32|  
|TYPE_GUID|Identyfikator GUID|  
|CHARACTER_MAXIMUM_LENGTH|Int64|  
|CHARACTER_OCTET_LENGTH|Int64|  
|NUMERIC_PRECISION|Int32|  
|NUMERIC_SCALE|Int16|  
|DATETIME_PRECISION|Int64|  
|CHARACTER_SET_CATALOG|String|  
|CHARACTER_SET_SCHEMA|String|  
|CHARACTER_SET_NAME|String|  
|COLLATION_CATALOG|String|  
|COLLATION_SCHEMA|String|  
|COLLATION_NAME|String|  
|DOMAIN_CATALOG|String|  
|DOMAIN_SCHEMA|String|  
|DOMAIN_NAME|String|  
|OPIS ELEMENTU|String|  
  
### <a name="procedures"></a>Procedury  
  
|NazwaKolumny|Typ danych|  
|----------------|--------------|  
|PROCEDURE_CATALOG|String|  
|PROCEDURE_SCHEMA|String|  
|PROCEDURE_NAME|String|  
|PROCEDURE_TYPE|Int16|  
|PROCEDURE_DEFINITION|String|  
|OPIS ELEMENTU|String|  
|DATE_CREATED|DataGodzina|  
|DATE_MODIFIED|DataGodzina|  
  
### <a name="procedurecolumns"></a>ProcedureColumns  
  
|NazwaKolumny|Typ danych|  
|----------------|--------------|  
|PROCEDURE_CATALOG|String|  
|PROCEDURE_SCHEMA|String|  
|PROCEDURE_NAME|String|  
|COLUMN_NAME|String|  
|COLUMN_GUID|Identyfikator GUID|  
|COLUMN_PROPID|Int64|  
|ROWSET_NUMBER|Int64|  
|ORDINAL_POSITION|Int64|  
|IS_NULLABLE|Boolean|  
|DATA_TYPE|Int32|  
|TYPE_GUID|Identyfikator GUID|  
|CHARACTER_MAXIMUM_LENGTH|Int64|  
|CHARACTER_OCTET_LENGTH|Int64|  
|NUMERIC_PRECISION|Int32|  
|NUMERIC_SCALE|Int16|  
|OPIS ELEMENTU|String|  
|PRZECIĄŻENIE|Int16|  
  
### <a name="views"></a>Widoki  
  
|NazwaKolumny|Typ danych|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|VIEW_DEFINITION|String|  
|CHECK_OPTION|Boolean|  
|IS_UPDATABLE|Boolean|  
|OPIS ELEMENTU|String|  
|DATE_CREATED|DataGodzina|  
|DATE_MODIFIED|DataGodzina|  
  
### <a name="indexes"></a>Indeksy  
  
|NazwaKolumny|Typ danych|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|INDEX_CATALOG|String|  
|INDEX_SCHEMA|String|  
|INDEX_NAME|String|  
|PRIMARY_KEY|Boolean|  
|UNIQUE|Boolean|  
|CLUSTERED|Boolean|  
|TYP|Int32|  
|FILL_FACTOR|Int32|  
|INITIAL_SIZE|Int32|  
|NULL — Wartości|Int32|  
|SORT_BOOKMARKS|Boolean|  
|AUTO_UPDATE|Boolean|  
|NULL_COLLATION|Int32|  
|ORDINAL_POSITION|Int64|  
|COLUMN_NAME|String|  
|COLUMN_GUID|Identyfikator GUID|  
|COLUMN_PROPID|Int64|  
|SORTOWANIE|Int16|  
|KARDYNALNOŚĆ|Wartość dziesiętna|  
|STRONY|Int32|  
|FILTER_CONDITION|String|  
|ZINTEGROWANE|Boolean|  
  
## <a name="microsoft-jet-ole-db-provider"></a>Dostawca programu Microsoft Jet OLE DB  
 Sterownik firmy Microsoft Jet OLE DB obsługuje następujące kolekcje z określonego schematu, oprócz Typowe kolekcje schematów:  
  
-   Tabele  
  
-   Kolumny  
  
-   Procedury  
  
-   Widoki  
  
-   Indeksy  
  
### <a name="tables"></a>Tabele  
  
|NazwaKolumny|Typ danych|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|TABLE_TYPE|String|  
|TABLE_GUID|Identyfikator GUID|  
|OPIS ELEMENTU|String|  
|TABLE_PROPID|Int64|  
|DATE_CREATED|DataGodzina|  
|DATE_MODIFIED|DataGodzina|  
  
### <a name="columns"></a>Kolumny  
  
|NazwaKolumny|Typ danych|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|COLUMN_NAME|String|  
|COLUMN_GUID|Identyfikator GUID|  
|COLUMN_PROPID|Int64|  
|ORDINAL_POSITION|Int64|  
|COLUMN_HASDEFAULT|Boolean|  
|COLUMN_DEFAULT|String|  
|COLUMN_FLAGS|Int64|  
|IS_NULLABLE|Boolean|  
|DATA_TYPE|Int32|  
|TYPE_GUID|Identyfikator GUID|  
|CHARACTER_MAXIMUM_LENGTH|Int64|  
|CHARACTER_OCTET_LENGTH|Int64|  
|NUMERIC_PRECISION|Int32|  
|NUMERIC_SCALE|Int16|  
|DATETIME_PRECISION|Int64|  
|CHARACTER_SET_CATALOG|String|  
|CHARACTER_SET_SCHEMA|String|  
|CHARACTER_SET_NAME|String|  
|COLLATION_CATALOG|String|  
|COLLATION_SCHEMA|String|  
|COLLATION_NAME|String|  
|DOMAIN_CATALOG|String|  
|DOMAIN_SCHEMA|String|  
|DOMAIN_NAME|String|  
|OPIS ELEMENTU|String|  
  
### <a name="procedures"></a>Procedury  
  
|NazwaKolumny|Typ danych|  
|----------------|--------------|  
|PROCEDURE_CATALOG|String|  
|PROCEDURE_SCHEMA|String|  
|PROCEDURE_NAME|String|  
|PROCEDURE_TYPE|Int16|  
|PROCEDURE_DEFINITION|String|  
|OPIS ELEMENTU|String|  
|DATE_CREATED|DataGodzina|  
|DATE_MODIFIED|DataGodzina|  
  
### <a name="views"></a>Widoki  
  
|NazwaKolumny|Typ danych|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|VIEW_DEFINITION|String|  
|CHECK_OPTION|Boolean|  
|IS_UPDATABLE|Boolean|  
|OPIS ELEMENTU|String|  
|DATE_CREATED|DataGodzina|  
|DATE_MODIFIED|DataGodzina|  
  
### <a name="indexes"></a>Indeksy  
  
|NazwaKolumny|Typ danych|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|INDEX_CATALOG|String|  
|INDEX_SCHEMA|String|  
|INDEX_NAME|String|  
|PRIMARY_KEY|Boolean|  
|UNIQUE|Boolean|  
|CLUSTERED|Boolean|  
|TYP|Int32|  
|FILL_FACTOR|Int32|  
|INITIAL_SIZE|Int32|  
|NULL — Wartości|Int32|  
|SORT_BOOKMARKS|Boolean|  
|AUTO_UPDATE|Boolean|  
|NULL_COLLATION|Int32|  
|ORDINAL_POSITION|Int64|  
|COLUMN_NAME|String|  
|COLUMN_GUID|Identyfikator GUID|  
|COLUMN_PROPID|Int64|  
|SORTOWANIE|Int16|  
|KARDYNALNOŚĆ|Wartość dziesiętna|  
|STRONY|Int32|  
|FILTER_CONDITION|String|  
|ZINTEGROWANE|Boolean|  
  
## <a name="see-also"></a>Zobacz też  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
