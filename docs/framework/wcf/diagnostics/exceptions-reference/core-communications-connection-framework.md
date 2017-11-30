---
title: "Podstawowe wiadomości: Struktura połączenia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61ee00e1-896d-47c8-942f-1db28ac89cdc
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c485c05c1c54a19a102a8378dc79c908a29aa658
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="core-communications-connection-framework"></a><span data-ttu-id="96e8c-102">Podstawowe wiadomości: Struktura połączenia</span><span class="sxs-lookup"><span data-stu-id="96e8c-102">Core Communications: Connection Framework</span></span>
<span data-ttu-id="96e8c-103">W tym temacie wymieniono wszystkie wyjątki generowane przez [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] struktura połączenia.</span><span class="sxs-lookup"><span data-stu-id="96e8c-103">This topic lists all exceptions generated by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Connection Framework.</span></span>  
  
## <a name="exception-list"></a><span data-ttu-id="96e8c-104">Listy wyjątków</span><span class="sxs-lookup"><span data-stu-id="96e8c-104">Exception List</span></span>  
  
|<span data-ttu-id="96e8c-105">Kod zasobu</span><span class="sxs-lookup"><span data-stu-id="96e8c-105">Resource Code</span></span>|<span data-ttu-id="96e8c-106">Ciąg zasobu</span><span class="sxs-lookup"><span data-stu-id="96e8c-106">Resource String</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="96e8c-107">CloseTimedOut</span><span class="sxs-lookup"><span data-stu-id="96e8c-107">CloseTimedOut</span></span>|<span data-ttu-id="96e8c-108">Close — metoda, przekroczono limit czasu po upływie określonego czasu.</span><span class="sxs-lookup"><span data-stu-id="96e8c-108">The Close method timed out after the specified time.</span></span> <span data-ttu-id="96e8c-109">Zwiększ wartość limitu czasu przekazywaną w wywołaniu Close lub wartość CloseTimeout w obiekcie w powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="96e8c-109">Increase the timeout value that is passed to the call to Close or increase the CloseTimeout value on the binding.</span></span> <span data-ttu-id="96e8c-110">Czas przydzielony na tę operację mógł stanowi część większego limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="96e8c-110">The time allotted to this operation may have been a portion of a longer timeout.</span></span>|  
|<span data-ttu-id="96e8c-111">ContentTypeMismatch</span><span class="sxs-lookup"><span data-stu-id="96e8c-111">ContentTypeMismatch</span></span>|<span data-ttu-id="96e8c-112">Określony typ zawartości został wysłany do usługi, która oczekiwała określony.</span><span class="sxs-lookup"><span data-stu-id="96e8c-112">The specified content type was sent to a service that was expecting the specified.</span></span> <span data-ttu-id="96e8c-113">Powiązania klienta i usługi mogą być niezgodne.</span><span class="sxs-lookup"><span data-stu-id="96e8c-113">The client and service bindings may be mismatched.</span></span>|  
|<span data-ttu-id="96e8c-114">DuplexChannelAbortedDuringOpen</span><span class="sxs-lookup"><span data-stu-id="96e8c-114">DuplexChannelAbortedDuringOpen</span></span>|<span data-ttu-id="96e8c-115">Kanał dupleksowy do określonego została zakończona podczas procesu otwierania.</span><span class="sxs-lookup"><span data-stu-id="96e8c-115">The duplex channel to the specified terminated during the Open process.</span></span>|  
|<span data-ttu-id="96e8c-116">FramingValueNotAvailable</span><span class="sxs-lookup"><span data-stu-id="96e8c-116">FramingValueNotAvailable</span></span>|<span data-ttu-id="96e8c-117">Wartość nie jest dostępny, ponieważ nie jest całkowicie zdekodować.</span><span class="sxs-lookup"><span data-stu-id="96e8c-117">The value cannot be accessed because it is not fully decoded.</span></span>|  
|<span data-ttu-id="96e8c-118">OperationAbortedDuringConnectionEstablishment</span><span class="sxs-lookup"><span data-stu-id="96e8c-118">OperationAbortedDuringConnectionEstablishment</span></span>|<span data-ttu-id="96e8c-119">Operacja została zakończona podczas nawiązywania połączenia z określonym.</span><span class="sxs-lookup"><span data-stu-id="96e8c-119">The operation was terminated while establishing a connection to the specified.</span></span>|  
|<span data-ttu-id="96e8c-120">ReceiveTimedOut2</span><span class="sxs-lookup"><span data-stu-id="96e8c-120">ReceiveTimedOut2</span></span>|<span data-ttu-id="96e8c-121">Operacja odbioru został przekroczony po określonym czasie.</span><span class="sxs-lookup"><span data-stu-id="96e8c-121">The receive operation has timed out after the specified time.</span></span> <span data-ttu-id="96e8c-122">Czas przydzielony na tę operację mógł stanowi część większego limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="96e8c-122">The time allotted to this operation may have been a portion of a longer timeout.</span></span>|  
|<span data-ttu-id="96e8c-123">SendCannotBeCalledAfterCloseOutputSession</span><span class="sxs-lookup"><span data-stu-id="96e8c-123">SendCannotBeCalledAfterCloseOutputSession</span></span>|<span data-ttu-id="96e8c-124">Nie można wysłać wiadomości kanałem po wywołaniu CloseOutputSession.</span><span class="sxs-lookup"><span data-stu-id="96e8c-124">You cannot send messages on a channel after CloseOutputSession has been called.</span></span>|