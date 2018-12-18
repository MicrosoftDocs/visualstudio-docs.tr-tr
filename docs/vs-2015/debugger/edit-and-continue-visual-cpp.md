---
title: Düzenle ve devam et (Visual C++) | Microsoft Docs
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
- Edit and Continue [C++]
- debugging [C++], Edit and Continue
- C/C++, Edit and Continue
ms.assetid: 1815251e-a877-433e-9e5e-69bd9ba254c7
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e1dc97af70f575632629a13ea67e905f2ad0815
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51748358"
---
# <a name="edit-and-continue-visual-c"></a>Düzenle ve Devam Et (Visual C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual C++ projelerinde, Düzenle ve devam et kullanabilirsiniz. Bkz: [desteklenen kod değişiklikleri (C++)](../debugger/supported-code-changes-cpp.md) Düzenle ve devam et sınırlamaları hakkında bilgi için.  
  
 Artık desteklediğinden Visual Studio 2015 güncelleştirme 1'de başlayarak, artık Düzenle ve devam et DirectX uygulamaları, Windows Store C++ uygulamaları ile kullanabileceğiniz **/zi** derleyici anahtarıyla **/bigobj** geçin. Düzenle ve devam et ile derlenmiş ikili dosyaları ile kullanabilirsiniz **/FASTLINK** geçin.  
  
 Yeni, iptal edilebilir bekleme iletişim kutusu diğer güncelleştirme 1 geliştirmeleri içerir ve bir dosya desteklemediği zaman bildirim Düzenle ve devam et. Güncelleştirme 1 iyileştirmeleri hakkında daha fazla bilgi için bkz. [C++ Düzenle ve devam et Visual Studio 2015 güncelleştirme 1 için geliştirmeler](http://blogs.msdn.com/b/vcblog/archive/2015/11/30/improvements-for-c-edit-and-continue-in-visual-studio-2015-update-1.aspx).  
  
 [/Zo (geliştirmek için iyileştirilmiş hata ayıklama)](http://msdn.microsoft.com/library/eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f) Visual Studio 2013 güncelleştirme 3'te kullanılmaya başlanan derleyici seçeneği olmadan ikili dosyaları derlenmiş için bu ek bilgiler için .pdb (simge) dosyaları ekler [/Od (devre dışı bırak (Hata Ayıkla)) ](http://msdn.microsoft.com/library/aafb762y.aspx) seçeneği.  
  
 **/ZO** devre dışı bırakır, Düzenle ve devam et. Bkz: [nasıl yapılır: iyileştirilmiş kodda hata ayıklama](../debugger/how-to-debug-optimized-code.md).  
  
##  <a name="BKMK_Enable_or_disable_automatic_invocation_of_Edit_and_Continue"></a> Düzenle ve Devam Et'i devre dışı bırakmak veya etkinleştirmek  
 Geçerli hata ayıklama oturumu sırasında uygulanan istemediğiniz kod düzenlemeler yapmasını durumunda Düzenle ve devam et otomatik çağrılmasını devre dışı bırakmak isteyebilirsiniz. Ayrıca otomatik Düzenle ve devam et yeniden etkinleştirebilirsiniz.  
  
1. Üzerinde **Araçları** menüsünde seçin **seçenekleri**.  
  
2. İçinde **seçenekleri** iletişim kutusunda **hata ayıklama / genel**.  
  
3. İçinde **Düzenle ve devam et** grubu seçin veya temizleyin **etkinleştirme yerel Düzenle ve devam et** onay kutusu.  
  
   Bu ayarı değiştirmeden üzerinde çalışan tüm projeleri etkiler. Bu ayarı değiştirdikten sonra uygulamanızı yeniden gerekmez. Hatta ayıklarken ayarı değiştirebilirsiniz. Ayarlarsanız uygulamanızı bir derleme görevleri dosyası veya komut satırından derleme, ancak Visual Studio ortamında Hata Ayıkla, Düzenle ve devam et kullanmaya devam edebilirsiniz **/zi** seçeneği.  
  
##  <a name="BKMK_How_to_apply_code_changes_explicitly"></a> Kod değişikliklerini açıkça uygulama  
 Visual C++'da, Düzenle ve devam et, iki yolla kod değişiklikleri uygulayabilirsiniz. Kod değişiklikleri uygulanabilir örtük olarak, bir yürütme komutu seçtiğinizde veya açıkça kullanarak **kod değişikliklerini uygulama** komutu.  
  
 Kod değişikliklerini açıkça uygulama, programınız kesme modunda – hiçbir yürütülmenin kalır.  
  
-   Kod değişikliklerini açıkça uygulamak için üzerinde **hata ayıklama** menüsünde seçin **kod değişikliklerini uygulama**.  
  
##  <a name="BKMK_How_to_stop_code_changes"></a> Kod değişikliklerini durdurma  
 Düzenle ve devam ederken kod değişikliklerini uygulama sürecinde, işlemi durdurabilirsiniz.  
  
 Kod değişiklikleri uygulanırken durdurmak için:  
  
- Üzerinde **hata ayıklama** menüsünde seçin **kod değişikliklerini uygulamayı Durdur'u**.  
  
  Bu menü öğesi, yalnızca kod değişiklikleri uygulanıyor bile görülebilir.  
  
  Bu seçeneği seçerseniz, hiçbir kod değişikliği kabul edilir.  
  
##  <a name="BKMK_How_to_reset_the_point_of_execution"></a> Yürütme noktası sıfırlama  
 Bazı kod değişiklikleri, Düzenle ve devam et değişiklikleri uygulandığında, yeni bir konuma taşımak için yürütme noktasını neden olabilir. Düzenle ve devam et yerleştirir yürütme noktası olarak doğru bir şekilde, ancak sonuçları her durumda doğru olmayabilir.  
  
 Visual C++'da, bir iletişim kutusu yürütme noktası değiştiğinde bildirir. Hata ayıklama devam etmeden önce konumun doğru olduğunu doğrulamanız gerekir. Doğru değilse, **sonraki deyimi Ayarla** komutu. Daha fazla bilgi için [yürütülecek sonraki deyimi ayarlamak](http://msdn.microsoft.com/library/y740d9d3.aspx#BKMK_Set_the_next_statement_to_execute).  
  
##  <a name="BKMK_How_to_work_with_stale_code"></a> Eski kod ile çalışma  
 Bazı durumlarda, Düzenle ve devam et kod değişikliklerini yürütülebilir dosyaya hemen uygulanamaz, ancak hata ayıklama devam ederseniz daha sonra kod değişikliklerini uygulamak mümkün olabilir. Bu geçerli işlevi çağıran bir işlev düzenlerseniz veya çağrı yığınında bir işleve 64 bayttan daha fazla yeni değişkenleri eklerseniz gerçekleşir  
  
 Bu gibi durumlarda, hata ayıklayıcı, değişikliklerin uygulanması kadar özgün kod yürütülmeye devam eder. Eski kod bir başlığa sahip ayrı bir kaynak penceresinde bir geçici kaynak dosya penceresi gibi görünür `enc25.tmp`. Düzenlenen kaynak özgün kaynak penceresinde görünmeye devam eder. Eski kod düzenlemeye çalışırsanız, bir uyarı iletisi görüntülenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Desteklenen Kod Değişiklikleri (C++)](../debugger/supported-code-changes-cpp.md)



