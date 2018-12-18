---
title: 'İzlenecek yol: Kod Kusurları için C/C++ Kodunu Analiz Etme'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 6e15c6acc241e36e7cadc1d6f043549f1f5e46c7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31922039"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>İzlenecek yol: Kod Kusurları için C/C++ Kodunu Analiz Etme

Bu kılavuz C/C++ kodu için kod analizi aracı kullanarak olası kod kusurları için C/C++ kodunu analiz etme gösterir.

- Kod çözümleme yerel kodu çalıştırın.
- Kod hatası uyarıları çözümleyin.
- Hata olarak kabul uyarı.
- Kod hatasını çözümleme geliştirmek için kaynak kodu açıklama.

## <a name="prerequisites"></a>Önkoşullar

- Bir kopyasını [gösterim örneği](../code-quality/demo-sample.md).
- C/C++ ilgili temel bilgilere.

### <a name="to-run-code-defect-analysis-on-native-code"></a>Kod hatasını çözümleme yerel kodu çalıştırmak için

1. Tanıtım çözümde açmak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

     Tanıtım çözüm şimdi doldurur **Çözüm Gezgini**.

2. Üzerinde **yapı** menüsünde tıklatın **çözümü yeniden derle**.

     Çözüm, herhangi bir hata veya uyarı oluşturur.

3. İçinde **Çözüm Gezgini**, CodeDefects projesini seçin.

4. Üzerinde **proje** menüsünde tıklatın **özellikleri**.

     **CodeDefects özellik sayfaları** iletişim kutusu görüntülenir.

5. Tıklatın **kod çözümleme**.

6. Tıklatın **derlemede C/C++ için Kod Analizi etkinleştir** onay kutusu.

7. CodeDefects projeyi yeniden oluşturun.

     Kod çözümleme uyarıları görüntülenir **hata listesi**.

### <a name="to-analyze-code-defect-warnings"></a>Kod hatası uyarıları çözümlemek için

1. Üzerinde **Görünüm** menüsünde tıklatın **hata listesi**.

     İçinde seçtiğiniz Geliştirici profili bağlı olarak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], işaret gerekebilir **diğer pencereler** üzerinde **Görünüm** menüsüne ve ardından **hata listesi**.

2. İçinde **hata listesi**, aşağıdaki uyarıyı çift tıklatın:

     C6230 Uyarı: anlamsal olarak farklı türleri arasında örtük cast: Boolean bağlamda HRESULT kullanarak.

     Kod Düzenleyicisi uyarı işlevinde neden satırı görüntüler `bool``ProcessDomain()`. Bu uyarı bir HRESULT bir 'If' deyimi bir Boolean sonucu beklenirken kullanılmakta olduğunu gösterir.

3. Bu uyarı, başarılı makrosu kullanarak düzeltin. Kodunuzu aşağıdaki kodu benzemelidir:

   ```cpp
   if (SUCCEEDED (ReadUserAccount()) )
   ```

4. İçinde **hata listesi**, aşağıdaki uyarıyı çift tıklatın:

     C6282 Uyarı: yanlış işleci: test bağlamda sabiti atama. İstenen == edildi?

5. Bu uyarı eşitlik için test ederek düzeltin. Kodunuzu aşağıdaki kodu benzer görünmelidir:

   ```cpp
   if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))
   ```

### <a name="to-treat-warning-as-an-error"></a>Uyarı hata olarak işlemek için

1. Aşağıdaki Bug.cpp dosyasına ekleyin `#pragma` C6001 uyarıyı hata olarak işlemek için dosyanın başına deyimi:

   ```cpp
   #pragma warning (error: 6001)
   ```

2. CodeDefects projeyi yeniden oluşturun.

     İçinde **hata listesi**, C6001 hata olarak görünür.

3. Kalan iki C6001 hataları düzeltin **hata listesi** başlatma tarafından `i` ve `j` 0.

4. CodeDefects projeyi yeniden oluşturun.

     Proje uyarı veya hata oluşturulur.

### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>Kaynak kodu ek açıklama uyarılarla annotation.c düzeltmek için

1. Çözüm Gezgini'nde ek açıklamaları projesini seçin.

2. Üzerinde **proje** menüsünde tıklatın **özellikleri**.

     **Ek açıklamaları özellik sayfaları** iletişim kutusu görüntülenir.

3. Tıklatın **kod çözümleme**.

4. Seçin **derlemede C/C++ için Kod Analizi etkinleştir** onay kutusu.

5. Ek açıklamalar projeyi yeniden oluşturun.

6. İçinde **hata listesi**, aşağıdaki uyarıyı çift tıklatın:

     C6011 Uyarı: NULL işaretçi 'newNode' başvurusunun kaldırılmasının.

     Bu uyarı dönüş değerini denetlemek için çağıran tarafından başarısız olduğunu gösterir. Bu durumda, çağrı içinde **AllocateNode** bir NULL değer döndürebilir (işlev bildirimi AllocateNode için annotations.h üstbilgi dosyası bakın).

7. Annotations.cpp dosyasını açın.

8. Bu uyarı düzeltmek için dönüş değerini sınamak için bir 'If' deyimi kullanın. Kodunuzu aşağıdaki kodu benzemelidir:

   ```cpp
   if (NULL != newNode)
   {
   newNode->data = value;
   newNode->next = 0;
   node->next = newNode;
   }
   ```

9. Ek açıklamalar projeyi yeniden oluşturun.

     Proje uyarı veya hata oluşturulur.

### <a name="to-use-source-code-annotation"></a>Kaynak kodu ek açıklama kullanmak için

1. Biçimsel parametresi açıklama ve dönüş değeri işlevinin `AddTail` Bu örnekte gösterildiği gibi öncesi ve sonrası koşullarını kullanarak:

   ```cpp
   [returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail
   (
   [SA_Pre(Null=SA_Maybe)] LinkedList* node,
   int value
   )
   ```

2. Ek açıklamalar projeyi yeniden derleyin.

3. İçinde **hata listesi**, aşağıdaki uyarıyı çift tıklatın:

     C6011 Uyarı: bilgileri başvuru kaldırma boş işaretçi 'düğümü'.

     Bu uyarı işlevdeki geçirilen düğüm null olabileceğini gösterir ve uyarı nerede gerçekleştiği satır numarasını gösterir.

4. Bu uyarı düzeltmek için dönüş değerini sınamak için bir 'If' deyimi kullanın. Kodunuzu aşağıdaki kodu benzemelidir:

   ```cpp
   . . .
   LinkedList *newNode = NULL;
   if (NULL == node)
   {
        return NULL;
        . . .
   }
   ```

5. Ek açıklamalar projeyi yeniden derleyin.

     Proje uyarı veya hata oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.

[İzlenecek yol: Kod kusurları için yönetilen kod çözümleme](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)
[C/C++ için kod çözümleme](../code-quality/code-analysis-for-c-cpp-overview.md)