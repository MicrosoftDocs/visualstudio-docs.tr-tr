---
title: Düzenle ve devam et (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 05/31/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C++]
- debugging [C++], Edit and Continue
- C/C++, Edit and Continue
ms.assetid: 1815251e-a877-433e-9e5e-69bd9ba254c7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 7e468f75abbadbe46ea973a5c04d2e286fcfaca5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49867708"
---
# <a name="edit-and-continue-visual-c"></a>Düzenle ve Devam Et (Visual C++)
Visual C++ projelerinde, Düzenle ve devam et kullanabilirsiniz. Bkz: [desteklenen kod değişiklikleri (C++)](../debugger/supported-code-changes-cpp.md) Düzenle ve devam et sınırlamaları hakkında bilgi için.
  
Visual Studio 2015 güncelleştirme 3'ü iyileştirmeleri hakkında daha fazla bilgi için bkz. [C++ Düzenle ve devam et Visual Studio 2015 güncelleştirme 3'te](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/).  
  
 [/Zo (geliştirmek için iyileştirilmiş hata ayıklama)](/cpp/build/reference/zo-enhance-optimized-debugging) Visual Studio 2013 güncelleştirme 3'te kullanılmaya başlanan derleyici seçeneği olmadan ikili dosyaları derlenmiş için bu ek bilgiler için .pdb (simge) dosyaları ekler [/Od (devre dışı bırak (Hata Ayıkla)) ](https://msdn.microsoft.com/library/aafb762y.aspx) seçeneği.  
  
 **/ZO** devre dışı bırakır, Düzenle ve devam et. Bkz: [nasıl yapılır: iyileştirilmiş kodda hata ayıklama](../debugger/how-to-debug-optimized-code.md).  
  
##  <a name="BKMK_Enable_or_disable_automatic_invocation_of_Edit_and_Continue"></a> Düzenle ve Devam Et'i devre dışı bırakmak veya etkinleştirmek  
 Geçerli hata ayıklama oturumu sırasında uygulanan istemediğiniz kod düzenlemeler yapmasını durumunda Düzenle ve devam et otomatik çağrılmasını devre dışı bırakmak isteyebilirsiniz. Ayrıca otomatik Düzenle ve devam et yeniden etkinleştirebilirsiniz.

> [!IMPORTANT]
> Gerekli yapılandırma ayarlarını ve diğer özellik uyumluluğu hakkında bilgi için [C++ Düzenle ve devam et Visual Studio 2015 güncelleştirme 3'te] konusuna bakın (https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/.
  
1. Hata ayıklama oturumunda varsa, hata ayıklamayı Durdur (**Shift + F5 tuşlarına basarak**).

2. Üzerinde **Araçları** menüsünde seçin **seçenekleri**.
  
3. İçinde **seçenekleri** iletişim kutusunda **hata ayıklama > Genel**.

4. Etkinleştirmek için seçin **etkinleştirme Düzenle ve devam et**. Devre dışı bırakmak için onay kutusunu temizleyin.
  
5. İçinde **Düzenle ve devam et** grubu seçin veya temizleyin **etkinleştirme yerel Düzenle ve devam et** onay kutusu.  
  
   Bu ayarı değiştirmeden üzerinde çalışan tüm projeleri etkiler. Bu ayarı değiştirdikten sonra uygulamanızı yeniden gerekmez. Ayarlarsanız uygulamanızı bir derleme görevleri dosyası veya komut satırından derleme, ancak Visual Studio ortamında Hata Ayıkla, Düzenle ve devam et kullanmaya devam edebilirsiniz **/zi** seçeneği.  
  
##  <a name="BKMK_How_to_apply_code_changes_explicitly"></a> Kod değişikliklerini açıkça uygulama  
 Visual C++'da, Düzenle ve devam et, iki yolla kod değişiklikleri uygulayabilirsiniz. Kod değişiklikleri uygulanabilir örtük olarak, bir yürütme komutu seçtiğinizde veya açıkça kullanarak **kod değişikliklerini uygulama** komutu.  
  
 Kod değişikliklerini açıkça uygulama, programınız kesme modunda - hiçbir yürütülmenin kalır.  
  
-   Kod değişikliklerini açıkça uygulamak için üzerinde **hata ayıklama** menüsünde seçin **kod değişikliklerini uygulama**.  
  
##  <a name="BKMK_How_to_stop_code_changes"></a> Kod değişikliklerini durdurma  
 Düzenle ve devam ederken kod değişikliklerini uygulama sürecinde, işlemi durdurabilirsiniz.  
  
 Kod değişiklikleri uygulanırken durdurmak için:  
  
- Üzerinde **hata ayıklama** menüsünde seçin **kod değişikliklerini uygulamayı Durdur'u**.  
  
  Bu menü öğesi, yalnızca kod değişiklikleri uygulanıyor bile görülebilir.  
  
  Bu seçeneği seçerseniz, hiçbir kod değişikliği kabul edilir.  
  
##  <a name="BKMK_How_to_reset_the_point_of_execution"></a> Yürütme noktası sıfırlama  
 Bazı kod değişiklikleri, Düzenle ve devam et değişiklikleri uygulandığında, yeni bir konuma taşımak için yürütme noktasını neden olabilir. Düzenle ve devam et yerleştirir yürütme noktası olarak doğru bir şekilde, ancak sonuçları her durumda doğru olmayabilir.  
  
 Visual C++'da, bir iletişim kutusu yürütme noktası değiştiğinde bildirir. Hata ayıklama devam etmeden önce konumun doğru olduğunu doğrulamanız gerekir. Doğru değilse, **sonraki deyimi Ayarla** komutu. Daha fazla bilgi için [yürütülecek sonraki deyimi ayarlamak](https://msdn.microsoft.com/library/y740d9d3.aspx#BKMK_Set_the_next_statement_to_execute).  
  
##  <a name="BKMK_How_to_work_with_stale_code"></a> Eski kod ile çalışma  
 Bazı durumlarda, Düzenle ve devam et kod değişikliklerini yürütülebilir dosyaya hemen uygulanamaz, ancak hata ayıklama devam ederseniz daha sonra kod değişikliklerini uygulamak mümkün olabilir. Bu geçerli işlevi çağıran bir işlev düzenlerseniz veya çağrı yığınında bir işleve 64 bayttan daha fazla yeni değişkenleri eklerseniz gerçekleşir  
  
 Bu gibi durumlarda, hata ayıklayıcı, değişikliklerin uygulanması kadar özgün kod yürütülmeye devam eder. Eski kod bir başlığa sahip ayrı bir kaynak penceresinde bir geçici kaynak dosya penceresi gibi görünür `enc25.tmp`. Düzenlenen kaynak özgün kaynak penceresinde görünmeye devam eder. Eski kod düzenlemeye çalışırsanız, bir uyarı iletisi görüntülenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Desteklenen Kod Değişiklikleri (C++)](../debugger/supported-code-changes-cpp.md)