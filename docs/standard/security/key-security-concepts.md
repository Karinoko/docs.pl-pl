---
title: "Główne pojęcia dotyczące zabezpieczeń"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- unauthorized access
- permissions [.NET Framework]
- security [.NET Framework], about security
ms.assetid: 3cfced4f-ea02-4e66-ae98-d69286363e98
caps.latest.revision: "22"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5e29b3c12fe89861574741506cb7cd018eb81b1d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="key-security-concepts"></a><span data-ttu-id="37de6-102">Główne pojęcia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="37de6-102">Key Security Concepts</span></span>
<span data-ttu-id="37de6-103">Microsoft .NET Framework zapewnia oparte na rolach zabezpieczeń mających na celu adres problemy z zabezpieczeniami dotyczące kodu przenośnego i zapewnienie obsługi, który umożliwia ustalenie, użytkownicy są upoważnione na.</span><span class="sxs-lookup"><span data-stu-id="37de6-103">The Microsoft .NET Framework offers role-based security to help address security concerns about mobile code and to provide support that enables components to determine what users are authorized to do.</span></span>  
  
## <a name="type-safety-and-security"></a><span data-ttu-id="37de6-104">Typ bezpieczeństwa i zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="37de6-104">Type safety and security</span></span>  
 <span data-ttu-id="37de6-105">Bezpieczny kod uzyskuje dostęp do lokalizacji pamięci, który jest upoważniony do dostępu.</span><span class="sxs-lookup"><span data-stu-id="37de6-105">Type-safe code accesses only the memory locations it is authorized to access.</span></span> <span data-ttu-id="37de6-106">(Dla tej dyskusji zabezpieczeń w szczególności odwołuje się do pamięci typu bezpieczeństwa i nie należy mylić z typu bezpieczeństwa w szerszym zakresie.) Na przykład bezpieczny kod nie można odczytać wartości z pól prywatnych innego obiektu.</span><span class="sxs-lookup"><span data-stu-id="37de6-106">(For this discussion, type safety specifically refers to memory type safety and should not be confused with type safety in a broader respect.) For example, type-safe code cannot read values from another object's private fields.</span></span> <span data-ttu-id="37de6-107">Uzyskuje dostęp do typów tylko w sposób wyraźnie określone, dozwolony.</span><span class="sxs-lookup"><span data-stu-id="37de6-107">It accesses types only in well-defined, allowable ways.</span></span>  
  
 <span data-ttu-id="37de6-108">Podczas just in time (JIT) kompilacji proces weryfikacji opcjonalne sprawdza, czy metadane i języku pośrednim firmy Microsoft (MSIL) z metodę, aby skompilować JIT do kodu macierzystego maszyny, aby sprawdzić, czy są one bezpieczne typu.</span><span class="sxs-lookup"><span data-stu-id="37de6-108">During just-in-time (JIT) compilation, an optional verification process examines the metadata and Microsoft intermediate language (MSIL) of a method to be JIT-compiled into native machine code to verify that they are type safe.</span></span> <span data-ttu-id="37de6-109">Ten proces jest pomijane, jeśli kod ma uprawnienie do pominięcia weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="37de6-109">This process is skipped if the code has permission to bypass verification.</span></span> <span data-ttu-id="37de6-110">Aby uzyskać więcej informacji o weryfikacji, zobacz [proces zarządzanego wykonania](../../../docs/standard/managed-execution-process.md).</span><span class="sxs-lookup"><span data-stu-id="37de6-110">For more information about verification, see [Managed Execution Process](../../../docs/standard/managed-execution-process.md).</span></span>  
  
 <span data-ttu-id="37de6-111">Weryfikacji zabezpieczeń nie jest wymagane do uruchomienia kodu zarządzanego, bezpieczeństwo typów odgrywa kluczową role w zestawie izolacji i wymuszanie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="37de6-111">Although verification of type safety is not mandatory to run managed code, type safety plays a crucial role in assembly isolation and security enforcement.</span></span> <span data-ttu-id="37de6-112">Jeśli kod jest typu bezpieczne, środowisko uruchomieniowe języka wspólnego całkowicie można odizolować zestawy od siebie.</span><span class="sxs-lookup"><span data-stu-id="37de6-112">When code is type safe, the common language runtime can completely isolate assemblies from each other.</span></span> <span data-ttu-id="37de6-113">Izolacja gwarantuje, że zestawy nie może mieć niekorzystny wpływ na siebie i zwiększa niezawodność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="37de6-113">This isolation helps ensure that assemblies cannot adversely affect each other and it increases application reliability.</span></span> <span data-ttu-id="37de6-114">Bezpieczne składniki mogą wykonywać bezpiecznie w ramach tego samego procesu, nawet jeśli są zaufane na różnych poziomach.</span><span class="sxs-lookup"><span data-stu-id="37de6-114">Type-safe components can execute safely in the same process even if they are trusted at different levels.</span></span> <span data-ttu-id="37de6-115">Gdy kodu nie jest typem bezpieczne, może wystąpić niepożądane skutki uboczne.</span><span class="sxs-lookup"><span data-stu-id="37de6-115">When code is not type safe, unwanted side effects can occur.</span></span> <span data-ttu-id="37de6-116">Na przykład środowisko uruchomieniowe nie mogą uniemożliwiać kodu zarządzanego z wywołania do kodu macierzystego (niezarządzany) i wykonywanie operacji złośliwe.</span><span class="sxs-lookup"><span data-stu-id="37de6-116">For example, the runtime cannot prevent managed code from calling into native (unmanaged) code and performing malicious operations.</span></span> <span data-ttu-id="37de6-117">Jeśli kod jest typu bezpieczne, mechanizmu wymuszania zabezpieczeń środowiska uruchomieniowego zapewnia że go nie dostęp do kodu macierzystego, chyba że ma uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="37de6-117">When code is type safe, the runtime's security enforcement mechanism ensures that it does not access native code unless it has permission to do so.</span></span> <span data-ttu-id="37de6-118">Cały kod, który nie jest typem bezpieczne musi mieć przyznaną <xref:System.Security.Permissions.SecurityPermission> z elementu członkowskiego wyliczenia przekazany <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A> do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="37de6-118">All code that is not type safe must have been granted <xref:System.Security.Permissions.SecurityPermission> with the passed enum member <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A> to run.</span></span>  
  
 <span data-ttu-id="37de6-119">Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](../../../docs/framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="37de6-119">For more information, see [Code Access Security Basics](../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="principal"></a><span data-ttu-id="37de6-120">Główne</span><span class="sxs-lookup"><span data-stu-id="37de6-120">Principal</span></span>  
 <span data-ttu-id="37de6-121">Podmiot zabezpieczeń reprezentuje tożsamość i rolę użytkownika i działa w imieniu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="37de6-121">A principal represents the identity and role of a user and acts on the user's behalf.</span></span> <span data-ttu-id="37de6-122">Zabezpieczenia oparte na rolach w programie .NET Framework obsługuje trzy rodzaje podmiotów zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="37de6-122">Role-based security in the .NET Framework supports three kinds of principals:</span></span>  
  
-   <span data-ttu-id="37de6-123">Ogólny podmiotów reprezentują użytkowników i role, które istnieją niezależnie od użytkowników systemu Windows i ról.</span><span class="sxs-lookup"><span data-stu-id="37de6-123">Generic principals represent users and roles that exist independent of Windows users and roles.</span></span>  
  
-   <span data-ttu-id="37de6-124">Podmioty zabezpieczeń systemu Windows reprezentują użytkowników systemu Windows i ich role (lub ich grupy systemu Windows).</span><span class="sxs-lookup"><span data-stu-id="37de6-124">Windows principals represent Windows users and their roles (or their Windows groups).</span></span> <span data-ttu-id="37de6-125">Podmiot zabezpieczeń systemu Windows mogą personifikować innego użytkownika, co oznacza, że podmiot zabezpieczeń może dostępu do zasobu w imieniu użytkownika podczas przedstawiania tożsamości, która należy do tego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="37de6-125">A Windows principal can impersonate another user, which means that the principal can access a resource on a user's behalf while presenting the identity that belongs to that user.</span></span>  
  
-   <span data-ttu-id="37de6-126">Niestandardowe podmiotów zabezpieczeń mogą zostać zdefiniowane przez aplikację w dowolny sposób, który jest wymagany dla tej konkretnej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="37de6-126">Custom principals can be defined by an application in any way that is needed for that particular application.</span></span> <span data-ttu-id="37de6-127">Można rozszerzają podstawowe pojęcie tożsamości podmiotu i ról.</span><span class="sxs-lookup"><span data-stu-id="37de6-127">They can extend the basic notion of the principal's identity and roles.</span></span>  
  
 <span data-ttu-id="37de6-128">Aby uzyskać więcej informacji, zobacz [podmiot zabezpieczeń i obiekty tożsamości](../../../docs/standard/security/principal-and-identity-objects.md).</span><span class="sxs-lookup"><span data-stu-id="37de6-128">For more information, see [Principal and Identity Objects](../../../docs/standard/security/principal-and-identity-objects.md).</span></span>  
  
## <a name="authentication"></a><span data-ttu-id="37de6-129">Uwierzytelnianie</span><span class="sxs-lookup"><span data-stu-id="37de6-129">Authentication</span></span>  
 <span data-ttu-id="37de6-130">Uwierzytelnianie to proces odnajdywania i weryfikowania tożsamości podmiot zabezpieczeń, sprawdzając poświadczenia użytkownika i sprawdzanie poprawności poświadczeń dla niektórych urzędu.</span><span class="sxs-lookup"><span data-stu-id="37de6-130">Authentication is the process of discovering and verifying the identity of a principal by examining the user's credentials and validating those credentials against some authority.</span></span> <span data-ttu-id="37de6-131">Dane uzyskane podczas uwierzytelniania jest użyteczne bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="37de6-131">The information obtained during authentication is directly usable by your code.</span></span> <span data-ttu-id="37de6-132">Umożliwia także zabezpieczenia oparte na rolach .NET Framework uwierzytelnić bieżącego użytkownika i określenia, czy zezwalać tego podmiotu zabezpieczeń dostępu kodu do.</span><span class="sxs-lookup"><span data-stu-id="37de6-132">You can also use .NET Framework role-based security to authenticate the current user and to determine whether to allow that principal to access your code.</span></span> <span data-ttu-id="37de6-133">Zobacz przeciążeń <xref:System.Security.Principal.WindowsPrincipal.IsInRole%2A?displayProperty=nameWithType> metody przykłady tego, jak uwierzytelniać podmiot zabezpieczeń dla określonych ról.</span><span class="sxs-lookup"><span data-stu-id="37de6-133">See the overloads of the <xref:System.Security.Principal.WindowsPrincipal.IsInRole%2A?displayProperty=nameWithType> method for examples of how to authenticate the principal for specific roles.</span></span> <span data-ttu-id="37de6-134">Na przykład można użyć <xref:System.Security.Principal.WindowsPrincipal.IsInRole%28System.String%29?displayProperty=nameWithType> przeciążenia, aby określić, czy bieżący użytkownik jest członkiem grupy Administratorzy.</span><span class="sxs-lookup"><span data-stu-id="37de6-134">For example, you can use the <xref:System.Security.Principal.WindowsPrincipal.IsInRole%28System.String%29?displayProperty=nameWithType> overload to determine if the current user is a member of the Administrators group.</span></span>  
  
 <span data-ttu-id="37de6-135">Różnych mechanizmów uwierzytelniania używanych dzisiaj, z których wiele może być używany z zabezpieczeń opartych na rolach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="37de6-135">A variety of authentication mechanisms are used today, many of which can be used with .NET Framework role-based security.</span></span> <span data-ttu-id="37de6-136">Niektóre z najczęściej używane mechanizmów są podstawowe, szyfrowane, Passport, system operacyjny (na przykład protokołu NTLM lub Kerberos) lub mechanizmów zdefiniowanym przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="37de6-136">Some of the most commonly used mechanisms are basic, digest, Passport, operating system (such as NTLM or Kerberos), or application-defined mechanisms.</span></span>  
  
### <a name="example"></a><span data-ttu-id="37de6-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="37de6-137">Example</span></span>  
 <span data-ttu-id="37de6-138">Poniższy przykład wymaga aktywny podmiot zabezpieczeń administratora.</span><span class="sxs-lookup"><span data-stu-id="37de6-138">The following example requires that the active principal be an administrator.</span></span> <span data-ttu-id="37de6-139">`name` Parametr jest `null`, dzięki czemu każdy użytkownik, który jest administratorem, aby przekazać żądanie.</span><span class="sxs-lookup"><span data-stu-id="37de6-139">The `name` parameter is `null`, which allows any user who is an administrator to pass the demand.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="37de6-140">W systemie Windows Vista kontroli konta użytkownika (UAC) określa uprawnienia użytkownika.</span><span class="sxs-lookup"><span data-stu-id="37de6-140">In Windows Vista, User Account Control (UAC) determines the privileges of a user.</span></span> <span data-ttu-id="37de6-141">Jeśli jesteś członkiem wbudowanej grupy Administratorzy, masz przypisane dwa tokeny dostępu w czasie wykonywania: token dostępu użytkownika standardowego i token dostępu administratora.</span><span class="sxs-lookup"><span data-stu-id="37de6-141">If you are a member of the Built-in Administrators group, you are assigned two run-time access tokens: a standard user access token and an administrator access token.</span></span> <span data-ttu-id="37de6-142">Domyślnie jesteś w roli użytkownika standardowego.</span><span class="sxs-lookup"><span data-stu-id="37de6-142">By default, you are in the standard user role.</span></span> <span data-ttu-id="37de6-143">Do wykonania kodu, musisz być administratorem, musi najpierw podwyższenie Twoje uprawnienia od użytkownika standardowego do administratora.</span><span class="sxs-lookup"><span data-stu-id="37de6-143">To execute the code that requires you to be an administrator, you must first elevate your privileges from standard user to administrator.</span></span> <span data-ttu-id="37de6-144">Można to zrobić, podczas uruchamiania aplikacji przez kliknięcie prawym przyciskiem myszy ikonę aplikacji i wskazujący, że chcesz uruchomić jako administrator.</span><span class="sxs-lookup"><span data-stu-id="37de6-144">You can do this when you start an application by right-clicking the application icon and indicating that you want to run as an administrator.</span></span>  
  
 [!code-cpp[Classic PrincipalPermission Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CPP/source.cpp#1)]
 [!code-csharp[Classic PrincipalPermission Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CS/source.cs#1)]
 [!code-vb[Classic PrincipalPermission Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/VB/source.vb#1)]  
  
 <span data-ttu-id="37de6-145">W poniższym przykładzie pokazano sposób określania tożsamości podmiotu zabezpieczeń i dostępne do principal role.</span><span class="sxs-lookup"><span data-stu-id="37de6-145">The following example demonstrates how to determine the identity of the principal and the roles available to the principal.</span></span> <span data-ttu-id="37de6-146">Aplikacja, w tym przykładzie może być aby upewnić się, że bieżący użytkownik jest w roli, możesz zezwolić na korzystanie z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="37de6-146">An application of this example might be to confirm that the current user is in a role you allow for using your application.</span></span>  
  
 [!code-cpp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CPP/source.cpp#1)]
 [!code-csharp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CS/source.cs#1)]
 [!code-vb[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/VB/source.vb#1)]  
  
## <a name="authorization"></a><span data-ttu-id="37de6-147">Autoryzacja</span><span class="sxs-lookup"><span data-stu-id="37de6-147">Authorization</span></span>  
 <span data-ttu-id="37de6-148">Autoryzacja jest proces określania, czy podmiot zabezpieczeń może wykonać żądanej akcji.</span><span class="sxs-lookup"><span data-stu-id="37de6-148">Authorization is the process of determining whether a principal is allowed to perform a requested action.</span></span> <span data-ttu-id="37de6-149">Występuje po uwierzytelnieniu i używa informacji o tożsamości podmiotu i ról do ustalenia podmiot zabezpieczeń mogą uzyskiwać dostęp do zasobów.</span><span class="sxs-lookup"><span data-stu-id="37de6-149">Authorization occurs after authentication and uses information about the principal's identity and roles to determine what resources the principal can access.</span></span> <span data-ttu-id="37de6-150">Zabezpieczenia oparte na rolach .NET Framework służy do implementowania autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="37de6-150">You can use .NET Framework role-based security to implement authorization.</span></span>