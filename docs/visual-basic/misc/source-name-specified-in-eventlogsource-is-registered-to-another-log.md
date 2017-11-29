---
title: "Nazwa źródła w parametru EventLogSource jest zarejestrowana w dzienniku inną niż określona w EventLogName"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 7317e100-098b-408d-86e5-7c74cf8558c7
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c190caa7634760c2e4dc4a2bb7a9a09f532eb0ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="source-name-specified-in-eventlogsource-is-registered-to-a-log-other-than-that-specified-in-eventlogname"></a><span data-ttu-id="0212b-102">Nazwa źródła w parametru EventLogSource jest zarejestrowana w dzienniku inną niż określona w EventLogName</span><span class="sxs-lookup"><span data-stu-id="0212b-102">Source name specified in EventLogSource is registered to a log other than that specified in EventLogName</span></span>
<span data-ttu-id="0212b-103">`EventLog` Próbuje odwołać się do źródła, które jest zarejestrowany na inny dziennik.</span><span class="sxs-lookup"><span data-stu-id="0212b-103">The `EventLog` is attempting to refer to a source that is registered to a different log.</span></span> <span data-ttu-id="0212b-104">Jeśli piszesz wpisów do dziennika zdarzeń, należy określić <xref:System.Diagnostics.EventLog.Source%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="0212b-104">If you are writing entries to an event log, you must specify the <xref:System.Diagnostics.EventLog.Source%2A> property.</span></span> <span data-ttu-id="0212b-105"><xref:System.Diagnostics.EventLog.Source%2A> Właściwość rejestruje składnika z dziennika zdarzeń jako prawidłowe źródło wpisów.</span><span class="sxs-lookup"><span data-stu-id="0212b-105">The <xref:System.Diagnostics.EventLog.Source%2A> property registers your component with the event log as a valid source of entries.</span></span> <span data-ttu-id="0212b-106">Jedno źródło może być skojarzony z (i w związku z tym zapisywanie wpisów do) tylko jeden dziennika zdarzeń w czasie.</span><span class="sxs-lookup"><span data-stu-id="0212b-106">A single source can be associated with (and therefore write entries to) only one event log at a time.</span></span>  
  
 <span data-ttu-id="0212b-107">Domyślnie przy próbie zapisu bez najpierw o zarejestrowany składnik jako prawidłowe źródło, system automatycznie rejestruje źródło dziennika zdarzeń, używając wartości <xref:System.Diagnostics.EventLog.Source%2A> właściwość jako ciąg źródła.</span><span class="sxs-lookup"><span data-stu-id="0212b-107">By default, if you try to write an entry without first having registered your component as a valid source, the system automatically registers the source with the event log, using the value of the <xref:System.Diagnostics.EventLog.Source%2A> property as the source string.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0212b-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="0212b-108">To correct this error</span></span>  
  
-   <span data-ttu-id="0212b-109">Upewnij się, że źródło jest zarejestrowany w dzienniku poprawne.</span><span class="sxs-lookup"><span data-stu-id="0212b-109">Make sure the source is registered to the correct log.</span></span> <span data-ttu-id="0212b-110">Aby to zrobić, użyj <xref:System.Diagnostics.EventLog.CreateEventSource%2A> metody lub jeden z jego przeciążenia, aby określić ciąg, który unikatowo identyfikuje składnika w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0212b-110">To do this, use the <xref:System.Diagnostics.EventLog.CreateEventSource%2A> method or one of its overloads to specify a string that uniquely identifies your component to the event log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0212b-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0212b-111">See Also</span></span>  
 [<span data-ttu-id="0212b-112">Administrowanie dzienniki zdarzeń</span><span class="sxs-lookup"><span data-stu-id="0212b-112">Administering Event Logs</span></span>](http://msdn.microsoft.com/en-us/35f53238-bdd2-417b-acd8-2fd9f7397f18)  
 [<span data-ttu-id="0212b-113">Odwołania do dziennika zdarzeń</span><span class="sxs-lookup"><span data-stu-id="0212b-113">Event Log References</span></span>](http://msdn.microsoft.com/en-us/4af0661c-6c96-49f4-961d-b26ed9bc3e87)  
 [<span data-ttu-id="0212b-114">Porady: Dodawanie aplikacji jako źródło wpisów dziennika zdarzeń</span><span class="sxs-lookup"><span data-stu-id="0212b-114">How to: Add Your Application as a Source of Event Log Entries</span></span>](http://msdn.microsoft.com/en-us/948ff920-a739-4e66-a191-ee951512d42c)  
 [<span data-ttu-id="0212b-115">Porady: usuwanie źródłem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="0212b-115">How to: Remove an Event Source</span></span>](http://msdn.microsoft.com/en-us/bc66c900-4b8a-426a-b8e2-17031a20167e)