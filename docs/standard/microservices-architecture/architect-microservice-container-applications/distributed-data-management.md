---
title: Problemy i rozwiązania dotyczące rozproszonego zarządzania danymi
description: Dowiedz się, jakie są problemy i rozwiązania dotyczące rozproszonego zarządzania danymi w świecie mikrousług.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: adfb3c0be33d18a991ee552a99a2d02cc3ec7bb3
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53151034"
---
# <a name="challenges-and-solutions-for-distributed-data-management"></a>Problemy i rozwiązania dotyczące rozproszonego zarządzania danymi

## <a name="challenge-1-how-to-define-the-boundaries-of-each-microservice"></a>Wyzwanie \#1: Jak zdefiniować granice poszczególne mikrousługi

Definiowanie granic mikrousługi prawdopodobnie jest pierwsze wyzwanie, z których każda osoba napotka. Każda mikrousługa musi być częścią aplikacji, a każda mikrousługa powinna być autonomicznego przy użyciu wszystkich korzyści i problemy, które wywołuje. Ale jak można zidentyfikować te granice?

Najpierw należy skoncentrować się na modeli domeny logiczne i powiązane dane aplikacji. Spróbuj zidentyfikować Wyspy rozdzieleniu danych i kontekstów w tej samej aplikacji. W każdym kontekście może mieć różnych firm język (warunki różnych firm). Konteksty powinien być zdefiniowane i zarządzane niezależnie. Warunki i jednostek, które są używane w tych różnych kontekstach może brzmią podobnie, ale może być odnajdywanie, że w szczególnym kontekście koncepcji biznesowych z jedną służy do różnych celów w innym kontekście, a nawet może mieć inną nazwę. Na przykład przez użytkownika mogą być określane jako użytkownika w tożsamości lub członkostwo w kontekście jako klient w kontekście CRM kupującym w kontekście sortowania i tak dalej.

Sposób identyfikacji granic między wiele kontekstów aplikacji z innej domeny, dla każdego kontekstu jest dokładnie, jak można zidentyfikować granice poszczególne mikrousługi firmy i jej powiązane danych i modelu domeny. Zawsze próbować zminimalizować sprzężenie między tymi mikrousług. Ten przewodnik zawiera bardziej szczegółowe o ten projekt modelu identyfikacji i domeny w sekcji [identyfikowanie ograniczeń modelu domeny dla poszczególnych mikrousług](identify-microservice-domain-model-boundaries.md) później.

## <a name="challenge-2-how-to-create-queries-that-retrieve-data-from-several-microservices"></a>Wyzwanie \#2: Jak tworzyć zapytania, które pobierają dane z wielu mikrousług

Drugi wyzwaniem jest sposób implementacji zapytań, które pobierają dane z wielu mikrousług, unikając do mikrousług nasilenie komunikacji z klientem zdalnym aplikacji. Przykładem może być jednego ekranu z aplikacji mobilnej, który wymaga, aby wyświetlić informacje o użytkowniku, który jest własnością mikrousług tożsamości koszyka, wykazu i użytkownika. Innym przykładem może być złożonych raportów, obejmujących wiele tabel znajdujących się w wielu mikrousługach. Rozwiązanie zaspokajające zależy od złożoności zapytania. Ale w każdym przypadku, będziesz potrzebować sposób agregują informacje, jeśli chcesz zwiększyć wydajność w komunikacji systemu. Najbardziej popularne rozwiązania są następujące.

**Brama interfejsu API.** Agregacji proste dane z wielu mikrousług, którego właścicielem różnych baz danych Zalecanym podejściem jest mikrousług agregacji, określany jako bramy interfejsu API. Jednak należy zachować ostrożność w przypadku implementowania tego wzorca, ponieważ może być punktem urządzenie rozruchowe w systemie, a jej naruszać zasady Autonomia mikrousług. Aby uniknąć tej możliwości, może mieć wiele bram API karę szczegółowej każdy jeden koncentrujące się na "wycinka" w pionie lub obszar działalności systemu. Wzorzec bramy interfejsu API jest omówione bardziej szczegółowo w [sekcji bramy interfejsu API](direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md#why-consider-api-gateways-instead-of-direct-client-to-microservice-communication) później.

**Podejście CQRS z tabelami w operacji zapytania/odczytu.** Innym rozwiązaniem do agregowania danych z wielu mikrousług jest [użycia wzorca zmaterializowanego widoku](https://docs.microsoft.com/azure/architecture/patterns/materialized-view). W tym podejściu użytkownik Generowanie z wyprzedzeniem (przygotować dane denormalizowane, przed wystąpieniem rzeczywiste zapytań), tylko do odczytu tabelę z danymi, która jest właścicielem przez wiele mikrousług. Tabela ma format, dostosowane do potrzeb aplikacji klienckiej.

Należy wziąć pod uwagę podobny ekran dla aplikacji mobilnej. W przypadku pojedynczej bazy danych, użytkownik może zebrane dane dla tego ekranu przy użyciu zapytania SQL, który wykonuje złożone sprzężeniem obejmującym wiele tabel. Jednak zawierać wiele baz danych, gdy każda baza danych jest własnością innego mikrousług, nie można zbadać tych baz danych i Utwórz sprzężenie SQL. Zapytanie złożone staje się wyzwaniem. Można rozwiązać wymagań przy użyciu podejścia CQRS — Utwórz tabelę nieznormalizowany w innej bazie danych, która jest używana tylko dla zapytania. Tabeli może być zaprojektowane specjalnie dla danych, czego potrzebujesz do złożonego zapytania, z relacją między polami wymagane przez ekran aplikacji i kolumn w tabeli zapytania. Można go również służyć do celów raportowania.

To podejście nie tylko rozwiązuje problem oryginalnego (jak wykonywać zapytania i sprzężenia między mikrousług), ale również poprawiasz jej wydajność znacznie w porównaniu ze sprzężeniem złożone, ponieważ masz już dane, które są wymagane przez aplikację w tabeli zapytania. Oczywiście używając polecenia i podział odpowiedzialności zapytania (CQRS) z tabelami w operacji zapytania/odczytu oznacza, że dodatkowe prace i konieczne będzie Uwzględniaj spójność ostateczną. Niemniej jednak wymagania dotyczące wydajności i wysokiej skalowalności w [scenariuszach współpracy](http://udidahan.com/2011/10/02/why-you-should-be-using-cqrs-almost-everywhere/) (lub konkurencyjnych scenariuszy, w zależności od punktu widzenia) są, gdzie należy zastosować podejście CQRS z wieloma bazami danych.

**"Zimnych danych" centralnej bazy danych.** Dla złożonych raportów i zapytań, które mogą nie wymagać danych w czasie rzeczywistym, typowym podejściem jest Eksportuj swoje oznaczenie "gorące dane" (dane transakcyjne z mikrousług) jako "zimnych danych" w dużych baz danych, które są używane tylko w przypadku raportowania. Czy system centralnej bazy danych może być systemu opartego na danych Big Data, takich jak Hadoop, magazynu danych, takich jak oparty na usłudze Azure SQL Data Warehouse lub nawet pojedynczej bazy danych SQL używaną tylko w przypadku raportów (Jeśli rozmiar nie będzie problem).

Należy pamiętać, że ta scentralizowanej bazie danych będzie używana tylko dla zapytań i raportów, które nie są w czasie rzeczywistym danych. Oryginalny aktualizacje i transakcji jako źródło prawdziwych danych, muszą znajdować się w danych mikrousług. Sposób będą synchronizować dane będą przy użyciu oparte na zdarzeniach komunikacji (co omówiono w kolejnych sekcjach) lub przy użyciu innych narzędzi importu/eksportu infrastruktury bazy danych. Jeśli używasz komunikacji oparte na zdarzeniach, procesu integracji mogą być podobne do sposób propagowanie danych zgodnie z wcześniejszym opisem CQRS zapytania tabel.

Jednak jeśli projektu aplikacji obejmuje stale agregując informacje z wielu mikrousług w przypadku złożonych zapytań, może być objawem nieprawidłowy projekt - mikrousługi powinien być izolowana możliwie z innych mikrousług. (Z wyłączeniem raporty/analizę, która zawsze należy używać bazy danych centralnej zimne dane.) Często wystąpienia tego problemu może być powód do scalenia mikrousług. Musisz równoważenie autonomii ewolucji i wdrożenia, poszczególne mikrousługi przy użyciu silnego zależności, spójności i agregacja danych.

## <a name="challenge-3-how-to-achieve-consistency-across-multiple-microservices"></a>Wyzwanie \#3: Jak ujednolicenia wyglądu wiele mikrousług

Jak wspomniano wcześniej, dane należące do poszczególnych mikrousług są prywatne tego mikrousług i może zostać oceniony jedynie przy użyciu jego mikrousług interfejsu API. Dlatego żądanie prezentowane jest sposób implementacji procesów biznesowych end-to-end przy jednoczesnym zachowaniu spójności w wielu mikrousługach.

Aby analizować ten problem, Spójrzmy na przykład z [ramach aplikacji eShopOnContainers odwołania aplikacji](https://aka.ms/eshoponcontainers). Mikrousługi katalogu przechowuje informacje o wszystkich produktów, w tym cena produktu. Mikrousługi koszyka zarządza danych czasowych danych o elementach produktu, które Przystępując do dodawania użytkowników do ich koszyki zakupów, w tym ceny elementy w czasie, które zostały dodane do koszyka. Po zaktualizowaniu cena produktu w katalogu można również zaktualizować cena, w aktywny koszyki, zawierających tego samego produktu, a także system prawdopodobnie należy ostrzec użytkowników, informujący o tym, że cena określonego elementu zmieniła się od ich dodania do koszyka.

Hipotetyczny monolityczne wersji tej aplikacji zmianie cen w tabeli Produkty w podsystemie katalogu można służy do aktualizowania bieżąca cena w tabeli koszyka po prostu transakcji ACID.

Jednak w przypadku aplikacji opartych na mikrousługach tabel Product i koszyka są własnością ich odpowiednich mikrousług. Nie mikrousług nigdy nie powinna zawierać własnością innego mikrousług w jego własnej transakcji, nawet w przypadku zapytania bezpośredniego, tabele i magazynowania, jak pokazano w rysunek 4 – 9.

![Mikrousługi nie może uzyskać bezpośredni dostęp do tabeli w innym mikrousług, spójność ostateczną, muszą być używane do synchronizacji danych.](./media/image9.png)

**Rysunek 4 – 9**. Mikrousługi nie może uzyskać bezpośredni dostęp do tabeli w innej mikrousług

Mikrousług katalogu nie należy bezpośrednio zaktualizować tabeli koszyka, ponieważ tabeli koszyka jest własnością mikrousług koszyka. Aby dokonać aktualizacji mikrousług koszyka, mikrousługi katalogu należy używać spójność ostateczną, prawdopodobnie oparte na komunikacji asynchronicznej, takich jak zdarzenia integracji (wiadomości i komunikacji oparte na zdarzeniu). Jest to sposób, w jaki [ramach aplikacji eShopOnContainers](http://aka.ms/eshoponcontainers) odwołania aplikacja wykonuje ten typ spójności między mikrousług.

Podane przez [kolejnego elementu teorii CAP](https://en.wikipedia.org/wiki/CAP_theorem), musisz wybrać między dostępnością i ACID silnej spójności. Większość scenariuszy opartych na mikrousługach wymaga dostępności i wysokiej skalowalności w przeciwieństwie do silnej spójności. Aplikacji o krytycznym znaczeniu musi znajdować się, a następnie uruchomiona i deweloperów można obejść wysoki poziom spójności przy użyciu technik do pracy z słabych lub ostateczną spójność. To podejście stosowane przez większość opartych na mikrousługach architektury.

Ponadto ACID stylu lub dwufazowe zatwierdzanie transakcji nie są tylko względem zasad mikrousług. Większość baz danych NoSQL (np. usługi Azure Cosmos DB, bazy danych MongoDB itp.) nie obsługują transakcji dwufazowego, zwykle w scenariuszach rozproszonych baz danych. Obsługa danych spójności w różnych usługach i baz danych jest jednak niezbędne. Temu wyzwaniu dotyczy również zapytania dotyczące propagujące zmiany w wielu mikrousług, gdy konieczne jest nadmiarowy niektórych danych — na przykład, gdy musisz mieć nazwę produktu lub opis w mikrousługach wykazu i koszyka mikrousługi.

Dobrym rozwiązaniem tego problemu jest używać spójności ostatecznej między mikrousługami przegubowe za pośrednictwem komunikacji oparte na zdarzeniach i systemem publikowania i subskrybowania. Te tematy zostały omówione w sekcji [komunikacji asynchronicznej oparte na zdarzeniach](asynchronous-message-based-communication.md#asynchronous-event-driven-communication) później w tym przewodniku.

## <a name="challenge-4-how-to-design-communication-across-microservice-boundaries"></a>Wyzwanie \#4: Jak projektować komunikacji między granicami mikrousług

Granice, komunikacji za pośrednictwem mikrousług jest rzeczywistym wyzwaniem. W tym kontekście komunikacji nie odwołuje się do który protokół powinien używać (protokół HTTP i REST, AMQP, obsługi wiadomości i tak dalej). Zamiast tego usuwa styl komunikacji należy użyć, a zwłaszcza jak sprzężonych mikrousługi powinno być. W zależności od poziomu sprzężenia gdy wystąpi błąd, wpływ tej awarii w systemie różni się znacznie.

W rozproszonym systemie, takie jak opartych na mikrousługach aplikacji z artefaktów tak wiele poruszanie się i usługi rozproszone między wiele serwerów lub hosty składniki po pewnym czasie nie powiedzie. Częściowych niepowodzeń i jeszcze większym awarii nastąpi, więc należy projektować mikrousługi i komunikację między nimi analizie ryzyka wspólnej w rozproszonym systemie tego typu.

Popularne podejście jest mikrousługi oparty na protokole REST protokołu HTTP, ze względu na ich prostotę. Podejście oparte na protokole HTTP jest idealnie dopuszczalne; Ten problem, w tym miejscu dotyczą sposobu ich używania. Jeśli używasz żądań i odpowiedzi HTTP, tylko w celu interakcji z mikrousługi z aplikacji klienckich lub bramy interfejsu API, który jest poprawne. Ale jeśli tworzysz długie łańcuchy synchroniczne wywołania HTTP na mikrousługach, komunikacji za pośrednictwem ich granice tak, jakby mikrousługi były obiektami w aplikacji monolitycznej aplikacji będzie po pewnym czasie.

Na przykład załóżmy, że Twoja aplikacja kliencka sprawia, że wywołania interfejsu API protokołu HTTP w taki sposób, aby jedna mikrousługa, takie jak mikrousługi porządkowanie. Mikrousługi porządkowanie z kolei wywołuje dodatkowe cyklu mikrousług przy użyciu protokołu HTTP w ramach tego samego żądania/odpowiedzi, tworzysz łańcuch połączeń HTTP. Może być brzmi uzasadnione początkowo. Jednakże istnieją ważne punkty, które należy wziąć pod uwagę w przypadku wyłączenia tej ścieżki:

- Blokowanie i niskiej wydajności. Ze względu na charakter synchroniczne HTTP oryginalne żądanie nie uzyska odpowiedzi zakończenie wszystkich wewnętrznych wywołań HTTP. Wyobraź sobie, jeśli liczbę tych wywołań znacznie zwiększa i w tym samym czasie, wywoływanych jeden pośrednich HTTP mikrousługa jest zablokowany. Wynik jest, że to wpływ na wydajność i skalowalność ogólną wykładniczo wpłynie na jako dodatkowe zwiększenie żądania HTTP.

- Sprzężenie mikrousług za pośrednictwem protokołu HTTP. Mikrousług biznesowych nie powinny być połączone z mikrousług innych firm. Najlepiej, jeśli ich nie powinny "know" o istnieniu innych mikrousług. Jeśli aplikacja zależy od tego, sprzężenia mikrousług, tak jak w przykładzie, osiągnięcia Autonomia poszczególnych mikrousług jest prawie niemożliwe.

- Błąd w dowolnej jeden mikrousług. Jeśli zaimplementowano łańcuch mikrousług połączone przez wywołania HTTP, w którym dowolnego mikrousługi nie powiedzie się (i ostatecznie zakończy się niepowodzeniem) całego łańcucha mikrousług zakończy się niepowodzeniem. System opartych na mikrousługach, powinny zostać tak zaprojektowane, aby kontynuować pracę oraz możliwości częściowej awarii. Nawet w przypadku zastosowania logiki klienta, która używa ponownych prób z wykorzystaniem wykładniczego wycofywania lub mechanizmy wyłącznika, więcej łańcuchy wywołania HTTP złożone są bardziej złożone, które można zaimplementować strategię błędu HTTP.

W rzeczywistości Jeśli wewnętrznego mikrousługi komunikują się przez utworzenie łańcucha żądań HTTP, zgodnie z opisem, może być podniesiono czy masz aplikacji monolitycznej, ale go w oparciu HTTP między procesami, zamiast mechanizmów komunikacji wewnątrzprocesową.

W związku z tym aby wymusić Autonomia mikrousług i mieć większą odporność, należy zminimalizować użycie łańcuchów komunikacji żądania/odpowiedzi na mikrousługach. Zaleca się używać interakcji tylko asynchronicznych do komunikacji między mikrousług przy użyciu asynchronicznych komunikatów i zdarzenie oparte na komunikacji lub (asynchroniczny) sondowania HTTP niezależnie od oryginalnego żądania HTTP / Cykl odpowiedzi.

Korzystanie z komunikacji asynchronicznej zostało wyjaśnione z dodatkowymi szczegółami w dalszej części tego przewodnika, w sekcjach [integracji asynchroniczne mikrousług wymusza autonomię w mikrousługach](communication-in-microservice-architecture.md#asynchronous-microservice-integration-enforces-microservices-autonomy) i [asynchroniczne Komunikacja oparta na komunikatach](asynchronous-message-based-communication.md).

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Kolejnego elementu teorii CAP** \
  [*https://en.wikipedia.org/wiki/CAP_theorem*](https://en.wikipedia.org/wiki/CAP_theorem)

- **Spójność ostateczna** \
  [*https://en.wikipedia.org/wiki/Eventual_consistency*](https://en.wikipedia.org/wiki/Eventual_consistency)

- **Podstawy spójności danych** \
  [*https://docs.microsoft.com/previous-versions/msp-n-p/dn589800(v=pandp.10)*](https://docs.microsoft.com/previous-versions/msp-n-p/dn589800(v=pandp.10))

- **Martina Fowlera. Podejście CQRS (Command and Query Responsibility Segregation)** \
  [*https://martinfowler.com/bliki/CQRS.html*](https://martinfowler.com/bliki/CQRS.html)

- **Zmaterializowany widok** \
  [*https://docs.microsoft.com/azure/architecture/patterns/materialized-view*](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

- **Charles wiersz. ACID programu vs. PODSTAWOWA: PH Shifting przetwarzania transakcji bazy danych** \
  [*http://www.dataversity.net/acid-vs-base-the-shifting-ph-of-database-transaction-processing/*](http://www.dataversity.net/acid-vs-base-the-shifting-ph-of-database-transaction-processing/)

- **Transakcja wyrównująca** \
  [*https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction*](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- **Udi Dahan. Kompozycja korzystający z usługi** \
  [*http://udidahan.com/2014/07/30/service-oriented-composition-with-video/*](http://udidahan.com/2014/07/30/service-oriented-composition-with-video/)

>[!div class="step-by-step"]
>[Poprzednie](logical-versus-physical-architecture.md)
>[dalej](identify-microservice-domain-model-boundaries.md)