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
ms.openlocfilehash: d89dbc0b752c2b8c538ec53769c166b6edbd802f
ms.sourcegitcommit: 1df0ae74af03bcf0244129a29fd6bd605efc9f61
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50915279"
---
1. Uzak bilgisayarda bulmak ve başlatmak **uzaktan hata ayıklayıcı** gelen **Başlat** menüsü. 
   
   Uzak bilgisayarda yönetici izinlerine sahip değilseniz, sağ **uzaktan hata ayıklayıcı** seçin **yönetici olarak çalıştır**. Aksi takdirde, yalnızca başlatın normalde.

   Farklı sürümlerini olabilir *msvsmon.exe* içinde *x64*, *x32*, veya başka klasörler. Uygulamanızda hata ayıklama gereken sürümü başlatmak istediğinizden emin olun. 
   
1. İlk kez uzaktan hata ayıklayıcıyı başlattığınızda (veya önce yapılandırdığınızdan,), **uzaktan hata ayıklama Yapılandırması** iletişim kutusu görüntülenir.  
  
    ![Uzaktan hata ayıklayıcı yapılandırma](../media/remotedebuggerconfwizardpage.png "uzaktan hata ayıklayıcı yapılandırma")  
  
1. Windows Web Servisleri API, yalnızca Windows Server 2008 R2 üzerinde gerçekleşen yüklü değilse, seçin **yükleme** düğmesi.  
  
1. Uzak Araçlar üzerinde kullanmak istediğiniz en az bir ağ türünü seçin. Bilgisayarları bir etki alanına bağlıysanız, ilk öğe seçmeniz gerekir. Bilgisayar bir çalışma grubunda veya ev grubu bağlıysa, uygun şekilde ikinci veya üçüncü öğeyi seçin.  
  
1. Seçin **uzaktan hata ayıklamayı Yapılandır** güvenlik duvarını yapılandırmak ve uzaktan hata ayıklayıcıyı başlatın.  
  
1. Yapılandırma tamamlandığında, **uzaktan hata ayıklayıcı** penceresi görüntülenir.
  
    ![Uzaktan hata ayıklayıcı penceresini](../media/remotedebuggerwindow.png "uzaktan hata ayıklayıcı penceresi")
  
    Uzaktan hata ayıklayıcı şimdi bir bağlantı için bekliyor. Sunucu adı ve bağlantı noktası numarasına uzaktan bağlantı yapılandırmasını Visual Studio'da ayarlayın.  
  
Uzaktan hata ayıklayıcıyı durdurmak için seçin **dosya** > **çıkış**. Buradan yeniden **Başlat** menüsünden veya komut satırından:  
  
```cmd
<Remote debugger installation directory>\msvsmon.exe
```
