---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 95d76781f651b681b81e4dd18848b404d8a85664
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38809274"
---
 Kodunuzu Visual Studio bilgisayar üzerinde oluşturmak simgelerle hata ayıklamanız mümkün olması gerekir. Uzaktan hata ayıklayıcı performansının çok yerel semboller kullandığınızda daha iyidir.  Uzak sembolleri kullanmanız gerekirse, uzak makinede simgeleri aramak için uzaktan hata ayıklama İzleyicisi söylemeniz gerekir.  
  
 Visual Studio 2013 güncelleştirme 2'de başlayarak, yönetilen kod için Uzak semboller kullanmak için aşağıdaki msvsmon komut satırı anahtarını kullanabilirsiniz: `Msvsmon /FallbackLoadRemoteManagedPdbs`  
  
 Daha fazla bilgi için lütfen uzak hata ayıklama yardıma bakın (basın **F1** uzaktan hata ayıklayıcı penceresinde veya tıklatın **Yardım > kullanım**). Daha fazla bilgi bulabilirsiniz [.NET uzaktan sembolü yükleniyor Visual Studio 2012 ve 2013 değişiklikleri](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013.aspx)