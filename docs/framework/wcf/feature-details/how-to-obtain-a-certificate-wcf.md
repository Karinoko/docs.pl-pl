---
title: 'Instrukcje: Uzyskiwanie certyfikatu (WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: 664eb62997123ea248b0b69700b86bf794646d4b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519225"
---
# <a name="how-to-obtain-a-certificate-wcf"></a>Instrukcje: Uzyskiwanie certyfikatu (WCF)
Aby użyć dowolnego narzędzia Windows Communication Foundation (WCF) funkcji, które używają certyfikatów X.509, po prostu najpierw uzyskać certyfikaty.  
  
### <a name="to-obtain-an-x509-certificate"></a>Aby uzyskać certyfikat X.509  
  
1.  Wybierz jedną z następujących opcji:  
  
    -   Kup certyfikat od urzędu certyfikacji, takich jak VeriSign, Inc.  
  
    -   Skonfigurować usługi certyfikatów i podpisywania certyfikatów urzędu certyfikacji. [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], Windows 2000 Server, Windows 2000 Server Datacenter oraz Windows 2000 Datacenter Server uwzględnienia usług certyfikatów, które obsługują infrastruktury kluczy publicznych (PKI). W systemie Windows Server 2008, należy użyć [usług certyfikatów Active Directory](https://go.microsoft.com/fwlink/?LinkID=153483) roli do zarządzania urzędem certyfikacji.  
  
    -   Skonfiguruj usługi certyfikatów i czy nie ma certyfikatów podpisany.  
  
    > [!NOTE]
    >  Niezależnie od tego podejścia, odbiorca żądania SOAP, który zawiera certyfikat X.509, muszą ufać certyfikatu X.509. Oznacza to, że certyfikat X.509 lub wystawcy w łańcuchu certyfikatów znajduje się w magazynie certyfikatów zaufanych osób i że certyfikat X.509 nie znajduje się w magazynie certyfikatów niezaufanych.  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Instrukcje: tworzenie certyfikatów tymczasowych do używania w trakcie opracowywania](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
