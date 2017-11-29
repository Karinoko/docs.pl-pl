---
title: "Obsługa błędów działań w WF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24b68bd3-cef5-4413-ab82-2e2625f209aa
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bcb006f649fe0d2a92b4c789c435ba33916d140f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="error-handling-activities-in-wf"></a><span data-ttu-id="e54c7-102">Obsługa błędów działań w WF</span><span class="sxs-lookup"><span data-stu-id="e54c7-102">Error Handling Activities in WF</span></span>
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]<span data-ttu-id="e54c7-103">Implementowanie obsługi błędów i odzyskiwania zawiera kilka działań dostarczane przez system.</span><span class="sxs-lookup"><span data-stu-id="e54c7-103"> provides several system-provided activities for implementing error handling and recovery.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="e54c7-104">[Wyjątki](../../../docs/framework/windows-workflow-foundation/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="e54c7-104"> [Exceptions](../../../docs/framework/windows-workflow-foundation/exceptions.md).</span></span>  
  
## <a name="error-handling-activities"></a><span data-ttu-id="e54c7-105">Błąd obsługi działań</span><span class="sxs-lookup"><span data-stu-id="e54c7-105">Error handling activities</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.Rethrow>|<span data-ttu-id="e54c7-106">Ponownie zgłasza wyjątek ostatniego z poziomu `TryCatch` działania.</span><span class="sxs-lookup"><span data-stu-id="e54c7-106">Rethrows the last exception thrown from within a `TryCatch` activity.</span></span>|  
|<xref:System.Activities.Statements.Throw>|<span data-ttu-id="e54c7-107">Zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e54c7-107">Throws an exception.</span></span>|  
|<xref:System.Activities.Statements.TryCatch>|<span data-ttu-id="e54c7-108">Implementuje obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="e54c7-108">Implements exception handling.</span></span>|