---
title: Visual Basic çözümlemek ve C# kod kalitesi statik kod analizini kullanarak Store uygulamalarında
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb.express
ms.assetid: cab553fc-19a9-4cbf-858e-8200258ffe50
caps.latest.revision: 16
author: erickson-doug
ms.author: gewarren
manager: douge
ms.openlocfilehash: a3a3d753f9e2dd3b046159d191149b7af062fe16
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063221"
---
# <a name="analyze-visual-basic-and-c-code-quality-in-store-apps-using-visual-studio-static-code-analysis"></a>Visual Studio statik kod analizini kullanarak Store uygulamalarında Visual Basic ve C# kod kalitesini analiz etme

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows ve Windows Phone için geçerlidir] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 Visual Studio Express'te kod analizi aracı, kodunuz için bir dizi yaygın hataları ve programlama iyi yöntem ihlallerini inceler. Geçerli olan, ancak yine de siz veya kodunuzu kullanan diğer kişilerin sorunlarına neden olabilir, belirli bir kod desenleri için kod analizi aracı arar çünkü kod çözümleme uyarıları derleyici hataları ve Uyarıları farklılık gösterir. Kod Analizi, kodunuzda test sürecinde bulmak zor olan hataları da bulabilirsiniz. Kod çözümleme aracı, geliştirme sürecinde düzenli aralıklarla çalışan tamamlanmış uygulamanızın kalitesini artırabilirsiniz.

> [!NOTE]
>  Visual Studio Ultimate, Visual Studio Premium ve Visual Studio Professional içinde kod analizi tam işlevselliğini kullanabilirsiniz. Bkz: [kod çözümleme araçları ile uygulama kalitesini analiz etme](http://msdn.microsoft.com/library/dd264897.aspx) MSDN Kitaplığı'nda.

## <a name="in-this-topic"></a>Bu konuda
 Hakkında bilgi edinebilirsiniz:

 [Kod Analizi çalıştırma](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Run)

 [Çözümleme ve kod çözümleme uyarıları çözümleme](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Analyze)

 [Kod Analizi uyarılarını gizleme](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Suppress)

 [Arama ve Kod Analizi sonuçlarını filtreleme](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Search)

 [Visual Basic ve C# Kod Analizi uyarılarının](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Warnings)

##  <a name="BKMK_Run"></a> Kod Analizi çalıştırma
 Visual Studio çözümünüzü Kod Analizi çalıştırmak için:

- Üzerinde **derleme** menüsünde seçin **çözüm üzerinde kod analizini Çalıştır**.

  Kod analizinin her zaman otomatik olarak çalıştırmak için bir proje oluşturun:

1. Çözüm Gezgini'nde proje adına sağ tıklayın ve ardından **özellikleri**.

2. Proje özellik sayfası seçin **Kod Analizi** seçip **etkinleştir (CODEANALYSIS sabitini tanımlar) derlemede kod analizini**.

   Çözüm derlenir ve Kod Analizi çalıştırır. Sonuçları Kod Analizi penceresinde görünür.

   ![Kod Analizi penceresi](../test/media/ca-managed-collapsed.png "CA_Managed_Collapsed")

##  <a name="BKMK_Analyze"></a> Çözümleme ve kod çözümleme uyarıları çözümleme
 Belirli bir uyarıyı çözümlemek için Kod Analizi penceresi uyarıda başlığını tıklatın. Sorun hakkında ayrıntılı bilgileri görüntülemek için uyarı genişletir.

 ![Kod Analizi uyarısı Genişletilmiş](../test/media/ca-managed-callouts.png "CA_Managed_Callouts")

 Bir uyarı genişlettiğinizde, Visual Studio Kod Düzenleyicisi'nde uyarıya yol açan kod satırının vurgulanır.

 ![Kod Analizi metni vurgulama](../test/media/ca-managed-sourceline.png "CA_Managed_SourceLine")

 Sorunu anladıktan sonra kodunuzu çözebilirsiniz. Ardından uyarı artık Kod Analizi penceresi açılır ve düzeltmenizi henüz yeni uyarılar ortaya emin olmak için kod analizini yeniden çalıştırın.

> [!TIP]
>  Kod analizinden kaynaklanan Kod Analizi penceresi yeniden çalıştırabilirsiniz. Tıklayın **Çözümle** düğmesine tıklayın ve analiz kapsamını seçin. Seçilen proje veya çözümün tamamını üzerinde analiz yeniden çalıştırabilirsiniz.

##  <a name="BKMK_Suppress"></a> Kod Analizi uyarılarını gizleme
 Kod Analizi uyarısı düzeltmemeyi ne zaman karar verebilirsiniz zamanlar vardır. Uyarı çözümleme sorunu kodunuzun tüm gerçek uygulamasında ortaya çıkacağını olasılık ile ilgili çok fazla değiştirilemeyen gerektirir karar verebilirsiniz. Veya uyarıda kullanılan analiz belirli bir içerik için uygun olduğunu düşündüğünüz. Artık Kod Analizi penceresinde görünecekleri bireysel uyarıları gösterilmemesini sağlayabilirsiniz.

 Bir uyarıyı bastırmak için:

1. Ayrıntılı bilgi görüntülenmiyorsa genişletmek için uyarı başlığını tıklatın.

2. Seçin **eylemleri** Uyarı alt kısmındaki bağlantı.

3. İşaret **ileti Gizle** seçin **içinde kaynak** veya **gizleme dosyası içinde**.

   - **Kaynakta** ekler bir `SuppressMessage` uyarıyı oluşturan yöntem yukarıda kaynak dosyasındaki özniteliği. Bu gizleme daha bulunabilir hale getirir.

   - **Gizleme dosyasında** ekler bir `SuppressMessage` özniteliğini **GlobalSuppressions.cs** proje dosyası. Bu yönetim gizlemelerinin kolaylaştırabilir. Unutmayın `SuppressMessage` eklenen özniteliği **GlobalSuppression.cs** da hedefler, uyarıyı oluşturan yöntem. Uyarı engellemez genel.

     Kararınız uyarı gizleme dosyasında veya kaynak dosyadaki engellenip engellenmeyeceğini belirtir, kodlama stili ve gereksinimlerine bağlıdır.

##  <a name="BKMK_Search"></a> Arama ve Kod Analizi sonuçlarını filtreleme
 Uzun listesi uyarı iletilerini arayabilir ve çoklu proje çözümlerinde uyarıları filtreleyebilirsiniz.

 ![Aramanıza ve filtrelemenize Kod Analizi penceresi](../test/media/ca-searchfilter.png "CA_SearchFilter")

 İçinde [!INCLUDE[vs_dev11_expwin_long](../includes/vs-dev11-expwin-long-md.md)], tüm kod analizi uyarıları, uyarı önem derecesi vardır.

##  <a name="BKMK_Warnings"></a> Visual Basic ve C# Kod Analizi uyarılarının
 Kod Analizi aşağıdaki uyarılar oluşturur:

 [CA1001: Atılabilir alanlara sahip olan türler atılabilir olmalıdır](http://msdn.microsoft.com/library/ms182172.aspx)

 [CA1821: Boş sonlandırıcıları kaldırın](http://msdn.microsoft.com/library/bb264476.aspx)

 [CA2213: Atılabilen alanlar atılmalıdır](http://msdn.microsoft.com/library/ms182328.aspx)

 [CA2229: Serileştirme oluşturucularını uygulayın](http://msdn.microsoft.com/library/ms182343.aspx)

 [CA2231: ValueType.Equals değerini geçersiz kılmada eşittir işlecini aşırı yükle](http://msdn.microsoft.com/library/ms182359.aspx)
