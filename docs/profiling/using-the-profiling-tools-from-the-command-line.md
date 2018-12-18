---
title: Profil oluşturma kullanarak komut satırından araçları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- command line, performance tools
- command-line tools, performance tools
- profiling tools,command line
- tools, command-line
- command line, tools
ms.assetid: 6593fa82-181e-4009-a0ed-02aa24c2c063
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ac28817a7c72b7ecfbbc3c76dd3626f0a24d11c9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49882333"
---
# <a name="use-the-profiling-tools-from-the-command-line"></a>Komut satırından profil oluşturma araçlarını kullanma
Komut satırı araçlarını kullanabilirsiniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] profili uygulamalara komut isteminde ve toplu iş dosyaları kullanarak ve komut dosyası profil oluşturma otomatik hale getirmek için profil oluşturma araçları. Bir komut isteminde rapor dosyalarını da oluşturabilirsiniz. Basit bağımsız profil oluşturucuyu olmadığı bilgisayarlarda verileri toplamak için kullanabileceğiniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yüklü.  
  
> [!NOTE]
>  Windows 8 ve Windows Server 2012'deki Gelişmiş güvenlik özellikleri Visual Studio profil oluşturucu bu platformlarda veri toplayan bir şekilde önemli değişiklikler gerekmiştir. UWP uygulamaları, ayrıca yeni toplama teknikleri gerektirir. Bkz: [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Ortak görevler  
  
| Görev | İlgili içerik |
| - | - |
| **Semboller konumunu ayarlayın:** işlevleri ve parametre adlarını görüntülemek için profil oluşturucu sembol erişiminiz olması gerekir (. *pdb*) profili oluşturulan ikili dosyaları. Bu dosyalar, analiz görüntülemek istediğiniz uygulamaları ve Microsoft işletim sistemi için Sembol dosyaları içermelidir. Doğru olduğundan emin olmak için genel Microsoft sembol Sunucusu'nu kullanabilirsiniz. *pdb* Microsoft ikili dosyaları. | -   [Nasıl yapılır: komut satırından sembol dosyası konumlarını belirtme](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md) |
| **Uygulamanızın profilini:** bir hedef uygulama profil oluşturma metodu uygulamanın türüne bağlı profili için kullandığınız seçenekleri ve komut satırı araçları ve hedef yönetilen veya yerel bir uygulama olup. | -   [Komut satırından profil oluşturma yöntemlerini kullanma](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)<br />-   [Bağımsız uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)<br />-   [Profil ASP.NET web uygulamaları](../profiling/command-line-profiling-of-aspnet-web-applications.md)<br />-   [Profil hizmetler](../profiling/command-line-profiling-of-services.md) |
| **.XML veya .csv raporları oluşturun:** komut satırından profil oluşturma için arabirimi görüntülenebilir veri dosyalarını oluşturur [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Da oluşturabilirsiniz. *xml* veya virgülle ayrılmış değer (. *CSV*) VSPerfReport komut satırı aracını kullanarak veri dosyaları. | -   [Komut satırından profil oluşturucu raporlar oluşturma](../profiling/creating-profiler-reports-from-the-command-line.md)<br />-   [VSPerfReport](../profiling/vsperfreport.md) |
| **Profili Visual Studio olmadan bilgisayarlarda kodda:** sahip olmayan bilgisayarlarda uygulama verilerini toplamak için profil oluşturma araçları bağımsız profil oluşturucuyu kullanabilirsiniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yüklü. | -   [Nasıl yapılır: bağımsız profil oluşturucuyu yükleme](../profiling/how-to-install-the-stand-alone-profiler.md) |
  
## <a name="reference"></a>Başvuru  
 [Komut satırı profil araçları başvurusu](../profiling/command-line-profiling-tools-reference.md)  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Performans Gezgini](../profiling/performance-explorer.md)