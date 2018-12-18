---
title: 'Nasıl yapılır: komut satırından sembol dosyası konumlarını belirtme | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 8aa067bb-e8bf-4081-aff0-cfbcf65934a0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 498720ff5b76ce2c3229c9c7a493023318213ae4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49941938"
---
# <a name="how-to-specify-symbol-file-locations-from-the-command-line"></a>Nasıl yapılır: komut satırından sembol dosyası konumlarını belirtme
İşlev adları ve satır numaraları gibi sembol bilgilerini görüntülemek için VSPerfReport komut satırı aracı sembol erişim gerektirir (. *pdb*) profili oluşturulan bileşenleri ve Windows sistem dosyalarını dosya. Bir bileşen derlendiğinde sembol dosyaları oluşturulur. Daha fazla bilgi için [VSPerfReport](../profiling/vsperfreport.md). VSPerfReport sembol dosyaları için aşağıdaki konumlar otomatik olarak arar:  
  
- Belirtilen yollar **/symbolpath** seçeneği veya **_NT_SYMBOL_PATH** ortam değişkeni.  
  
- Burada bir bileşen derlenen tam yerel yolu.  
  
- Profil oluşturma verilerini içeren dizine (. *Vsp* veya. *vsps*) dosyası.  
  
  Microsoft sağlar. *pdb* çok ürünlerin, çevrimiçi bir sembol sunucusunda dosyaları. Raporlama için kullanmakta olduğunuz bilgisayarın Internet'e bağlıysa, VSPerfReport otomatik olarak sembol bilgilerini arama ve dosyalarını yerel depoya kaydetmek için çevrimiçi bir sembol sunucusuna bağlanır.  
  
  Sembol dosyaları ve Microsoft sembol sunucusunun depolama konumu aşağıdaki yöntemlerle belirtebilirsiniz:  
  
- Ayarlama **_NT_SYMBOL_PATH** ortam değişkeni.  
  
- Ekleme **/symbolpath** VSPerfReport komut satırı seçeneği.  
  
  Bu yöntemlerin her ikisi de kullanabilirsiniz.  
  
> [!NOTE]
>  Varsa [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Windows simge dosyaları büyük olasılıkla belirtilmedi için zaten bir konuma yerel bilgisayarda yüklü. Daha fazla bilgi için [nasıl yapılır: başvuru Windows sembol bilgileri](../profiling/how-to-reference-windows-symbol-information.md). Hala VSPerfReport konumu ve bu konunun ilerleyen bölümlerinde açıklandığı sunucusu kullanmak için yapılandırmanız gerekir.  
  
## <a name="specify-windows-symbol-files"></a>Windows sembol dosyalarını belirtin  
  
#### <a name="to-configure-the-use-of-the-windows-symbol-server"></a>Windows sembol sunucusu kullanımını yapılandırmak için  
  
1. Gerekirse, sembol dosyaları yerel olarak depolamak için bir dizin oluşturun.  
  
2. Ayarlamak için aşağıdaki sözdizimini kullanın **_NT_SYMBOL_PATH** ortam değişkeni veya VSPerfReport/symbolpath seçeneği:  
  
    **SRV\\*** *LocalStore* **\*http://msdl.microsoft.com/downloads/symbols**  
  
    Burada *LocalStore* oluşturduğunuz yerel bir dizin yolu.  
  
## <a name="specify-component-symbol-files"></a>Bileşen sembol dosyaları belirtin  
 Profil oluşturma araçları arar. *pdb* bileşenler veya profil oluşturma veri dosyasını içeren klasöre depolanan özgün konumlarına profilinde istediğiniz bileşenlerin dosyaları. Bir veya daha fazla yol ekleyerek aramak için diğer konumlar belirtebilirsiniz **_NT_SYMBOL_PATH** veya **/symbolpath** seçeneği. Ayrı yollarının noktalı virgülle ayırın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut satırı kümeleri **_NT_SYMBOL_PATH** ortam değişkenini Windows sembol sunucusu ve yerel dizine **C:\Symbols**.  
  
 **ayarlama _NT_SYMBOL_PATH srv =\*C:\symbols\*http://msdl.microsoft.com/downloads/symbols**  
  
 VSPerfReport komut satırını ekler *C:\Projects\Symbols* dizin kullanılarak arama yoluna **/symbolpath** seçeneği.  
  
 **VSPerfReport***MyApp* **.exe /SymbolPath:C:\Projects\Symbols userrulesdirectory**