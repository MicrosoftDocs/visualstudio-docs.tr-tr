---
title: 'Nasıl yapılır: WPF izleme bilgilerini görüntüleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: be3c6859-06e1-459e-9fd0-46375b5f55ef
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 99fc861c627a094f9f5e4e67a6b034ecdd407688
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476230"
---
# <a name="how-to-display-wpf-trace-information"></a>Nasıl Yapılır: WPF İzleme Bilgilerini Görüntüleme
[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] WPF uygulamalardan hata ayıklama izleme bilgilerini alabilir ve bu bilgileri görüntülemek **çıkış** penceresi. Hata ayıklama izleme bilgilerini görüntülemek için WPF izleme etkinleştirilmesi gerekir.  
  
 WPF izleme App.Config dosyası veya program aracılığıyla kullanarak etkinleştirebilirsiniz <xref:System.Diagnostics.PresentationTraceSources> sınıfı. Kullanarak WPF izlemeyi etkinleştirmek için daha kolay bir yoludur **seçenekleri** penceresi. WPF izleme web uygulamaları için desteklenmiyor.  
  
### <a name="to-enable-or-customize-wpf-trace-information"></a>Etkinleştirmek veya WPF izleme bilgilerini özelleştirme  
  
1.  Üzerinde **Araçları** menüsünde, select **seçenekleri**.  
  
2.  İçinde **seçenekleri** iletişim kutusunda, sol taraftaki kutusu açın **hata ayıklama** düğümü.  
  
3.  Altında **hata ayıklama**, tıklatın **çıktı penceresi**.  
  
4.  Altında **genel çıkış ayarları**seçin **tüm çıkış hata ayıklama**.  
  
5.  Sağdaki kutusunda arayın **WPF izleme ayarları**.  
  
6.  Açık **WPF izleme ayarları** düğümü.  
  
7.  Altında **WPF izleme ayarları**, etkinleştirmek istediğiniz ayarları kategorisini tıklatın (örneğin, **veri bağlama**).  
  
     Açılır liste denetimi ayarları sütununda görüntülenir **veri bağlama** veya tıklattığınız ne olursa olsun kategorisi.  
  
8.  Aşağı açılan listeye tıklayın ve görmek istediğiniz izleme bilgileri türünü seçin: **tüm**, **kritik**, **hata**, **uyarı**,  **Bilgi**, **ayrıntılı**, veya **ActivityTracing**.  
  
     **Kritik** yalnızca kritik olayları izlemeyi etkinleştirir.  
  
     **Hata** kritik ve hata olaylarını izlemeyi etkinleştirir.  
  
     **Uyarı** kritik, hata, izleme ve uyarı olaylarını sağlar.  
  
     **Bilgi** kritik, hata, uyarı ve bilgi olaylarını izlemeyi etkinleştirir.  
  
     **Ayrıntılı** kritik, hata, uyarı, bilgi ve ayrıntılı olaylarını izlemeyi etkinleştirir.  
  
     **ActivityTracing** Durdur, Başlat, askıya alma, aktarım ve sürdürme olaylarını izlemeyi etkinleştirir.  
  
     Bu izleme bilgilerini düzeylerini, bkz: anlamları hakkında daha fazla bilgi için <xref:System.Diagnostics.SourceLevels>.  
  
9. **Tamam**'ı tıklatın.  
  
### <a name="to-disable-wpf-trace-information"></a>WPF izleme bilgilerini devre dışı bırakmak için  
  
1.  Üzerinde **Araçları** menüsünde, select **seçenekleri**.  
  
2.  İçinde **seçenekleri** iletişim kutusunda, sol taraftaki kutusu açın **hata ayıklama** düğümü.  
  
3.  Altında **hata ayıklama**, tıklatın **çıktı penceresi**.  
  
4.  Sağdaki kutusunda arayın **WPF izleme ayarları**.  
  
5.  Açık **WPF izleme ayarları** düğümü.  
  
6.  Altında **WPF izleme ayarları**, etkinleştirmek istediğiniz ayarları kategorisini tıklatın (örneğin, **veri bağlama**).  
  
     Açılır liste denetimi ayarları sütununda görüntülenir **veri bağlama** veya tıklattığınız ne olursa olsun kategorisi.  
  
7.  Aşağı açılan listeye tıklayın ve seçin **devre dışı**.  
  
8.  **Tamam**'ı tıklatın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF'de hata ayıklama](../debugger/debugging-wpf.md)