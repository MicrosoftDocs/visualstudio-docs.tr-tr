---
title: 'Nasıl yapılır: WPF izleme bilgilerini görüntüleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: be3c6859-06e1-459e-9fd0-46375b5f55ef
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a91d9f1f58a6905d50e14351bbbaf6fe732c60f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51771241"
---
# <a name="how-to-display-wpf-trace-information"></a>Nasıl Yapılır: WPF İzleme Bilgilerini Görüntüleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] WPF uygulamaları hata ayıklama izleme bilgilerini alabilir ve bu bilgileri görüntülemek **çıkış** penceresi. Hata ayıklama izleme bilgilerini görüntülemek için WPF izleme etkinleştirilmesi gerekir.  
  
 App.Config dosyanızda veya programlama aracılığıyla kullanarak WPF izlemeyi etkinleştirebilirsiniz <xref:System.Diagnostics.PresentationTraceSources> sınıfı. WPF izlemeyi etkinleştirmek için daha kolay bir yolu kullanmaktır **seçenekleri** penceresi. WPF izleme web uygulamaları için desteklenmez.  
  
### <a name="to-enable-or-customize-wpf-trace-information"></a>Etkinleştirmek veya WPF izleme bilgilerini özelleştirme  
  
1.  Üzerinde **Araçları** menüsünde **seçenekleri**.  
  
2.  İçinde **seçenekleri** iletişim kutusunda, sol taraftaki kutudan açın **hata ayıklama** düğümü.  
  
3.  Altında **hata ayıklama**, tıklayın **çıkış penceresine**.  
  
4.  Altında **genel çıkış ayarları**seçin **tüm hata ayıklama çıkışı**.  
  
5.  Sağ taraftaki kutuya Ara **WPF izleme ayarlarını**.  
  
6.  Açık **WPF izleme ayarlarını** düğümü.  
  
7.  Altında **WPF izleme ayarlarını**, etkinleştirmek istediğiniz ayar kategorisine tıklayın (örneğin, **veri bağlama**).  
  
     Aşağı açılan liste denetimi ayarları sütunda yanında görünen **veri bağlama** veya tıkladığınız her kategorisi.  
  
8.  Aşağı açılan listeye tıklayın ve istediğiniz izleme bilgilerini türünü seçin: **tüm**, **kritik**, **hata**, **uyarı**,  **Bilgi**, **ayrıntılı**, veya **ActivityTracing**.  
  
     **Kritik** yalnızca kritik olayları izlemeyi etkinleştirir.  
  
     **Hata** kritik ve hata olaylarını izlemeyi etkinleştirir.  
  
     **Uyarı** kritik, hata, izleme ve uyarı olaylarını etkinleştirir.  
  
     **Bilgi** kritik, hata, uyarı ve bilgi olaylarını izlemeyi etkinleştirir.  
  
     **Ayrıntılı** kritik, hata, uyarı, bilgi ve ayrıntı olaylarını izlemeyi etkinleştirir.  
  
     **ActivityTracing** durdurma, Başlat, askıya alma, aktarımı ve sürdürme olaylarını izlemeyi etkinleştirir.  
  
     Bu düzeyde izleme bilgilerini, bkz: anlamı hakkında daha fazla bilgi için <xref:System.Diagnostics.SourceLevels>.  
  
9. **Tamam**'ı tıklatın.  
  
### <a name="to-disable-wpf-trace-information"></a>WPF izleme bilgilerini devre dışı bırakmak için  
  
1.  Üzerinde **Araçları** menüsünde **seçenekleri**.  
  
2.  İçinde **seçenekleri** iletişim kutusunda, sol taraftaki kutudan açın **hata ayıklama** düğümü.  
  
3.  Altında **hata ayıklama**, tıklayın **çıkış penceresine**.  
  
4.  Sağ taraftaki kutuya Ara **WPF izleme ayarlarını**.  
  
5.  Açık **WPF izleme ayarlarını** düğümü.  
  
6.  Altında **WPF izleme ayarlarını**, etkinleştirmek istediğiniz ayar kategorisine tıklayın (örneğin, **veri bağlama**).  
  
     Aşağı açılan liste denetimi ayarları sütunda yanında görünen **veri bağlama** veya tıkladığınız her kategorisi.  
  
7.  Aşağı açılan listeye tıklayıp **kapalı**.  
  
8.  **Tamam**'ı tıklatın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF'de Hata Ayıklama](../debugger/debugging-wpf.md)



