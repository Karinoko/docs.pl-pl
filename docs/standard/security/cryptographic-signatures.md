---
title: Podpisy kryptograficzne
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
helpviewer_keywords:
- digital signatures
- cryptography [.NET Framework], signatures
- digital signatures, XML signing
- signatures, cryptographic
- digital signatures, generating
- verifying signatures
- generating signatures
- digital signatures, about
- encryption [.NET Framework], signatures
- security [.NET Framework], signatures
- XML signing
- digital signatures, verifying
- signing XML
ms.assetid: aa87cb7f-e608-4a81-948b-c9b8a1225783
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0651ae0fbc85b01d3e02354c06a9796804c8516e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="cryptographic-signatures"></a><span data-ttu-id="967a1-102">Podpisy kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="967a1-102">Cryptographic Signatures</span></span>
<span data-ttu-id="967a1-103"><a name="top"></a>Kryptograficznych podpisów cyfrowych korzysta algorytmy kluczy publicznych w celu zapewnienia integralności danych.</span><span class="sxs-lookup"><span data-stu-id="967a1-103"><a name="top"></a> Cryptographic digital signatures use public key algorithms to provide data integrity.</span></span> <span data-ttu-id="967a1-104">Podczas rejestrowania danych za pomocą podpisu cyfrowego ktoś inny może zweryfikować podpisu, a można udowodnić, że dane pochodzą od użytkownika oraz nie została zmodyfikowana po podpisaniu jej.</span><span class="sxs-lookup"><span data-stu-id="967a1-104">When you sign data with a digital signature, someone else can verify the signature, and can prove that the data originated from you and was not altered after you signed it.</span></span> <span data-ttu-id="967a1-105">Aby uzyskać więcej informacji na temat podpisów cyfrowych, zobacz [usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md).</span><span class="sxs-lookup"><span data-stu-id="967a1-105">For more information about digital signatures, see [Cryptographic Services](../../../docs/standard/security/cryptographic-services.md).</span></span>  
  
 <span data-ttu-id="967a1-106">W tym temacie opisano sposób generować i weryfikować podpisów cyfrowych przy użyciu klas w <xref:System.Security.Cryptography?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="967a1-106">This topic explains how to generate and verify digital signatures using classes in the <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span></span>  
  
-   [<span data-ttu-id="967a1-107">Generowanie podpisów</span><span class="sxs-lookup"><span data-stu-id="967a1-107">Generating Signatures</span></span>](#generate)  
  
-   [<span data-ttu-id="967a1-108">Weryfikowanie podpisów</span><span class="sxs-lookup"><span data-stu-id="967a1-108">Verifying Signatures</span></span>](#verify)  
  
<a name="generate"></a>   
## <a name="generating-signatures"></a><span data-ttu-id="967a1-109">Generowanie podpisów</span><span class="sxs-lookup"><span data-stu-id="967a1-109">Generating Signatures</span></span>  
 <span data-ttu-id="967a1-110">Podpisy cyfrowe są zazwyczaj stosowane do wartości skrótu, reprezentujących większy danych.</span><span class="sxs-lookup"><span data-stu-id="967a1-110">Digital signatures are usually applied to hash values that represent larger data.</span></span> <span data-ttu-id="967a1-111">Poniższy przykład dotyczy wartości skrótu podpisu cyfrowego.</span><span class="sxs-lookup"><span data-stu-id="967a1-111">The following example applies a digital signature to a hash value.</span></span> <span data-ttu-id="967a1-112">Po pierwsze, nowe wystąpienie klasy <xref:System.Security.Cryptography.RSACryptoServiceProvider> klasa jest tworzona można wygenerować pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="967a1-112">First, a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class is created to generate a public/private key pair.</span></span> <span data-ttu-id="967a1-113">Następnie <xref:System.Security.Cryptography.RSACryptoServiceProvider> jest przekazywana do nowego wystąpienia <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> klasy.</span><span class="sxs-lookup"><span data-stu-id="967a1-113">Next, the <xref:System.Security.Cryptography.RSACryptoServiceProvider> is passed to a new instance of the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class.</span></span> <span data-ttu-id="967a1-114">Spowoduje to przesłanie klucza prywatnego <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, który wykonuje rzeczywistą podpisu cyfrowego.</span><span class="sxs-lookup"><span data-stu-id="967a1-114">This transfers the private key to the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, which actually performs the digital signing.</span></span> <span data-ttu-id="967a1-115">Aby móc zalogować skrótu, należy określić algorytm wyznaczania wartości skrótu do użycia.</span><span class="sxs-lookup"><span data-stu-id="967a1-115">Before you can sign the hash code, you must specify a hash algorithm to use.</span></span> <span data-ttu-id="967a1-116">W tym przykładzie używa algorytmu SHA1.</span><span class="sxs-lookup"><span data-stu-id="967a1-116">This example uses the SHA1 algorithm.</span></span> <span data-ttu-id="967a1-117">Na koniec <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> metoda jest wywoływana na podpisywanie.</span><span class="sxs-lookup"><span data-stu-id="967a1-117">Finally, the <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> method is called to perform the signing.</span></span>  
  
```vb  
Imports System  
Imports System.Security.Cryptography  
  
Module Module1  
    Sub Main()  
        'The hash value to sign.  
        Dim HashValue As Byte() = {59, 4, 248, 102, 77, 97, 142, 201, 210, 12, 224, 93, 25, 41, 100, 197, 213, 134, 130, 135}  
  
        'The value to hold the signed value.  
        Dim SignedHashValue() As Byte  
  
        'Generate a public/private key pair.  
        Dim RSA As New RSACryptoServiceProvider()  
  
        'Create an RSAPKCS1SignatureFormatter object and pass it   
        'the RSACryptoServiceProvider to transfer the private key.  
        Dim RSAFormatter As New RSAPKCS1SignatureFormatter(RSA)  
  
        'Set the hash algorithm to SHA1.  
        RSAFormatter.SetHashAlgorithm("SHA1")  
  
        'Create a signature for HashValue and assign it to   
        'SignedHashValue.  
        SignedHashValue = RSAFormatter.CreateSignature(HashValue)  
    End Sub  
End Module  
  
using System;  
using System.Security.Cryptography;  
```  
  
```csharp  
class Class1  
{  
   static void Main()  
   {  
      //The hash value to sign.  
      byte[] HashValue = {59,4,248,102,77,97,142,201,210,12,224,93,25,41,100,197,213,134,130,135};  
  
      //The value to hold the signed value.  
      byte[] SignedHashValue;  
  
      //Generate a public/private key pair.  
      RSACryptoServiceProvider RSA = new RSACryptoServiceProvider();  
  
      //Create an RSAPKCS1SignatureFormatter object and pass it the   
      //RSACryptoServiceProvider to transfer the private key.  
      RSAPKCS1SignatureFormatter RSAFormatter = new RSAPKCS1SignatureFormatter(RSA);  
  
      //Set the hash algorithm to SHA1.  
      RSAFormatter.SetHashAlgorithm("SHA1");  
  
      //Create a signature for HashValue and assign it to   
      //SignedHashValue.  
      SignedHashValue = RSAFormatter.CreateSignature(HashValue);  
   }  
}  
```  
  
### <a name="signing-xml-files"></a><span data-ttu-id="967a1-118">Podpisywanie plików XML</span><span class="sxs-lookup"><span data-stu-id="967a1-118">Signing XML Files</span></span>  
 <span data-ttu-id="967a1-119">Platforma .NET Framework zapewnia <xref:System.Security.Cryptography.Xml> przestrzeni nazw, która pozwala zarejestrować XML.</span><span class="sxs-lookup"><span data-stu-id="967a1-119">The .NET Framework provides the <xref:System.Security.Cryptography.Xml> namespace, which enables you sign XML.</span></span> <span data-ttu-id="967a1-120">Podpisywanie XML jest ważne, jeśli chcesz sprawdzić, czy plik XML pochodzą z danego źródła.</span><span class="sxs-lookup"><span data-stu-id="967a1-120">Signing XML is important when you want to verify that the XML originates from a certain source.</span></span> <span data-ttu-id="967a1-121">Na przykład jeśli używasz usługi giełdowych, który jest używany plik XML możesz zweryfikować źródło XML jest podpisany.</span><span class="sxs-lookup"><span data-stu-id="967a1-121">For example, if you are using a stock quote service that uses XML, you can verify the source of the XML if it is signed.</span></span>  
  
 <span data-ttu-id="967a1-122">Postępuj zgodnie z klas w tej przestrzeni nazw [składni XML podpisu i przetwarzania zalecenie](http://go.microsoft.com/fwlink/?LinkId=136777) z konsorcjum World Wide Web.</span><span class="sxs-lookup"><span data-stu-id="967a1-122">The classes in this namespace follow the [XML-Signature Syntax and Processing recommendation](http://go.microsoft.com/fwlink/?LinkId=136777) from the World Wide Web Consortium.</span></span>  
  
 [<span data-ttu-id="967a1-123">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="967a1-123">Back to top</span></span>](#top)  
  
<a name="verify"></a>   
## <a name="verifying-signatures"></a><span data-ttu-id="967a1-124">Weryfikowanie podpisów</span><span class="sxs-lookup"><span data-stu-id="967a1-124">Verifying Signatures</span></span>  
 <span data-ttu-id="967a1-125">Aby sprawdzić, czy dane został podpisany przez firmę określonego, musi mieć następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="967a1-125">To verify that data was signed by a particular party, you must have the following information:</span></span>  
  
-   <span data-ttu-id="967a1-126">Klucz publiczny strony, który podpisał danych.</span><span class="sxs-lookup"><span data-stu-id="967a1-126">The public key of the party that signed the data.</span></span>  
  
-   <span data-ttu-id="967a1-127">Podpis cyfrowy.</span><span class="sxs-lookup"><span data-stu-id="967a1-127">The digital signature.</span></span>  
  
-   <span data-ttu-id="967a1-128">Dane, który został podpisany.</span><span class="sxs-lookup"><span data-stu-id="967a1-128">The data that was signed.</span></span>  
  
-   <span data-ttu-id="967a1-129">Algorytm wyznaczania wartości skrótu używanego przez osoby podpisującej.</span><span class="sxs-lookup"><span data-stu-id="967a1-129">The hash algorithm used by the signer.</span></span>  
  
 <span data-ttu-id="967a1-130">Można zweryfikować podpisu podpisane przez <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> klasy, należy użyć <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> klasy.</span><span class="sxs-lookup"><span data-stu-id="967a1-130">To verify a signature signed by the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class, use the <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class.</span></span> <span data-ttu-id="967a1-131"><xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> Klasa musi być dostarczony klucz publiczny podpisu.</span><span class="sxs-lookup"><span data-stu-id="967a1-131">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class must be supplied the public key of the signer.</span></span> <span data-ttu-id="967a1-132">Konieczne będzie wartości resztę i wykładnik, aby określić klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="967a1-132">You will need the values of the modulus and the exponent to specify the public key.</span></span> <span data-ttu-id="967a1-133">(Strony, który wygenerował pary kluczy publiczny/prywatny należy podać te wartości.) Najpierw utwórz <xref:System.Security.Cryptography.RSACryptoServiceProvider> obiektu do przechowywania klucz publiczny, który będzie zweryfikować podpisu, a następnie zainicjuj <xref:System.Security.Cryptography.RSAParameters> struktury modulo i wykładnik wartości, które określają klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="967a1-133">(The party that generated the public/private key pair should provide these values.) First create an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to hold the public key that will verify the signature, and then initialize an <xref:System.Security.Cryptography.RSAParameters> structure to the modulus and exponent values that specify the public key.</span></span>  
  
 <span data-ttu-id="967a1-134">Poniższy kod przedstawia tworzenie <xref:System.Security.Cryptography.RSAParameters> struktury.</span><span class="sxs-lookup"><span data-stu-id="967a1-134">The following code shows the creation of an <xref:System.Security.Cryptography.RSAParameters> structure.</span></span> <span data-ttu-id="967a1-135">`Modulus` Właściwości ustawiono wartość tablicy bajtów o nazwie `ModulusData` i `Exponent` właściwości ustawiono wartość tablicy bajtów o nazwie `ExponentData`.</span><span class="sxs-lookup"><span data-stu-id="967a1-135">The `Modulus` property is set to the value of a byte array called `ModulusData` and the `Exponent` property is set to the value of a byte array called `ExponentData`.</span></span>  
  
```vb  
Dim RSAKeyInfo As RSAParameters  
RSAKeyInfo.Modulus = ModulusData  
RSAKeyInfo.Exponent = ExponentData  
```  
  
```csharp  
RSAParameters RSAKeyInfo;  
RSAKeyInfo.Modulus = ModulusData;  
RSAKeyInfo.Exponent = ExponentData;  
```  
  
 <span data-ttu-id="967a1-136">Po utworzeniu <xref:System.Security.Cryptography.RSAParameters> obiektu, należy zainicjować nowe wystąpienie klasy <xref:System.Security.Cryptography.RSACryptoServiceProvider> klasy do wartości określonej w <xref:System.Security.Cryptography.RSAParameters>.</span><span class="sxs-lookup"><span data-stu-id="967a1-136">After you have created the <xref:System.Security.Cryptography.RSAParameters> object, you can initialize a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class to the values specified in <xref:System.Security.Cryptography.RSAParameters>.</span></span> <span data-ttu-id="967a1-137"><xref:System.Security.Cryptography.RSACryptoServiceProvider> z kolei przekazany do konstruktora <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> do przeniesienia klucza.</span><span class="sxs-lookup"><span data-stu-id="967a1-137">The <xref:System.Security.Cryptography.RSACryptoServiceProvider> is, in turn, passed to the constructor of an <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> to transfer the key.</span></span>  
  
 <span data-ttu-id="967a1-138">Poniższy przykład przedstawia tego procesu.</span><span class="sxs-lookup"><span data-stu-id="967a1-138">The following example illustrates this process.</span></span> <span data-ttu-id="967a1-139">W tym przykładzie `HashValue` i `SignedHashValue` są tablice bajtów dostarczonym przez firmę zdalnego.</span><span class="sxs-lookup"><span data-stu-id="967a1-139">In this example, `HashValue` and `SignedHashValue` are arrays of bytes provided by a remote party.</span></span> <span data-ttu-id="967a1-140">Strona zdalna została podpisana `HashValue` przy użyciu algorytmu SHA1, tworzenie podpisu cyfrowego `SignedHashValue`.</span><span class="sxs-lookup"><span data-stu-id="967a1-140">The remote party has signed the `HashValue` using the SHA1 algorithm, producing the digital signature `SignedHashValue`.</span></span> <span data-ttu-id="967a1-141">Program</span><span class="sxs-lookup"><span data-stu-id="967a1-141">The</span></span>  
  
 <span data-ttu-id="967a1-142"><xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType>metoda sprawdza, czy podpis cyfrowy jest prawidłowa i czy został użyty do podpisania `HashValue`.</span><span class="sxs-lookup"><span data-stu-id="967a1-142"><xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> method verifies that the digital signature is valid and was used to sign the `HashValue`.</span></span>  
  
```vb  
Dim RSA As New RSACryptoServiceProvider()  
RSA.ImportParameters(RSAKeyInfo)  
Dim RSADeformatter As New RSAPKCS1SignatureDeformatter(RSA)  
RSADeformatter.SetHashAlgorithm("SHA1")  
If RSADeformatter.VerifySignature(HashValue, SignedHashValue) Then  
   Console.WriteLine("The signature is valid.")  
Else  
   Console.WriteLine("The signture is not valid.")  
End If  
```  
  
```csharp  
RSACryptoServiceProvider RSA = new RSACryptoServiceProvider();  
RSA.ImportParameters(RSAKeyInfo);  
RSAPKCS1SignatureDeformatter RSADeformatter = new RSAPKCS1SignatureDeformatter(RSA);  
RSADeformatter.SetHashAlgorithm("SHA1");  
if(RSADeformatter.VerifySignature(HashValue, SignedHashValue))  
{  
   Console.WriteLine("The signature is valid.");  
}  
else  
{  
   Console.WriteLine("The signature is not valid.");  
}  
```  
  
 <span data-ttu-id="967a1-143">Wyświetli fragmentu kodu "`The signature is valid`" Jeśli podpis jest nieprawidłowy i "`The signature is not valid`" Jeśli nie jest.</span><span class="sxs-lookup"><span data-stu-id="967a1-143">This code fragment will display "`The signature is valid`" if the signature is valid and "`The signature is not valid`" if it is not.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="967a1-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="967a1-144">See Also</span></span>  
 [<span data-ttu-id="967a1-145">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="967a1-145">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)