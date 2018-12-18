---
title: Windows Güvenlik Duvarı uzaktan hata ayıklama için yapılandırma | Microsoft Docs
ms.date: 10/31/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: da505c6193dd7d05cc10a8e7cec8383f8ee3adfc
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53058603"
---
# <a name="configure-windows-firewall-for-remote-debugging"></a>Uzaktan hata ayıklama için Windows Güvenlik duvarını yapılandırma

Windows Güvenlik Duvarı tarafından korunan bir ağda güvenlik duvarı uzaktan hata ayıklama izin verecek şekilde yapılandırılması gerekir. Yükleme veya başlatma sırasında doğru güvenlik duvarı bağlantı noktalarını açmak Visual Studio ve Uzaktan Hata Ayıklama Araçları'nı deneyin ancak bağlantı noktalarını açmak veya el ile uygulamalara izin vermek de gerekebilir. 

Bu konu, Windows 10 ve 8/8.1 7 uzaktan hata ayıklamayı etkinleştirmek için Windows Güvenlik duvarını açıklar; ve Windows Server 2012 R2, 2012 ve 2008 R2 bilgisayarlarını. Visual Studio ve uzak bilgisayar aynı işletim sistemi çalıştırıyor olmanız gerekmez. Örneğin, Visual Studio bilgisayarı, Windows 10 çalıştırabilirsiniz ve Windows Server 2012 R2 Uzak bilgisayarda çalıştırabilirsiniz.      
  
>[!NOTE]
>Windows Güvenlik Duvarı yapılandırma yönergeleri, farklı işletim sistemlerinde ve önceki Windows sürümleri için biraz daha farklı. Windows 8/8.1, Windows 10 ve Windows Server 2012 ayarlarını kullan word *uygulama*, Windows 7 ve Windows Server 2008 sözcüğünün kullanırken *program*.  

## <a name="configure-ports-for-remote-debugging"></a>Uzaktan hata ayıklama için bağlantı noktalarını yapılandırma  

Visual Studio ve uzaktan hata ayıklayıcı yükleme veya başlatma sırasında doğru bağlantı noktalarını açmayı deneyin. Ancak, bir üçüncü taraf güvenlik duvarı gibi bazı senaryolarda el ile bağlantı noktalarını açmanız gerekebilir. 

**Bir bağlantı noktasını açmak için:**
  
1. Windows içinde **Başlat** menü, arayın ve açık **Gelişmiş Güvenlik Özellikli Windows Güvenlik Duvarı**. Windows 10'da budur **Windows Defender Güvenlik Duvarı'nı Gelişmiş Güvenlik Özellikli**.
   
1. Yeni bir gelen bağlantı noktası için seçin **gelen kuralları** seçip **yeni kural**. Bir giden kuralı seçin **giden kuralları** yerine.

1. İçinde **yeni gelen kuralı Sihirbazı**seçin **bağlantı noktası**ve ardından **sonraki**. 
   
1. Şunlardan birini seçin **TCP** veya **UDP**bağlı olarak aşağıdaki tablolarda bulunan bağlantı noktası numarası.
   
1. Altında **belirli yerel bağlantı noktaları**aşağıdaki tablodan bir bağlantı noktası numarası girin ve seçin **sonraki**.
   
1. Seçin **bağlantıya izin**ve ardından **sonraki**.
   
1. Uzak bağlantı için ağ türü de dahil olmak üzere etkinleştirmek için bir veya daha fazla ağ türü seçin ve ardından **sonraki**.
   
1. Kural için bir ad ekleyin (örneğin, **msvsmon**, **IIS**, veya **Web dağıtımı**) ve ardından **son**.

   Yeni Kural görünür olmalıdır ve'seçilmesi **gelen kuralları** veya **giden kuralları** listesi.

### <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>Uzak bilgisayarda uzaktan hata ayıklamayı etkinleştirme bağlantı

Uzaktan hata ayıklama için aşağıdaki bağlantı noktalarını uzak bilgisayarda açık olması gerekir:

|**Bağlantı Noktaları**|**Gelen ve giden**|**Protokolü**|**Açıklama**|   
|-|-|-|-|
|4022|gelen|TCP|VS 2017 için. Her bir Visual Studio sürümü için 2 bağlantı noktası numarası artırır. Daha fazla bilgi için [Visual Studio uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md).|  
|4023|gelen|TCP|VS 2017 için. Her bir Visual Studio sürümü için 2 bağlantı noktası numarası artırır. Bu bağlantı noktası yalnızca kullanılan uzaktan hata ayıklama uzaktan hata ayıklayıcı 64-bit sürümünden 32 bitlik bir işlem var. Daha fazla bilgi için [Visual Studio uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md).| 
|3702|Giden|UDP|(İsteğe bağlı) Uzaktan hata ayıklayıcı bulma işlemi için gereklidir.|    
  
Seçerseniz **yönetilen Uyumluluk modunu kullan** altında **Araçları** > **seçenekleri** > **hata ayıklama**açın Bu ek uzaktan hata ayıklayıcı bağlantı noktası. Hata ayıklayıcı yönetilen uyumluluk modu, eski, hata ayıklayıcı Visual Studio 2010 sürümünü sağlar. 

|**Bağlantı Noktaları**|**Gelen ve giden**|**Protokolü**|**Açıklama**|  
|-|-|-|-|  
|135, 139, 445|Giden|TCP|Gerekli.|  
|137, 138|Giden|UDP|Gerekli.|  

Etki alanı ilkeniz ağ iletişimi, IPSec gerçekleştirilmesini gerektiriyorsa, hem Visual Studio hem de uzak bilgisayarlarda ek bağlantı noktalarını açmanız gerekir. Uzak bir IIS web sunucusunda hata ayıklamak için Uzak bilgisayar üzerindeki 80 numaralı bağlantı noktasını açın.

|**Bağlantı Noktaları**|**Gelen ve giden**|**Protokolü**|**Açıklama**|  
|-|-|-|-|  
|500, 4500|Giden|UDP|Etki alanı ilkeniz ağ iletişimi, IPSec gerçekleştirilmesini gerektiriyorsa gereklidir.|  
|80|Giden|TCP|Web sunucusu hata ayıklama için gereklidir.|

Windows Güvenlik Duvarı üzerinden belirli uygulamalara izin vermek için bkz: [Windows Güvenlik Duvarı üzerinden uzaktan hata ayıklamayı Yapılandır](#configure-remote-debugging-through-windows-firewall). 

## <a name="configure-remote-debugging-through-windows-firewall"></a>Windows Güvenlik Duvarı üzerinden uzaktan hata ayıklamayı Yapılandır

Uzak bilgisayarda uzaktan hata ayıklama araçlarını yüklemeniz veya paylaşılan klasörden çalıştırabilirsiniz. Her iki durumda da, uzak bilgisayarda güvenlik duvarı doğru şekilde yapılandırılması gerekir. 

Bir uzak bilgisayarda uzaktan hata ayıklama araçları dahildir.  
  
*\<Visual Studio yükleme dizini\>\\Common7\\IDE\\uzaktan hata ayıklayıcı\\\<x86*, *x64*, veya  *Appx*\> 
  
### <a name="allow-and-configure-the-remote-debugger-through-windows-firewall"></a>İzin ve Windows Güvenlik Duvarı üzerinden uzaktan hata ayıklayıcı yapılandırma 
  
1. Windows içinde **Başlat** menü, arayın ve açık **Windows Güvenlik Duvarı**, veya **Windows Defender Güvenlik Duvarı**. 
  
1. Seçin **uygulama Windows Güvenlik Duvarı üzerinden izin**.  
  
1.  Varsa **uzaktan hata ayıklayıcı** veya **Visual Studio uzaktan hata ayıklayıcı** altında görünmüyor **izin verilen uygulamalar ve Özellikler**seçin **ayarlarınıdeğiştir**ve ardından **başka bir uygulamanın ver**. 

1.  Uzaktan hata ayıklayıcı uygulama yine de listede yoksa **uygulama ekleme** iletişim kutusunda **Gözat**gidin  *\<Visual Studio yükleme dizini\> \\Common7\\IDE\\uzaktan hata ayıklayıcı\\\<x86*, *x64*, veya *Appx* \> , uygulamanız için uygun mimariyi bağlı olarak. Seçin *msvsmon.exe*ve ardından **Ekle**.  
    
1.  İçinde **uygulamaları** listesinden **uzaktan hata ayıklayıcı** eklediğiniz. Seçin **ağ türleri**ve ardından uzak bağlantı için ağ türü dahil olmak üzere, bir veya daha fazla ağ türü seçin. 
    
1.  Seçin **Ekle**ve ardından **Tamam**.

## <a name="troubleshooting"></a>Uzaktan hata ayıklama bağlantı sorunlarını giderme
  
Uzaktan hata ayıklayıcı ile uygulamanıza bağlanamıyorsa, uzaktan hata ayıklama güvenlik duvarı bağlantı noktaları, protokolleri, ağ türlerini ve uygulama ayarlarının doğru olduğunu doğrulayın. 

- Windows içinde **Başlat** menü, arayın ve açık **Windows Güvenlik Duvarı**seçip **uygulama Windows Güvenlik Duvarı üzerinden izin**. Emin **uzaktan hata ayıklayıcı** veya **Visual Studio uzaktan hata ayıklayıcı** görünür **izin verilen uygulamalar ve Özellikler** seçili bir onay kutusu ve doğru ağ türleri listesi Seçili. Aksi halde [doğru uygulamalar ve ayarlar ekleme](#configure-remote-debugging-through-windows-firewall).
  
- Windows içinde **Başlat** menü, arayın ve açık **Gelişmiş Güvenlik Özellikli Windows Güvenlik Duvarı**. Emin **uzaktan hata ayıklayıcı** veya **Visual Studio uzaktan hata ayıklayıcı** altında görünür **gelen kuralları** (ve isteğe bağlı olarak **giden kuralları**) Yeşil bir onay işareti ile tüm ayarların doğru olduğundan. 
  
  - Kural ayarlarını görüntülemek veya değiştirmek için sağ **uzaktan hata ayıklayıcı** uygulama listesini seçip **özellikleri**. Kullanım **özellikleri** etkinleştirmek veya kuralı devre dışı bırak veya değiştirmek için sekme bağlantı noktası numaraları, protokolleri ve ağ türleri. 
  - Uzaktan hata ayıklayıcı uygulama kuralları listesinde görünmüyorsa [ekleyin ve doğru bağlantı noktalarını yapılandırma](#configure-ports-for-remote-debugging). 

## <a name="see-also"></a>Ayrıca bkz.  
[Uzaktan hata ayıklama](../debugger/remote-debugging.md)

[Visual Studio uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md)
