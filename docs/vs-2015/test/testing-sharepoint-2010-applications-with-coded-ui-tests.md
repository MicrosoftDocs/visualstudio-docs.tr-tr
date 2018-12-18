---
title: Kodlanmış UI testleriyle SharePoint 2010 uygulamalarını test etme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51b53778-469c-4cc9-854c-4e4992d6389b
caps.latest.revision: 32
ms.author: gewarren
manager: douge
ms.openlocfilehash: e450cd333c01e4e2e557013ef106337fe5a80a71
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49937284"
---
# <a name="testing-sharepoint-2010-applications-with-coded-ui-tests"></a>Kodlanmış UI Testleriyle SharePoint 2010 Uygulamalarını Test Etme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kodlanmış UI testleri içindeki bir SharePoint uygulaması da dahil olmak üzere, kendi kullanıcı Arabirimi denetimleri de dahil olmak üzere tüm uygulamanın düzgün çalıştığını doğrulamak olanak tanır. Kodlanmış UI testleri, değerleri ve kullanıcı arabirimi mantığı da doğrulayabilirsiniz.  
  
 **Gereksinimler**  
  
-   Visual Studio Enterprise  
  
## <a name="what-else-should-i-know-about-coded-ui-tests"></a>Kodlanmış UI testleri hakkında başka neleri bilmeliyim?  
 Kodlanmış UI testleri kullanmanın avantajları hakkında daha fazla bilgi için bkz: [kullanım UI Otomasyon için Test kodunuzu](../test/use-ui-automation-to-test-your-code.md) ve [Visual Studio 2012 – bölüm 5 otomatikleşen sistem testleri ile sürekli teslimat testi](http://go.microsoft.com/fwlink/?LinkID=255196).  
  
 **Notlar**  
  
-   ![Prerequsite](../test/media/prereq.png "önkoşul uyarılarını gözardı et") SharePoint uygulamaları için kodlanmış UI testleri yalnızca SharePoint 2010 ile desteklenir.  
  
-   ![Prerequsite](../test/media/prereq.png "önkoşul uyarılarını gözardı et") Visio ve PowerPoint 2010, SharePoint uygulamanızın denetimlerinde desteği desteklenmiyor.  
  
## <a name="creating-a-coded-ui-test-for-your-sharepoint-app"></a>SharePoint uygulamanız için kodlanmış UI testi oluşturma  
 [Kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate) , SharePoint 2010 uygulamaları için diğer uygulama türleri için testleri oluşturma ile aynıdır. Kayıt ve kayıttan yürütme, Web'den düzenlemeyi arabirimindeki tüm denetimler için desteklenir. Kategorileri ve web bölümleri seçme arabirimi, tüm standart web denetimler bulunur.  
  
 ![SharePoint web bölümleri](../test/media/cuit-sharepoint.png "CUIT_SharePoint")  
  
> [!NOTE]
>  Eylem kaydı yapıyorsanız, eylemleri, kod oluşturmadan önce doğrulayın. Bazı davranışları fareyle üzerine gelindiğinde ile ilişkili olduğundan, varsayılan olarak açıktır. Yedekli eklenmemesi, kodlanmış UI testlerini kaldırmak dikkatli olun. Test için kod düzenleme veya kullanarak bunu yapabilirsiniz [kodlanmış UI Test Düzenleyicisi](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).  
  
## <a name="including-testing-of-office-2010-controls-within-your-sharepoint-app"></a>SharePoint uygulamanız içinde Office 2010 denetimlerin testi dahil olmak üzere  
 Bazı office 2010 web bölümleri SharePoint uygulamanızda Otomasyon etkinleştirmek için bazı küçük bir kod değişikliği yapmanız gerekir.  
  
> [!WARNING]
>  Visio ve PowerPoint 2010 denetimleri için desteği desteklenmiyor.  
  
### <a name="excel-2010-cell-controls"></a>Excel 2010 hücre denetimleri  
 Excel hücre denetimleri eklemek için kodlanmış UI test kodu bazı değişiklikler yapmanız gerekir.  
  
> [!WARNING]
>  Ok anahtar eylemi tarafından izlenen herhangi bir Excel hücreyi metin girme doğru kaydetmez. Hücreleri seçmek için fare kullanın.  
  
 Boş bir hücreye eylemleri kaydediyorsanız, double hücreyi tıklayarak ve ardından kümesi metin işlemi gerçekleştirme kodu değiştirmeniz gerekir. Tüm klavye eylemi tarafından izlenen hücrenin click etkinleştirir çünkü bu gerekli `textarea` hücresi içinde. Yalnızca kaydı bir `setvalue` boş hücreyi aramak `editbox` tıklanan hücre kadar mevcut değil. Örneğin:  
  
```csharp  
Mouse.DoubliClick(uiItemCell,new Point(31,14));  
uiGridKeyboardInputEdit.Text=value;  
```  
  
 Eylemler boş olmayan hücre kaydetmekte olduğunuz sonra çünkü kaydı biraz daha karmaşık alır bir hücre için metni ekleme şu anda yeni bir \<div > denetimi hücrenin alt olarak eklenir. Yeni \<div > girdiğiniz metin denetimi içerir. Kaydedici eylemleri yeni kaydetmek gereken \<div > denetimi; ancak, çünkü olamaz yeni \<div > Denetim yok kadar test girildikten sonra. Bu sorunu uyum sağlamak için aşağıdaki kod değişikliklerini el ile yapmalısınız.  
  
1.  Hücre başlatma için gidin ve olun `RowIndex` ve `ColumnIndex` birincil özellikleri:  
  
    ```csharp  
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. RowIndex] = "3";   
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. ColumnIndex] = "3";  
    ```  
  
2.  Bulma `HtmlDiv` alt hücrenin:  
  
    ```csharp  
    private UITestControl getControlToDoubleClick(HtmlCell cell)   
    {   
         if (String.IsNullOrEmpty(cell.InnerText)) return cell;   
         HtmlDiv pane = new HtmlDiv(cell);   
         pane.FilterProperties[HtmlDiv.PropertyNames.InnerText] = cell.InnerText;   
         // Class is an important property in finding pane   
         pane.FilterProperties[HtmlDiv.PropertyNames.Class] = "cv-nwr";   
         UITestControlCollection panes = pane.FindMatchingControls();   
         return panes[0];   
    }  
  
    ```  
  
3.  Kod bir fare çift tıklatın için eylem ekleme `HtmlDiv`:  
  
    ```csharp  
    Mouse.DoubleClick(uIItemPane, new Point(31, 14)); )  
    ```  
  
4.  Metni ayarlamak için kod ekleme `TextArea`:  
  
    ```csharp  
    uIGridKeyboardInputEdit.Text = value; }  
    ```  
  
## <a name="enabling-coded-ui-testing-of-silverlight-web-parts-in-your-sharepoint-2010-app"></a>Uygulamanızda SharePoint 2010 Silverlight web bölümleri UI testi kodlanmış etkinleştirme  
 Silverlight testi, Visual Studio 2012 ve sonraki sürümlerinde desteklenmez. Ancak, uygulamanızda SharePoint 2010 Silverlight web bölümleri test etmek isterseniz, Visual Studio Gallery'den ayrı Silverlight eklentisi yükleyebilirsiniz.  
  
#### <a name="setting-up-your-machine"></a>Makinenizi ayarlarken  
  
1. Daha sonra yüklenen veya sahip olduğunuz Visual Studio 2012.1 emin olun.  
  
2. Yükleme [Silverlight için Microsoft Visual Studio UI Test Eklentisi](http://visualstudiogallery.msdn.microsoft.com/28312a61-9451-451a-990c-c9929b751eb4).  
  
3. Yükleme [Fiddler](http://www.fiddler2.com/fiddler2/). Bu, yakalar ve HTTP trafiği günlükleri yalnızca bir araçtır.  
  
4. İndirme [fiddlerXap proje](http://blogs.msdn.com/cfs-file.ashx/__key/communityserver-components-postattachments/00-10-36-48-70/FiddlerXapProxy.zip). Sıkıştırılmış dosyayı derleyin ve Fiddler Aracı'nı kullandığınızda, Silverlight web bölümleri test etmek için gereken DLL Yardımcısı'nı yüklemek için "CopySLHelper.bat" komut dosyasını çalıştırın.  
  
   Uygulamanızı SharePoint 2010 Silverlight web bölümleri içeren test başlatmak için makinenizi kurmak ayarladıktan sonra aşağıdaki adımları izleyin:  
  
#### <a name="testing-silverlight-web-parts"></a>Silverlight web bölümleri test etme  
  
1.  Fiddler'ı başlatın.  
  
2.  Tarayıcı önbelleğini temizleyin. Silverlight UI Otomasyon Yardımcısı DLL içeren XAP dosyası genellikle önbelleğe alındığından, bu gereklidir. Biz tarayıcı önbelleğini temizlemek için değiştirilen XAP dosyası çekilir emin olmanız gerekir.  
  
3.  Web sayfasını açın.  
  
4.  Kaydediciyi başlatmak ve bir normal web uygulamasını test etmek için yaptığınız gibi kod üretebilirsiniz.  
  
5.  Oluşturulan kodun Microsoft.VisualStudio.TestTools.UITest.Extension.Silverlight.dll başvuran onaylamalıdır.  
  
     Daha fazla bilgi için [UI testi SharePoint 2010 ile Visual Studio 2012](http://blogs.msdn.com/b/visualstudioalm/archive/2012/11/01/ui-testing-sharepoint-2010-with-visual-studio-2012.aspx)  
  
## <a name="external-resources"></a>Dış kaynaklar  
  
### <a name="blogs"></a>Bloglar  
 [Visual Studio 2012 ile SharePoint 2010 test kullanıcı Arabirimi](http://blogs.msdn.com/b/visualstudioalm/archive/2012/11/01/ui-testing-sharepoint-2010-with-visual-studio-2012.aspx)  
  
 [Kodlanmış UI testi Silverlight denetimleri için arama mantığı anlama](http://blogs.msdn.com/b/tapas_sahoos_blog/archive/2010/11/16/understanding-the-search-logic-for-silverlight-controls-in-coded-ui-test.aspx)  
  
 [Bir Silverlight denetimi özelliği getiriliyor](http://blogs.msdn.com/b/tapas_sahoos_blog/archive/2010/11/16/fetching-property-of-a-silverlight-control.aspx)  
  
 [Kodlanmış UI testi için içerik dizini](http://blogs.msdn.com/b/mathew_aniyan/archive/2010/02/11/content-index-for-coded-ui-test.aspx)  
  
### <a name="guidance"></a>Kılavuz  
 [Sistem testleri otomatikleştirerek bölüm 5 – Visual Studio 2012 ile sürekli teslimat testi](http://go.microsoft.com/fwlink/?LinkID=255196)  
  
### <a name="forum"></a>Forum  
 [Visual Studio ALM + Team Foundation Server blogu](http://go.microsoft.com/fwlink/?LinkID=254496)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)   
 [Web performansı ve yük SharePoint 2010 ve 2013 uygulamalarını test etme](http://msdn.microsoft.com/library/20c2e469-0e4e-4296-a739-c0e8fff36e54)   
 [SharePoint çözümleri oluşturma](http://msdn.microsoft.com/library/4bfb1e59-97c9-4594-93f8-3068b4eb9631)   
 [Doğrulama ve SharePoint kod hata ayıklama](http://msdn.microsoft.com/library/b5f3bce2-6a51-41b1-a292-9e384bae420c)   
 [Oluşturma ve SharePoint çözümlerinde hata ayıklama](http://msdn.microsoft.com/library/c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae)   
 [SharePoint Uygulamaları için Performans Profili Oluşturma](http://msdn.microsoft.com/library/61ae02e7-3f37-4230-bae1-54a498c2fae8)



