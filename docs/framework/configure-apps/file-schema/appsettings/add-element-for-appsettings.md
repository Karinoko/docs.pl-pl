---
title: '&lt;Dodaj&gt; elementu &lt;appSettings&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
author: guardrex
ms.author: mairaw
ms.openlocfilehash: e74f0956dd5acebccee87fd6ad8c09b299badffd
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194348"
---
# <a name="add-element-for-appsettings"></a>\<Dodaj >, element dla \<appSettings >

Dodaje ustawienia aplikacji niestandardowych.

[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<Dodaj >**

## <a name="syntax"></a>Składnia

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a>Atrybuty

|           | Opis |
| --------- | ----------- |
| **Klucz**   | Atrybut wymagany.<br><br>Określa nazwę klucz do dodania. |
| **value** | Atrybut wymagany.<br><br>Określa wartość klucz do dodania. |

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ----------- |
| [**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | Zawiera ustawienia aplikacji niestandardowych, takich jak ścieżki do plików, adresy URL usługi sieci Web XML lub inne informacje konfiguracji niestandardowej dla aplikacji. |

## <a name="child-elements"></a>Elementy podrzędne

Brak

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak dodać ustawienie Konfiguracja niestandardowa nazwa aplikacji:

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

W poniższym przykładzie użyto `<add>` elementu, aby zdefiniować dwa ustawienia zgodności w aplikacji ASP.NET:

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="see-also"></a>Zobacz także

- [Schemat pliku konfiguracji dla programu .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
