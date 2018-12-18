---
title: Gelişmiş Seçenekler, metin düzenleyici, C# | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Advanced
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
helpviewer_keywords:
- XML comments
- XML documentation, generating
- outlining options [C#]
- outlining options [J#]
- XML documentation, creating
ms.assetid: 947f9d9a-b0f3-408d-9866-d82895bcee31
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 51707a1df9c9f7144dc9a3af021262ca818f03b1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49850522"
---
# <a name="options-text-editor-c-advanced"></a>Seçenekler, Metin Düzenleyici, C#, Gelişmiş
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Düzenleyici biçimlendirme, kodu yeniden düzenlemeye ve XML belgeleri yorumları ayarlarını Visual C# değiştirmek için bu iletişim kutusunu kullanın. Bu iletişim kutusuna erişmek için tıklayın **seçenekleri** üzerinde **Araçları** menüsünde genişletin **metin düzenleyici** klasörünü genişletin **C#** ve 'yetıklayın **Gelişmiş**.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="outlining"></a>Anahat Oluşturma  
 Dosyalar açıldığında anahat moduna gir  
 Bu onay kutusu seçildiğinde, otomatik olarak daraltılabilir kod bloklarını oluşturan kod dosyası özetlenmektedir. Bir dosya açıldığında, ilk kez #regions blokları ve etkin olmayan kod blokları daraltır.  
  
## <a name="editor-help"></a>Düzenleyici Yardımı  
 Hataları düzenleyicide altı çizili  
 Kodda derleme hataları tanımlar. Bu seçenek belirlendiğinde özel anlamları renkte dalgalı alt çizgiler görünür:  
  
- Ayrıştırma hataları kırmızı renkte görüntülenir.  
  
- Derleme hatalarını, mavi.  
  
- Derleme Uyarıları yeşildir.  
  
- Geçersiz [Düzenle ve devam et](../../debugger/edit-and-continue.md) mor düzenlemeleri şunlardır.  
  
  Hata hakkında bilgi içeren bir araç ipucu görmek için altı çizili kod kesimi üzerine getirin.  
  
  Canlı anlamsal hataları göster  
  Bildirme ve bilinmeyen bir tür kullanarak veya bilinmeyen bir özelliğe başvurma bazı derleme hataları açık derlemesini olmadan tanımlar.  
  
  İmlecin altındaki sembole başvuruları Vurgula  
  İmleç bir sembol içinde konumlandırıldığında veya sembol tıkladığınızda, kod dosyasındaki o simgenin tüm örnekleri vurgulanır.  
  
## <a name="refactoring"></a>Yeniden Düzenle  
 Yeniden düzenleme sonuçlarını doğrulayın  
 Görüntüler **doğrulama sonuçları** iletişim kutusu içeren derleme hataları yeniden düzenleme kod çalıştığınızda veya yeniden düzenleme, neden kendi özgün bağlamasını farklı bir şey bağlamak bir kod başvurusu.  
  
 Derleyicinin ürettiği başvuruları olan üyelerin uyar  
 Derleyicinin ürettiği başvuru olarak aynı ada sahip bir üye yeniden denediğinizde bir uyarı iletişim kutusu görüntüler.  
  
## <a name="xml-documentation-comments"></a>XML Belgeleri Yorumları  
 / / / İçin XML belge açıklamaları oluşturma  
 Bu onay kutusu seçildiğinde, ekler \<Özet > başlangıç ve bitiş etiketleri otomatik olarak XML belge açıklamaları için / / / açıklama giriş yazdıktan sonra. XML belgeleri hakkında daha fazla bilgi için bkz. [XML belgeleri yorumları](http://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199).  
  
## <a name="implement-interface"></a>Arabirimi Uygulama  
 #Region üretilen kodla çevreleyen  
 Bir #region ekler \< *arabirim adı*> Uygulama arabirimi veya uygulama arabirimi açıkça kullanıldığında yöntemleri etrafında üyesi.  
  
## <a name="organize-usings"></a>Using'leri düzenleme  
 Using deyimlerini sıralarken önce 'System' yönergelerini Yerleştir  
 Bu onay kutusu seçildiğinde, `System` kullanma yönergesi görünmüyorsa önce diğer yönergeleri kullanarak. Daha fazla bilgi için [kullanımları sıralama](../../misc/sort-usings.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML belge açıklamaları](http://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199)   
 [Dile özgü Düzenleyici seçeneklerini ayarlama](../../ide/reference/setting-language-specific-editor-options.md)   
 [Visual C# IntelliSense](../../ide/visual-csharp-intellisense.md)



