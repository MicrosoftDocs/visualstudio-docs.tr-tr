---
title: "Nasıl yapılır: tek başına Profiler'ı yükleme | Microsoft Docs"
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, installing stand-alone profiler
- profiling tools, stand-alone profiler
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 55c9e7c6ec4a34d59c45b2a56abedaa6d3fd2974
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942456"
---
# <a name="how-to-install-the-stand-alone-profiler"></a>Nasıl yapılır: bağımsız profil oluşturucuyu yükleme
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bir komut satırı tabanlı yüklemeden çalıştırabilirsiniz bağımsız profil oluşturucuyu sağlar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE. Bir bilgisayar yok ya da yüklü bir geliştirme ortamı olamaz bu durum oluşur. Örneğin, bir üretim web sunucusunda bir geliştirme ortamı yüklememelidir.  
  
> [!NOTE]
>  Bir ASP.NET web sitesi için performans verilerini toplamak için bağımsız profil oluşturucuyu kullanırken [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) Çizgi aracı üzerinden önerilir [VSPerfCmd](../profiling/vsperfcmd.md) aracı.  
  
### <a name="to-install-the-stand-alone-profiler"></a>Bağımsız profil oluşturucuyu yükleme  
  
1. Bağımsız Profil yükleyicisini bulun (*vs_profiler.exe*) üzerinde [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yükleme medyasını içeren dizine *\Standalone Profiler* yolu ve çalıştırın.  
  
2. Yollarını eklemek *vsintr.exe* ve *msdis150.dll* sistem yolu.  
  
   > [!NOTE]
   >  Varsayılan yüklemede [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], *vsinstr.exe* ve *msdis150.dll* bulunan *\Program Files\Visual Studio 10\Team Araçlar\Performans Araçları*.  
  
3. Komut isteminde **Vsınstr**.  
  
   > [!NOTE]
   >  Vsinstr.exe yönelik kullanım bilgilerini gösterilirse, her şeyin doğru şekilde ayarlanır. Vsinstr.exe belirten bir hata göreceğiniz ya da bağımlılıklarından biri bulunamadı, cihazınızdaki yollar 2. adımda açıklandığı gibi doğru şekilde ayarlanmış olduğundan emin olun.  
  
4. Sembol sunucusu ayarlamak, **_NT_SYMBOL_PATH** değişkenini **symsrv\*symsrv.dll\*c:\localcache\*http://msdl.microsoft.com/download/symbols**  
  
5. Sistem ortam değişkenlerini kullanarak sembol sunucunuz ayarladıktan sonra komut satırından profil oluşturucu Araçlar yeni bir komut isteminde çalıştırın. Bu, etkili olması yeni ortam değişkenlerini tanır. Komut İstemi penceresinde aşağıdaki komutu yazın:  
  
    **COMSPEC % Başlat**  
  
   > [!NOTE]
   >  Sembol sunucusu paketi ayarlama konusunda ayrıntılı yönergeler için bkz: [nasıl yapılır: başvuru Windows sembol bilgileri](../profiling/how-to-reference-windows-symbol-information.md).  
  
6. Kullanım [VSPerfReport](../profiling/vsperfreport.md) aracı profil oluşturma veri (.vsp) dosyasına, semboller serileştirmek için. Kullanım **VSPerfReport userrulesdirectory packsymbols** anahtarlar. Veri dosyasına eklenmiş semboller yoksa _NT_SYMBOL_PATH ortam değişken kümesi olduğunu emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Komut satırından profil](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [İzlenecek yol: Komut satırı kullanarak profil örnekleme](../profiling/walkthrough-command-line-profiling-using-sampling.md)   
 [İzlenecek yol: İzleme metodunu kullanarak komut satırı profil](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)   
 [Nasıl yapılır: başvuru Windows sembol bilgileri](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)