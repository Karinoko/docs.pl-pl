---
title: "Błąd dostępu do ścieżki pliku"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2c86d46c884617be152a5954426e9ddd6ef61651
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="pathfile-access-error"></a><span data-ttu-id="00ca1-102">Błąd dostępu do ścieżki/pliku</span><span class="sxs-lookup"><span data-stu-id="00ca1-102">Path/File access error</span></span>
<span data-ttu-id="00ca1-103">Podczas operacji dostępu do plików lub dostępu do dysku systemu operacyjnego nie można ustanowić połączenia między ścieżkę i nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="00ca1-103">During a file-access or disk-access operation, the operating system could not make a connection between the path and the file name.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="00ca1-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="00ca1-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="00ca1-105">Upewnij się, że specyfikacji pliku jest poprawnie sformatowana.</span><span class="sxs-lookup"><span data-stu-id="00ca1-105">Make sure the file specification is correctly formatted.</span></span> <span data-ttu-id="00ca1-106">Nazwa pliku może zawierać pełną (bezwzględna) lub względna ścieżka.</span><span class="sxs-lookup"><span data-stu-id="00ca1-106">A file name can contain a fully qualified (absolute) or relative path.</span></span> <span data-ttu-id="00ca1-107">Jest w pełni kwalifikowana ścieżka zaczyna się od nazwy dysku (jeśli znajduje się na innym dysku) i wyświetla jawne ścieżka od elementu głównego do pliku.</span><span class="sxs-lookup"><span data-stu-id="00ca1-107">A fully qualified path starts with the drive name (if the path is on another drive) and lists the explicit path from the root to the file.</span></span> <span data-ttu-id="00ca1-108">Dowolną ścieżkę, która nie jest w pełni kwalifikowana jest względne wobec bieżącego dysku i katalogu.</span><span class="sxs-lookup"><span data-stu-id="00ca1-108">Any path that is not fully qualified is relative to the current drive and directory.</span></span>  
  
2.  <span data-ttu-id="00ca1-109">Upewnij się, że nie próbował zapisać plik, który zastąpić istniejący plik tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="00ca1-109">Make sure that you did not attempt to save a file that would replace an existing read-only file.</span></span> <span data-ttu-id="00ca1-110">Jeśli jest to możliwe, zmień ten atrybut tylko do odczytu z pliku docelowego lub Zapisz plik z inną nazwą pliku.</span><span class="sxs-lookup"><span data-stu-id="00ca1-110">If this is the case, change the read-only attribute of the target file, or save the file with a different file name.</span></span>  
  
3.  <span data-ttu-id="00ca1-111">Upewnij się, że nie próbując otworzyć plik tylko do odczytu w kolejnych `Output` lub `Append` tryb.</span><span class="sxs-lookup"><span data-stu-id="00ca1-111">Make sure you did not attempt to open a read-only file in sequential `Output` or `Append` mode.</span></span> <span data-ttu-id="00ca1-112">Jeśli tak jest, otwórz plik w `Input` tryb lub zmień ten atrybut tylko do odczytu pliku.</span><span class="sxs-lookup"><span data-stu-id="00ca1-112">If this is the case, open the file in `Input` mode or change the read-only attribute of the file.</span></span>  
  
4.  <span data-ttu-id="00ca1-113">Upewnij się, że nie próbował zmienić [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] projektu bazy danych lub dokumentu.</span><span class="sxs-lookup"><span data-stu-id="00ca1-113">Make sure you did not attempt to change a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] project within a database or document.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00ca1-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="00ca1-114">See Also</span></span>  
 [<span data-ttu-id="00ca1-115">Error — typy</span><span class="sxs-lookup"><span data-stu-id="00ca1-115">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)