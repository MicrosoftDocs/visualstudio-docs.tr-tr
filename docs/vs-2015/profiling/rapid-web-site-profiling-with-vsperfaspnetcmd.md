---
title: VSPerfASPNETCmd ile Hızlı Web sitesi profili oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- proflilng tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
ms.assetid: 9a9d62a6-549a-45ac-a948-76eb98586ac5
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 80acb5030c61bd986bfbd2a5f2b383ac37a25a0c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51760012"
---
# <a name="rapid-web-site-profiling-with-vsperfaspnetcmd"></a>VSPerfASPNETCmd ile Hızlı Web Sitesi Profili Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**VSPerfASPNETCmd** komut satırı aracı sayesinde profiline bir kolayca [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web uygulamaları. Comparison için [VSPerfCmd](../profiling/vsperfcmd.md) komut satırı aracı seçenekleri sınırlı, hiçbir ortam değişkenlerini ayarlamak sahip ve bilgisayarın yeniden başlatılması gerekli değildir. Kullanarak **VSPerfASPNETCmd** bağımsız Profil Oluşturucu ile profil oluşturma için tercih edilen yöntemdir. Daha fazla bilgi için [nasıl yapılır: tek başına Profiler yükleme](../profiling/how-to-install-the-stand-alone-profiler.md).  
  
> [!NOTE]
>  Windows 8 ve Windows Server 2012'deki Gelişmiş güvenlik özellikleri Visual Studio profil oluşturucu bu platformlarda veri toplayan bir şekilde önemli değişiklikler gerekmiştir. Windows Store apps ayrıca yeni toplama teknikleri gerektirir. Bkz: [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Eşzamanlılık verileri toplama veya duraklatma ve sürdürme kullanarak profil oluşturma gibi bazı senaryolarda **VSPerfCmd** tercih edilen profil oluşturma yöntemidir.  
  
> [!NOTE]
>  Profil araçlarının komut satırı araçları tools\performance Tools alt dizininde içinde bulunan [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] yükleme dizini. 64 bit bilgisayarlarda, 32 bit tools\performance araçları dizininde VSPerfASPNETCmd aracını kullanın. Profil oluşturucu komut satırı araçlarını kullanmak için Araçlar yolunu komut istemi penceresinin PATH ortam değişkenine ekleyin veya komutun kendisine eklemeniz gerekir. Daha fazla bilgi için [komut satırı araçları yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
## <a name="profiling-an-aspnet-application"></a>Bir ASP.NET uygulaması için profil oluşturma  
 Profil için bir [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web uygulaması, aşağıdaki bölümlerde açıklanan komutlardan birini yazın. Web sitesi başlatılır ve Profil Oluşturucu veri toplamaya başlar. Uygulamanızın çalışma ve tarayıcıyı kapatın. Profil oluşturmayı durdurmak için komut istemi penceresinde Enter tuşuna basın.  
  
> [!NOTE]
>  Varsayılan olarak, sonra Komut İstemi'ni döndürmeyen bir **vsperfaspnetcmd** komutu. Kullanabileceğiniz **/nowait** döndürmek için komut istemi zorlamak için seçeneği. Bkz: [/nowait seçeneğini kullanarak](#UsingNoWait).  
  
## <a name="to-collect-application-statistics-by-using-the-sampling-method"></a>Örnekleme yöntemini kullanarak uygulama istatistikleri toplamak için  
 Örnekleme profili oluşturma yöntemi, varsayılan değerdir **VSPerfASPNETCmd** araç ve komut satırında belirtilmesi gerekmez. Aşağıdaki komut satırı belirtilen Web uygulamasından uygulama istatistikleri toplar:  
  
 **vsperfaspnetcmd**  *websiteUrl*  
  
## <a name="to-collect-detailed-timing-data-by-using-the-instrumentation-method"></a>Ayrıntılı izleme metodunu kullanarak zamanlama verileri toplamak için  
 Dinamik olarak derlenmiş ayrıntılı zamanlama verileri toplamak için şu komut satırını kullanın [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web uygulaması:  
  
 **vsperfaspnetcmd/Trace***websiteUrl*  
  
 Statik olarak derlenmiş bir .dll dosyaları Web uygulamanızın profilini oluşturmak istiyorsanız, kullanarak dosyaları işaretlemelidir [Vsınstr](../profiling/vsinstr.md) komut satırı aracı. Vsperfaspnetcmd/Trace komut dosyalarından izleme eklenmiş veriler içerir.  
  
## <a name="to-collect-net-memory-data"></a>.NET bellek verileri toplamak için  
 **/Memory** seçeneği nesnelerin .NET bellek ayırma hakkında veri toplar ve bu nesnelerin yaşam süresi hakkında veri toplayabilirsiniz. Ayırma veri koleksiyondur varsayılan modunu **/Memory** veri seçenek ve komut satırında belirtilmesi gerekmez.  
  
 **vsperfaspnetcmd /memory** *websiteUrl*  
  
 Kullanım **ömrü** nesne yaşam verisi ayrıca ayırma verileri toplamak için parametre:  
  
 **vsperfaspnetcmd /memory:lifetime** *websiteUrl*  
  
 Ayrıca **/Trace** .NET bellek verileri ile ayrıntılı zamanlama bilgileri içerecek şekilde seçeneği:  
  
 **vsperfaspnetcmd /memory**[**: ömür**]   **/trace**`websiteUrl`  
  
## <a name="to-collect-tier-interaction-data"></a>Katman etkileşim verileri toplamak için  
  
> [!WARNING]
>  Katman etkileşimli profil oluşturma (TIP) veri kullanarak toplanması [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], veya [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)]. Ancak, katman etkileşimli profil oluşturma veri yalnızca görüntülenebilir [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] ve [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
>   
>  Windows 8 veya Windows Server 2012'de ipucu verilerini toplamak için izlemeyi kullanma (**/trace**) seçeneği.  
  
 Veri örnekleme ile Katman etkileşim verileri toplamak için:  
  
 **vsperfaspnetcmd ıntellitrace'in** `websiteUrl`  
  
 Katman etkileşim verileri ile ölçümlü izleme verilerini toplamak için:  
  
 **vsperfaspnetcmd/Trace ıntellitrace'in** *websiteUrl*  
  
 Katman etkileşim verileri ile .NET bellek verileri toplamak için:  
  
 **vsperfaspnetcmd /memory**[**: ömür**] **/İpucu**_websiteUrl_  
  
##  <a name="UsingNoWait"></a> / Nowait seçeneğini kullanma  
 Varsayılan olarak, sonra Komut İstemi'ni döndürmeyen bir **vsperfaspnetcmd** komutu. Döndürülecek komut istemi zorlamak için aşağıdaki sözdizimi seçeneğini kullanabilirsiniz. Ardından, komut istemi penceresinde diğer işlemleri gerçekleştirebilirsiniz. Profil oluşturma sona erdirmek için kullanmak **/shutdown** seçeneği ayrı bir **vsperfaspnetcmd** komutu.  
  
 Profil oluşturma başlamak için:  
  
 **vsperfaspnetcmd** [*/Seçenekler*] **/nowait**_websiteUrl_  
  
 Profil oluşturma sona erdirmek için:  
  
 **vsperfaspnetcmd/shutdown** *websiteUrl*  
  
## <a name="additional-options"></a>Ek Seçenekler  
 Aşağıdaki seçeneklerden herhangi biri daha önce hariç Bu bölümde listelenen komutlar ekleyebilirsiniz **vsperfaspnetcmd/shutdown** komutu.  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/ Çıktı:** `VspFile`|Varsayılan olarak, profil oluşturma veri (.vsp) dosyasının dosya adı geçerli dizinde oluşturulan **PerformanceReport.vsp**. / Output seçeneği farklı bir konum, dosya adı veya her ikisini de belirtmek için kullanın.|  
|**/ PackSymbols: kapalı**|Varsayılan olarak, VsPerfASPNETCmd (işlev ve parametre adları, vb.) semboller .vsp dosyasına katıştırır. Simgeler ekleme, profil oluşturma veri dosyası çok büyük hale getirebilirsiniz. Erişim verilerini çözümlediğinizde semboller içeren .pdb dosyaları olacaksa, packsymbols kullanın: kapalı simgelerini ekleme devre dışı bırakma seçeneği.|



