---
title: Metapliki w GDI+
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], metafiles
- GDI+, metafiles
- metafiles
ms.assetid: 51da872c-c783-440f-8bf6-1e580a966c31
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6b75ceb08df0454172a000d5d1ad15445f685ddf
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="metafiles-in-gdi"></a><span data-ttu-id="bed2e-102">Metapliki w GDI+</span><span class="sxs-lookup"><span data-stu-id="bed2e-102">Metafiles in GDI+</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="bed2e-103">udostępnia <xref:System.Drawing.Imaging.Metafile> klasy, dzięki czemu można rejestrować i wyświetlanie metaplików.</span><span class="sxs-lookup"><span data-stu-id="bed2e-103"> provides the <xref:System.Drawing.Imaging.Metafile> class so that you can record and display metafiles.</span></span> <span data-ttu-id="bed2e-104">Metaplik, nazywany również obrazem wektora jest obraz, który jest przechowywany jako sekwencja rysowania poleceń i ustawień.</span><span class="sxs-lookup"><span data-stu-id="bed2e-104">A metafile, also called a vector image, is an image that is stored as a sequence of drawing commands and settings.</span></span> <span data-ttu-id="bed2e-105">Polecenia i ustawienia są rejestrowane w <xref:System.Drawing.Imaging.Metafile> można przechowywane w pamięci obiekt lub zapisać do pliku lub strumienia.</span><span class="sxs-lookup"><span data-stu-id="bed2e-105">The commands and settings recorded in a <xref:System.Drawing.Imaging.Metafile> object can be stored in memory or saved to a file or stream.</span></span>  
  
## <a name="metafile-formats"></a><span data-ttu-id="bed2e-106">Formaty metaplików</span><span class="sxs-lookup"><span data-stu-id="bed2e-106">Metafile Formats</span></span>  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="bed2e-107">można wyświetlić metapliki, które były przechowywane w następujących formatach:</span><span class="sxs-lookup"><span data-stu-id="bed2e-107"> can display metafiles that have been stored in the following formats:</span></span>  
  
-   <span data-ttu-id="bed2e-108">Windows Metafile (WMF)</span><span class="sxs-lookup"><span data-stu-id="bed2e-108">Windows Metafile (WMF)</span></span>  
  
-   <span data-ttu-id="bed2e-109">Rozszerzony metaplik (EMF)</span><span class="sxs-lookup"><span data-stu-id="bed2e-109">Enhanced Metafile (EMF)</span></span>  
  
-   <span data-ttu-id="bed2e-110">EMF +</span><span class="sxs-lookup"><span data-stu-id="bed2e-110">EMF+</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="bed2e-111">można rejestrować metapliki w formatach EMF i EMF +, ale nie w formacie WMF.</span><span class="sxs-lookup"><span data-stu-id="bed2e-111"> can record metafiles in the EMF and EMF+ formats, but not in the WMF format.</span></span>  
  
 <span data-ttu-id="bed2e-112">EMF + jest rozszerzeniem EMF, który umożliwia [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] rekordów mają być przechowywane.</span><span class="sxs-lookup"><span data-stu-id="bed2e-112">EMF+ is an extension to EMF that allows [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] records to be stored.</span></span> <span data-ttu-id="bed2e-113">Istnieją dwie odmiany EMF + format: EMF + tylko i EMF + procesory.</span><span class="sxs-lookup"><span data-stu-id="bed2e-113">There are two variations on the EMF+ format: EMF+ Only and EMF+ Dual.</span></span> <span data-ttu-id="bed2e-114">Metapliki EMF + tylko zawierają tylko [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] rekordów.</span><span class="sxs-lookup"><span data-stu-id="bed2e-114">EMF+ Only metafiles contain only [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] records.</span></span> <span data-ttu-id="bed2e-115">Metapliki takie mogą być wyświetlane przez [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] , ale nie przez [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bed2e-115">Such metafiles can be displayed by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] but not by [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span> <span data-ttu-id="bed2e-116">Metapliki EMF + podwójnego zawierają [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] i [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] rekordów.</span><span class="sxs-lookup"><span data-stu-id="bed2e-116">EMF+ Dual metafiles contain [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] records.</span></span> <span data-ttu-id="bed2e-117">Każdy [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] rekordów w dwóch EMF + metaplik łączyć alternatywny [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] rekordu.</span><span class="sxs-lookup"><span data-stu-id="bed2e-117">Each [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] record in an EMF+ Dual metafile is paired with an alternate [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] record.</span></span> <span data-ttu-id="bed2e-118">Metapliki takie mogą być wyświetlane przez [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] lub [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bed2e-118">Such metafiles can be displayed by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] or by [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span>  
  
 <span data-ttu-id="bed2e-119">W poniższym przykładzie przedstawiono metaplik, który został wcześniej zapisany jako plik.</span><span class="sxs-lookup"><span data-stu-id="bed2e-119">The following example displays a metafile that was previously saved as a file.</span></span> <span data-ttu-id="bed2e-120">Metaplik jest wyświetlana z jego lewego górnego rogu na (100, 100).</span><span class="sxs-lookup"><span data-stu-id="bed2e-120">The metafile is displayed with its upper-left corner at (100, 100).</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="bed2e-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bed2e-121">See Also</span></span>  
 [<span data-ttu-id="bed2e-122">Obrazy, mapy bitowe i metapliki</span><span class="sxs-lookup"><span data-stu-id="bed2e-122">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)