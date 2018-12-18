---
title: 'Nasıl yapılır: kodu görüntüleme ve düzenleme (Alt + F12) Özet tanımı kullanarak | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45f3dd20-902a-4047-8cca-9f18216123f4
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cc99602fe1ca2003995594f75736d581fa37e0d0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49254481"
---
# <a name="how-to-view-and-edit-code-by-using-peek-definition-altf12"></a>Nasıl yapılır: Özet Tanımı'nı Kullanarak Kodu Görüntüleme ve Düzenleme (Alt+F12)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kullanabileceğiniz **Özet tanım** görüntülemek ve kod yazdığınız uzaklaşmadan kod tanımlarını düzenlemek için komutu. **Özet tanım** ve **tanıma** aynı bilgileri gösterir ancak **Özet tanım** bir açılır pencerede gösterir ve **tanıma** gösterir ayrı bir kod penceresinde kodu. **Tanıma Git** tanım kodu penceresine geçilmesine, bağlamınızın (yani, etkin kod penceresi, geçerli satır ve imleç konumu) neden olur. Kullanarak **Özet tanım**, görüntüleyebilir ve tanımını düzenleyin ve orijinal kod dosyasında yerinizi tutarken tanım dosyası içinde gezinebilirsiniz.  
  
 Kullanabileceğiniz **Özet tanım** C#, Visual Basic ve C++ koduna sahip. Visual Basic'te **Özet tanım** bir bağlantısı gösterir **Nesne Tarayıcısı** tanım meta verileri (yerleşik olarak bulunan Örneğin, .NET Framework türleri) olmayan simgeler için.  
  
> [!IMPORTANT]
>  Visual Studio 2013'ün herhangi bir Express sürümünde bu komutu kullanamazsınız.  
  
## <a name="working-with-peek-definition"></a>Özet Tanım ile Çalışma  
  
#### <a name="to-open-a-peek-definition-window"></a>Bir Özet Tanım penceresi açmak için  
  
1.  Bulabilirsiniz **Özet tanım** keşfetmek istediğiniz yöntem için kısayol menüsünü açarak. (Klavye: Alt+F12)  
  
     Bu resimde **Özet tanım** adlı bir yöntem için pencere `Print()`:  
  
     ![Pencere Özet](../ide/media/peekwindow.png "PeekWindow")  
  
     Tanım penceresinin altında görünür `printer.Print(“Hello World!”)` özgün dosyadaki bir satır. Pencerede, özgün dosyanızdaki kodlardan hiçbiri gizlenmez. Gelen satırlar `printer.Print(“Hello World!”)` çağrı tanım penceresinin altında görünür.  
  
2.  İmleci, kod tanımı penceresinde farklı konumlara taşıyabilirsiniz. Özgün kod penceresinde tanım penceresinin altında veya üstünde gezinmeye devam edebilirsiniz.  
  
3.  Dizeyi tanım penceresinden kopyalayıp özgün koda yapıştırabilirsiniz. Dizeyi tanım penceresinden sürükleyip özgün koda da bırakabilirsiniz (tanım penceresinden silinmeden).  
  
4.  Esc tuşunu seçerek tanım penceresini kapatabilirsiniz veya **kapatmak** tanım penceresi sekmesindeki düğmesi.  
  
#### <a name="to-open-a-peek-definition-window-from-within-a-peek-definition-window"></a>Bir Özet Tanım penceresinin içinden Özet Tanım penceresi açmak için  
  
-   Zaten bir **Özet tanım** pencereniz açıksa çağırabilirsiniz **Özet tanım** Bu penceredeki kod üzerinde yeniden. Başka bir tanım penceresi açılır. Tanım penceresi sekmesinin yanında, tanım pencereleri arasında gezinmek için kullanabileceğiniz bir dizi içerik haritası noktası görünür. Her bir noktadaki araç ipucu, noktanın temsil ettiği tanım dosyasının dosya adını ve yolunu gösterir.  
  
     ![Bir Özet penceresi içinde Özet penceresinde](../ide/media/peekwithinpeek.png "PeekWithinPeek")  
  
#### <a name="to-use-peek-definition-with-multiple-results"></a>Özet Tanım komutunu birden çok sonuçla kullanmak için  
  
-   Kullanırsanız **Özet tanım** birden fazla tanıma (örneğin, parçalı sınıflar) sahip kod üzerinde kod tanımı görünümünün sağında bir sonuç listesi görünür. Listede istediğiniz sonucu seçerek tanımını görüntüleyebilirsiniz.  
  
     ![Birden çok sonuç gözlem penceresinden](../ide/media/peekmultiple.png "PeekMultiple")  
  
#### <a name="to-edit-inside-the-peek-definition-window"></a>Özet Tanım penceresinin içinde düzenlemek için  
  
-   İçinde düzenleme yapmaya başladığınızda bir **Özet tanım** penceresinde otomatik olarak değişiklik yaptığınız dosya olarak Kod Düzenleyicisi içinde ayrı bir sekmede açılır ve yapmış olduğunuz değişiklikleri yansıtır. Yapabilir, Geri Al ve kaydetmeye devam edebilirsiniz **Özet tanım** penceresi ve sekme bu değişiklikleri yansıtacak şekilde sürdürür. Değişikliklerinizi kaydetmeden pencereyi kapatsanız bile, tam olarak pencerede kaldığınız yeri seçerek, kalan değişikliklerinizi bu sekmede yapabilir, geri alabilir ve kaydedebilirsiniz.  
  
     ![Bir Özet penceresi içinde düzenleme](../ide/media/peekedit.png "PeekEdit")  
  
#### <a name="to-use-keyboard-shortcuts-for-peek-definition"></a>Özet Tanım klavye kısayollarını kullanmak için  
  
-   Bu klavye kısayollarını kullanabilirsiniz **Özet tanım** penceresi:  
  
    |İşlevi|Klavye kısayolu|  
    |-------------------|-----------------------|  
    |Tanım penceresini açma|Alt+F12|  
    |Tanım penceresini kapatma|Esc|  
    |Tanım penceresini bir normal belge sekmesine yükseltme|Shift+Alt+Home|  
    |Tanım pencereleri arasında gezinme|Ctrl+Alt+- ve Ctrl+Alt+=|  
    |Birden fazla sonuç arasında gezinme|F8ve Shift+F8|  
    |Kod düzenleyicisi penceresi ile tanım penceresi arasında geçiş yapma|Shift+Esc|  
  
    > [!NOTE]
    >  Kodu düzenleme için aynı klavye kısayollarını kullanabilirsiniz bir **Özet tanım** aynı pencereyi kullanırsınız başka bir yerde Visual Studio'da.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Üretkenlik İpuçları](../ide/productivity-tips-for-visual-studio.md)



