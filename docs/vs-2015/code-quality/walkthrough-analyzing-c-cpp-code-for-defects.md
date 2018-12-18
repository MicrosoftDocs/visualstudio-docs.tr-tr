---
title: 'İzlenecek yol: Kod kusurları için C / C++ kodunu analiz etme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
ms.assetid: eaee55b8-85fe-47c7-a489-9be0c46ae8af
caps.latest.revision: 37
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6a5e98ee673d232065dd522b0b81a21760306979
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782316"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>İzlenecek yol: Kod Kusurları için C/C++ Kodunu Analiz Etme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu yönerge, C/C++ kodu için kod analizi aracı kullanarak olası kod kusurları için C/C++ kodunu analiz etme gösterir.  
  
 Bu kılavuzda, olası kod kusurları için C/C++ kod analiz etmek için kod analizini kullanarak işlemi adım adım.  
  
 Aşağıdaki adımları tamamlamanız:  
  
-   Yerel kod üzerinde kod analizini Çalıştır.  
  
-   Kod hatasını uyarıları çözümleyin.  
  
-   Hata olarak kabul uyarısı.  
  
-   Kod hata analizi iyileştirmek için kaynak kodu açıklama ekleyin.  
  
## <a name="prerequisites"></a>Önkoşullar  
  
-   [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] veya [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)].  
  
-   Bir kopyasını [gösterim örneği](../code-quality/demo-sample.md).  
  
-   C/C++ temel düzeyde bilinmesini.  
  
### <a name="to-run-code-defect-analysis-on-native-code"></a>Yerel kod üzerinde kod hata analizi çalıştırmak için  
  
1.  Tanıtım çözümde açık [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     Tanıtım çözümü şimdi doldurur **Çözüm Gezgini**.  
  
2.  Üzerinde **derleme** menüsünde tıklatın **çözümü yeniden derle**.  
  
     Çözüm herhangi bir hata veya uyarı derlenir.  
  
3.  İçinde **Çözüm Gezgini**, CodeDefects projeyi seçin.  
  
4.  Üzerinde **proje** menüsünü tıklatın **özellikleri**.  
  
     **CodeDefects özellik sayfaları** iletişim kutusu görüntülenir.  
  
5.  Tıklayın **Kod Analizi**.  
  
6.  Tıklayın **C/c++ derlemede kod çözümlemeyi etkinleştir** onay kutusu.  
  
7.  CodeDefects projeyi yeniden derleyin.  
  
     Kod çözümleme uyarıları görüntülenir **hata listesi**.  
  
### <a name="to-analyze-code-defect-warnings"></a>Kod hatasını uyarıları çözümlemek için  
  
1.  Üzerinde **görünümü** menüsünü tıklatın **hata listesi**.  
  
     Te seçtiğiniz Geliştirici profili bağlı olarak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], işaret edecek şekilde olabilir **diğer Windows** üzerinde **görünümü** menüsüne ve ardından **hata listesi**.  
  
2.  İçinde **hata listesi**, aşağıdaki uyarıyı çift tıklatın:  
  
     Uyarı C6230: anlamsal olarak farklı türleri arasında örtük atama: Boole bağlamında HRESULT kullanma.  
  
     Kod Düzenleyicisi uyarıya yol açan işlev satır görüntüler `bool``ProcessDomain()`. Bu uyarı, bir HRESULT bir 'If' deyimi bir Boolean sonucu beklenen yeri kullanılmakta olduğunu gösterir.  
  
3.  Bu uyarı, SUCCEEDED makrosu kullanarak düzeltin. Kodunuzu aşağıdaki koda benzemelidir:  
  
    ```  
    if (SUCCEEDED (ReadUserAccount()) )  
    ```  
  
4.  İçinde **hata listesi**, aşağıdaki uyarıyı çift tıklatın:  
  
     Uyarı C6282: Yanlış işleç: test bağlamında sabit atama. Hedeflenen == oldu?  
  
5.  Bu uyarı, eşitlik için test ederek düzeltin. Kodunuzu aşağıdaki koda benzemelidir:  
  
    ```  
    if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
    ```  
  
### <a name="to-treat-warning-as-an-error"></a>Uyarı hata olarak değerlendirilecek  
  
1.  Bug.cpp dosyasına aşağıdakileri ekleyin `#pragma` C6001 uyarı hata olarak değerlendirilecek dosyanın başına deyimi:  
  
    ```  
    #pragma warning (error: 6001)  
    ```  
  
2.  CodeDefects projeyi yeniden derleyin.  
  
     İçinde **hata listesi**, C6001 hata olarak görünür.  
  
3.  Kalan iki C6001 hataları düzeltin **hata listesi** başlatma tarafından `i` ve `j` 0.  
  
4.  CodeDefects projeyi yeniden derleyin.  
  
     Projeyi herhangi bir uyarı veya hata derler.  
  
### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>Kaynak kod ek açıklama uyarılara annotation.c düzeltmek için  
  
1.  Çözüm Gezgini içinde ek açıklamalar projeyi seçin.  
  
2.  Üzerinde **proje** menüsünü tıklatın **özellikleri**.  
  
     **Ek açıklamaları özellik sayfaları** iletişim kutusu görüntülenir.  
  
3.  Tıklayın **Kod Analizi**.  
  
4.  Seçin **C/c++ derlemede kod çözümlemeyi etkinleştir** onay kutusu.  
  
5.  Ek açıklamalar projeyi yeniden derleyin.  
  
6.  İçinde **hata listesi**, aşağıdaki uyarıyı çift tıklatın:  
  
     Uyarı C6011: NULL işaretçi 'newNode' başvurusunun kaldırılması.  
  
     Bu uyarı, dönüş değeri denetleyin çağıran tarafından hatası gösterir. Bu durumda, bir çağrıda **AllocateNode** NULL bir değer döndürebilir (işlev bildirimi için AllocateNode annotations.h üstbilgi dosyasını bakın).  
  
7.  Annotations.cpp dosyasını açın.  
  
8.  Bu uyarıyı düzeltmek için dönüş değerini test etmek için bir 'if' deyimini kullanın. Kodunuzu aşağıdaki koda benzemelidir:  
  
     `if (NULL != newNode)`  
  
     `{`  
  
     `newNode->data = value;`  
  
     `newNode->next = 0;`  
  
     `node->next = newNode;`  
  
     `}`  
  
9. Ek açıklamalar projeyi yeniden derleyin.  
  
     Projeyi herhangi bir uyarı veya hata derler.  
  
### <a name="to-use-source-code-annotation"></a>Kaynak kod ek açıklamaları kullanmak için  
  
1.  Ek açıklama biçimsel parametreler ve dönüş değeri işlevin `AddTail` öncesi ve sonrası koşulları Bu örnekte gösterilen şekilde kullanarak:  
  
     `[returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail`  
  
     `(`  
  
     `[SA_Pre(Null=SA_Maybe)] LinkedList* node,`  
  
     `int value`  
  
     `)`  
  
2.  Ek açıklamalar projeyi yeniden derleyin.  
  
3.  İçinde **hata listesi**, aşağıdaki uyarıyı çift tıklatın:  
  
     Uyarı C6011: NULL işaretçi 'düğümü' başvurusunu kaldırma.  
  
     Bu uyarı işleve geçirilen düğüm null olabileceğini gösterir ve burada uyarı tetiklendi satır numarasını gösterir.  
  
4.  Bu uyarıyı düzeltmek için dönüş değerini test etmek için bir 'if' deyimini kullanın. Kodunuzu aşağıdaki koda benzemelidir:  
  
    ```  
    . . .  
    LinkedList *newNode = NULL;   
    if (NULL == node)  
    {  
         return NULL;  
        . . .  
    }  
    ```  
  
5.  Ek açıklamalar projeyi yeniden derleyin.  
  
     Projeyi herhangi bir uyarı veya hata derler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: Kod Kusurları için Yönetilen Kodu Analiz Etme](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)



