---
title: VSPerfASPNETCmd ile Hızlı Web sitesi profili oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- proflilng tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f0ad2c1411a47acd0219223fe928e4150368c80a
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43780553"
---
# <a name="rapid-web-site-profiling-with-vsperfaspnetcmd"></a>Profil oluşturma VSPerfASPNETCmd ile hızlı web sitesi

**VSPerfASPNETCmd** komut satırı aracı sayesinde profiline bir kolayca [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] web uygulamaları. Comparison için [VSPerfCmd](../profiling/vsperfcmd.md) komut satırı aracı seçenekleri sınırlı, hiçbir ortam değişkenlerini ayarlamak sahip ve bilgisayarın yeniden başlatılması gerekli değildir. Kullanarak **VSPerfASPNETCmd** bağımsız Profil Oluşturucu ile profil oluşturma için tercih edilen yöntemdir. Daha fazla bilgi için [nasıl yapılır: bağımsız profil oluşturucuyu yükleme](../profiling/how-to-install-the-stand-alone-profiler.md).

> [!NOTE]
> Windows 8 ve Windows Server 2012'deki Gelişmiş güvenlik özellikleri Visual Studio profil oluşturucu bu platformlarda veri toplayan bir şekilde önemli değişiklikler gerekmiştir. UWP uygulamaları, ayrıca yeni toplama teknikleri gerektirir. Bkz: [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

 Eşzamanlılık verileri toplama veya duraklatma ve sürdürme kullanarak profil oluşturma gibi bazı senaryolarda **VSPerfCmd** tercih edilen profil oluşturma yöntemidir.

> [!NOTE]
> Profil araçlarının komut satırı araçları yerleştirilir *tools\performance Araçları* Visual Studio yükleme dizininin alt. 64-bit bilgisayarlarda, 32-bit bulunan VSPerfASPNETCmd aracını *tools\performance Araçları* dizin. Profil oluşturucu komut satırı araçlarını kullanmak için Araçlar yolunu komut istemi penceresinin PATH ortam değişkenine ekleyin veya komutun kendisine eklemeniz gerekir. Daha fazla bilgi için [komut satırı araçları yolunu belirtin](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

## <a name="profile-an-aspnet-application"></a>Bir ASP.NET uygulamasının profilini oluşturun

Profil için bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] web uygulaması, aşağıdaki bölümlerde açıklanan komutlardan birini yazın. Web sitesi başlatılır ve Profil Oluşturucu veri toplamaya başlar. Uygulamanızın çalışma ve tarayıcıyı kapatın. Profil oluşturmayı durdurmak için basın **Enter** komut istemi penceresinde anahtar.

> [!NOTE]
> Varsayılan olarak, sonra Komut İstemi'ni döndürmeyen bir **vsperfaspnetcmd** komutu. Kullanabileceğiniz **/nowait** döndürmek için komut istemi zorlamak için seçeneği. Bkz: [/nowait seçeneğini](#use-the-nowait-option).

## <a name="to-collect-application-statistics-by-using-the-sampling-method"></a>Örnekleme yöntemini kullanarak uygulama istatistikleri toplamak için
 Örnekleme profili oluşturma yöntemi, varsayılan değerdir **VSPerfASPNETCmd** araç ve komut satırında belirtilmesi gerekmez. Aşağıdaki komut satırı belirtilen web uygulamasından uygulama istatistikleri toplar:

 **vsperfaspnetcmd**  *websiteUrl*

## <a name="to-collect-detailed-timing-data-by-using-the-instrumentation-method"></a>Ayrıntılı izleme metodunu kullanarak zamanlama verileri toplamak için

Dinamik olarak derlenmiş ayrıntılı zamanlama verileri toplamak için şu komut satırını kullanın [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] web uygulaması:

**vsperfaspnetcmd/Trace***websiteUrl*

Statik olarak profil isterseniz derlenmiş. *dll* dosyaları web uygulamanızda kullanarak dosyaları işaretlemelidir [Vsınstr](../profiling/vsinstr.md) komut satırı aracı. Vsperfaspnetcmd/Trace komut dosyalarından izleme eklenmiş veriler içerir.

## <a name="to-collect-net-memory-data"></a>.NET bellek verileri toplamak için

**/Memory** seçeneği nesnelerin .NET bellek ayırma hakkında veri toplar ve bu nesnelerin yaşam süresi hakkında veri toplayabilirsiniz. Ayırma veri koleksiyondur varsayılan modunu **/Memory** veri seçenek ve komut satırında belirtilmesi gerekmez.

 **vsperfaspnetcmd /memory** *websiteUrl*

 Kullanım **ömrü** nesne yaşam verisi ayrıca ayırma verileri toplamak için parametre:

 **vsperfaspnetcmd /memory:lifetime** *websiteUrl*

 Ayrıca **/Trace** .NET bellek verileri ile ayrıntılı zamanlama bilgileri içerecek şekilde seçeneği:

 **vsperfaspnetcmd /memory**[**: ömür**]   **/trace**`websiteUrl`

## <a name="to-collect-tier-interaction-data"></a>Katman etkileşim verileri toplamak için

> [!WARNING]
> Katman etkileşimli profil oluşturma (TIP) verileri, herhangi bir Visual Studio sürümünü kullanarak toplanabilir. Ancak, yalnızca Visual Studio Enterprise'da katman etkileşimli profil oluşturma veri görüntülenebilir.
>
> Windows 8 veya Windows Server 2012'de ipucu verilerini toplamak için izlemeyi kullanma (**/trace**) seçeneği.

Veri örnekleme ile Katman etkileşim verileri toplamak için:

**vsperfaspnetcmd ıntellitrace'in** `websiteUrl`

Katman etkileşim verileri ile ölçümlü izleme verilerini toplamak için:

**vsperfaspnetcmd/Trace ıntellitrace'in** *websiteUrl*

Katman etkileşim verileri ile .NET bellek verileri toplamak için:

**vsperfaspnetcmd /memory**[**: ömür**] **/İpucu**_websiteUrl_

## <a name="use-the-nowait-option"></a>/ Nowait seçeneğini kullanın

Varsayılan olarak, sonra Komut İstemi'ni döndürmeyen bir **vsperfaspnetcmd** komutu. Döndürülecek komut istemi zorlamak için aşağıdaki sözdizimi seçeneğini kullanabilirsiniz. Ardından, komut istemi penceresinde diğer işlemleri gerçekleştirebilirsiniz. Profil oluşturma sona erdirmek için kullanmak **/shutdown** seçeneği ayrı bir **vsperfaspnetcmd** komutu.

Profil oluşturma başlamak için:

**vsperfaspnetcmd** [*/Seçenekler*] **/nowait**_websiteUrl_

Profil oluşturma sona erdirmek için:

**vsperfaspnetcmd/shutdown** *websiteUrl*

## <a name="additional-options"></a>Ek Seçenekler

Aşağıdaki seçeneklerden herhangi biri daha önce hariç Bu bölümde listelenen komutlar ekleyebilirsiniz **vsperfaspnetcmd/shutdown** komutu.

|Seçenek|Açıklama|
|------------|-----------------|
|**/ Çıktı:** `VspFile`|Varsayılan olarak, profil oluşturma verilerinin (. *Vsp*) dosyası geçerli dizin dosyası adıyla oluşturulur **PerformanceReport.vsp**. / Output seçeneği farklı bir konum, dosya adı veya her ikisini de belirtmek için kullanın.|
|**/ PackSymbols: kapalı**|Varsayılan olarak, VsPerfASPNETCmd simgeleri (işlev ve parametre adları ve benzeri) katıştırır. *vsp* dosya. Simgeler ekleme, profil oluşturma veri dosyası çok büyük hale getirebilirsiniz. Erişiminiz. *pdb* verileri analiz ederken, semboller içeren dosyaları packsymbols kullanın: kapalı simgelerini ekleme devre dışı bırakma seçeneği.|
