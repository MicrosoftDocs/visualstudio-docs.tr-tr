---
title: Araç kutusu, HTML sekmesi | Microsoft Docs
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
- vs.toolbox.html
helpviewer_keywords:
- Toolbox, HTML tab
- HTML Designer, setting options
- HTML tab in Toolbox
ms.assetid: 9bfdd3b8-f5ac-4a5f-bdbf-c2b4e97641d8
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 31ee75c419870d9047b3892c668c5e4665850654
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49292082"
---
# <a name="toolbox-html-tab"></a>Araç Kutusu, HTML Sekmesi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
**HTML** araç kutusu sekmesi Web sayfalarını ve Web forms yararlı olan bileşenleri sağlar. Bu sekme görüntülemek için ilk HTML Tasarımcısı'nda düzenlemek için bir belgeyi açın. Üzerinde **görünümü** menüsünde tıklatın **araç kutusu**ve ardından **HTML** araç kutusu sekmesi.  
  
 Bir aracı örneği oluşturmak için **HTML** sekmesinde ya da çift aracı belgenize geçerli ekleme noktasına ekleyin veya aracı seçin ve düzenleme yüzeyi üzerinde istenen konuma sürükleyin.  
  
## <a name="tasks"></a>Görevler  
  
-   [Nasıl yapılır: araç kutusu penceresini yönetme](http://msdn.microsoft.com/en-us/a022c3fe-298c-4a59-a48f-b050da90ebc2)  
  
-   [Nasıl yapılır: araç kutusu sekmeleri düzenleme](http://msdn.microsoft.com/en-us/21285050-cadd-455a-b1f5-a2289a89c4db)  
  
## <a name="ui-elements"></a>Kullanıcı Arabirimi öğeleri  
 Aşağıdaki araçlar, HTML sekmesi varsayılan olarak kullanılabilir.  
  
 **İşaretçi**  
 ![ASP.NET Mobil Tasarımcısı HTMLpage işaretçi](../../ide/reference/media/vxpointer.gif "vxPointer")  
  
 Bu araç, herhangi bir araç kutusu sekmeyi açıldığında, varsayılan olarak seçilidir. Silinemiyor. İşaretçiyi, nesneler görünümü tasarım yüzeyine sürükleyin, yeniden boyutlandırabilir ve sayfa veya form üzerinde yeniden konumlandırmak sağlar. Daha fazla bilgi için [nasıl yapılır: araç kutusu penceresini yönetme](http://msdn.microsoft.com/en-us/a022c3fe-298c-4a59-a48f-b050da90ebc2) ve [nasıl yapılır: araç kutusu sekmeleri işlemek](http://msdn.microsoft.com/en-us/21285050-cadd-455a-b1f5-a2289a89c4db).  
  
 **Giriş (düğme)**  
 ![HTML web sayfası düğmesi](../../ide/reference/media/vxbutton.gif "vxButton")  
  
 Ekler bir `input` öğesinin `type="button"`. Görüntülenen metni değiştirmek için Düzenle `name` özelliği. Varsayılan olarak, `id="Button1"` ilk düğme için eklenen `id="Button2"` saniye vb. için.  
  
 Sürüklediğinizde **giriş (düğme)** Tasarım görünümü yüzeyine HTML biçimlendirmeyi aşağıdaki gibi belgenize eklenir:  
  
```  
<input id="Button1" type="button" value="Button" name="Button1">  
```  
  
 Daha fazla bilgi için bkz. [HTML giriş denetimlerine](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [HtmlInputButton sunucu denetimi bildirim temelli sözdizimi](http://msdn.microsoft.com/en-us/99ccf7fb-7e2a-4ba1-bcd9-981b619a16aa), [NIB: nasıl yapılır: betikleri oluşturma ve olay işleyicileri düzenlemek](http://msdn.microsoft.com/en-us/69d71d13-c68b-4ecd-869b-a42edf6d1f6d), [ Düğme Web sunucusu denetimleri içerik haritası](http://msdn.microsoft.com/library/66b3ce28-3b93-4f0a-951f-42fb5bb5fddf), <xref:System.Web.UI.HtmlControls.HtmlInputButton>, <xref:System.Web.UI.HtmlControls.HtmlButton>, ve <xref:System.Web.UI.WebControls.Button>.  
  
 **Giriş (Sıfırla)**  
 ![HTMLpageResetButton ekran](../../ide/reference/media/vxreset.gif "vxReset")  
  
 Ekler bir `input` öğesinin `type="reset"`. Görüntülenen metni değiştirmek için Düzenle `name` özelliği. Varsayılan olarak, `id="Reset1"` Sıfırla düğmesi, ilk için eklenen `id="Reset2"` saniye vb. için.  
  
 Sürüklediğinizde **giriş (Sıfırla)** Tasarım görünümü yüzeyine HTML biçimlendirmeyi aşağıdaki gibi belgenize eklenir:  
  
```  
<input id="Reset1" type="reset" value="Reset" name="Reset1">  
```  
  
 Daha fazla bilgi için [HTML giriş denetimlerine](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [HtmlInputReset sunucu denetimi bildirim temelli sözdizimi](http://msdn.microsoft.com/en-us/cfc1f1fb-d33a-464d-9bb5-204e66174979), <xref:System.Web.UI.HtmlControls.HtmlInputButton>, ve <xref:System.Web.UI.WebControls.Button>.  
  
 **Giriş (Gönder)**  
 ![HTMLpageToolbarSubmitButton ekran](../../ide/reference/media/vxsubmit.gif "vxSubmit")  
  
 Ekler bir `input` öğesinin `type="submit"`. Görüntülenen metni değiştirmek için Düzenle `name` özelliği. Varsayılan olarak, `id="Submit1"` ilk Gönder düğmesini için eklenen `id="Submit2"` saniye vb. için.  
  
 Sürüklediğinizde **giriş (Gönder)** Tasarım görünümü yüzeyine HTML biçimlendirmeyi aşağıdaki gibi belgenize eklenir:  
  
```  
<input id="Submit1" type="submit" value="Submit" name="Submit1">  
```  
  
 Daha fazla bilgi için [HTML giriş denetimlerine](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [HtmlInputSubmit sunucu denetimi bildirim temelli sözdizimi](http://msdn.microsoft.com/en-us/eef2a157-f184-4ce9-b256-d1eacc7930f2), <xref:System.Web.UI.HtmlControls.HtmlInputButton>, ve <xref:System.Web.UI.WebControls.Button>.  
  
 **Girişi (metin)**  
 ![HTMLpageToolbarTextField ekran](../../ide/reference/media/vxtextfield.gif "vxTextfield")  
  
 Ekler bir `input` öğesinin `type="text"` belgenizdeki. Görüntülenen varsayılan metni değiştirmek için Düzenle `value` özniteliği. Varsayılan olarak, `id="Text1"` ilk metin alanı için eklenen `id="Text2"` saniye vb. için.  
  
 Sürüklediğinizde **girişi (metin)** Tasarım görünümü yüzeyine HTML biçimlendirmeyi aşağıdaki gibi belgenize eklenir:  
  
```  
<input id="Text1" TYPE="text" value="Text Field" name="Text1">  
```  
  
 Daha fazla bilgi için [HTML giriş denetimlerine](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [HtmlInputText sunucu denetimi bildirim temelli sözdizimi](http://msdn.microsoft.com/en-us/87060d90-a11c-434d-9fc9-b03a8487041e), [Web sunucusu için TextBox denetimine genel bakış](http://msdn.microsoft.com/library/ab354bc1-f23a-48fc-93d8-d4d7c1b7396f), <xref:System.Web.UI.HtmlControls.HtmlInputText>, ve <xref:System.Web.UI.WebControls.TextBox>.  
  
> [!IMPORTANT]
>  Tüm kullanıcı girişi doğrulamanız önerilir. Daha fazla bilgi için [kullanıcı girişini doğrulama ASP.NET Web Pages'de](http://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).  
  
 **Giriş (dosya)**  
 ![HTML sayfası dosya alanı](../../ide/reference/media/vxfilefield.gif "vxFilefield")  
  
 Ekler bir `input` öğesinin `type="file"` belgenizdeki. Varsayılan olarak, `id="File1"` ilk dosya alanı için eklenen `id="File2"` saniye vb. için.  
  
 Sürüklediğinizde **giriş (dosya)** Tasarım görünümü yüzeyine HTML biçimlendirmeyi aşağıdaki gibi belgenize eklenir:  
  
```  
<input id="File1" type="file" name="File1">  
```  
  
 Daha fazla bilgi için [HTML giriş denetimlerine](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [HtmlInputFile Sunucu denetimi bildirim temelli sözdizimi](http://msdn.microsoft.com/en-us/a817b4a0-056f-4c17-a696-b9fdcde43db6), ve <xref:System.Web.UI.HtmlControls.HtmlInputFile>.  
  
> [!IMPORTANT]
>  Tüm kullanıcı girişi doğrulamanız önerilir. Daha fazla bilgi için [kullanıcı girişini doğrulama ASP.NET Web Pages'de](http://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).  
  
 **Giriş (parola)**  
 ![Visual Studio parola alanı](../../ide/reference/media/vxpassword.gif "vxPassword")  
  
 Ekler bir `input` öğesinin `type="password"`. Varsayılan olarak, `id="Password1"` ilk parola alanına eklenen `id="Password2"` saniye vb. için.  
  
 Sürüklediğinizde **giriş (parola)** Tasarım görünümü yüzeyine HTML biçimlendirmeyi aşağıdaki gibi belgenize eklenir:  
  
```  
<input id="Password1" type="password" name="Password1">  
```  
  
 Daha fazla bilgi için bkz [HTML giriş denetimlerine](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [HtmlInputPassword Sunucu denetimi bildirim temelli sözdizimi](http://msdn.microsoft.com/en-us/df703dd0-1624-4e5a-a547-c97f2f331b9f), [nasıl yapılır: TextBox Web sunucusu denetimi için parola girişi Ayarla](http://msdn.microsoft.com/library/5b5069f3-64a1-435a-aee6-da263f4e6310), ve [izlenecek yol: bir Web uygulamasında kullanıcı girdisi doğrulama Forms sayfası](http://msdn.microsoft.com/library/7141d6ba-34f3-410b-b5cd-2102a24cb436).  
  
> [!IMPORTANT]
>  Uygulamanızın kullanıcı adları ve parolalar gönderiyorsa, Web sitenizi iletim şifrelemek için Güvenli Yuva Katmanı (SSL) kullanmak için yapılandırmanız gerekir. Daha fazla bilgi için bkz: "Bağlantı SSL ile güvenli hale getirme" [IIS işlemler Kılavuzu](http://go.microsoft.com/fwlink/?linkid=47856). Ayrıca, tüm kullanıcı girişi doğrulamanız önerilir. Daha fazla bilgi için [kullanıcı girişini doğrulama ASP.NET Web Pages'de](http://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).  
  
 **Giriş (onay kutusu)**  
 ![HTML Web sayfası araç onay kutusu seçeneğini](../../ide/reference/media/vxcheckbox.gif "vxCheckbox")  
  
 Ekler bir `input` öğesinin `type="checkbox"`. Görüntülenen metni değiştirmek için Düzenle `name` özelliği. Varsayılan olarak, `id="Checkbox1"` ilk onay kutusunu, eklenen `id="Checkbox2"` saniye vb. için.  
  
 Sürüklediğinizde **giriş (onay kutusu)** Tasarım görünümü yüzeyine HTML biçimlendirmeyi aşağıdaki gibi belgenize eklenir:  
  
```  
<input id="Checkbox1" type="checkbox" name="Checkbox1">   
```  
  
 Daha fazla bilgi için [HTML giriş denetimlerine](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [HtmlInputCheckBox sunucu denetimi bildirim temelli sözdizimi](http://msdn.microsoft.com/en-us/4a509586-89d8-4ccf-a0b8-b9160ce6e4a6), [onay kutusunu ve CheckBoxList Web sunucu denetimlerine genel bakış](http://msdn.microsoft.com/library/3028dfd3-e2c5-451d-9150-d02c8ffb92bf), <xref:System.Web.UI.HtmlControls.HtmlInputCheckBox>, ve <xref:System.Web.UI.WebControls.CheckBox>.  
  
 **Giriş (radyo)**  
 ![VisualStudioHTMLpageRadioButton ekran](../../ide/reference/media/vxradio.gif "vxRadio")  
  
 Ekler bir `input` öğesinin `type="radio"`. Görüntülenen metni değiştirmek için Düzenle `name` özelliği. Varsayılan olarak, `id="Radio1"` ilk radyo düğmesi için eklenen `id="Radio2"` saniye vb. için.  
  
 Sürüklediğinizde **giriş (radyo)** Tasarım görünümü yüzeyine HTML biçimlendirmeyi aşağıdaki gibi belgenize eklenir:  
  
```  
<input id="Radio1" type="radio" name="Radio1">  
```  
  
 Daha fazla bilgi için [HTML giriş denetimlerine](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [HtmlInputRadioButton Sunucu denetimi bildirim temelli sözdizimi](http://msdn.microsoft.com/en-us/6e60ff63-cc57-46ef-bf96-e829e204ba33), [RadioButton ve RadioButtonList Web sunucu denetimlerine genel bakış](http://msdn.microsoft.com/library/20eb383c-4b59-432b-bba3-e9d785107747), <xref:System.Web.UI.HtmlControls.HtmlInputRadioButton>, ve <xref:System.Web.UI.WebControls.RadioButton>.  
  
 **Giriş (gizli)**  
 ![HTML öğesi gizli sayfasında](../../ide/reference/media/vxhidden.gif "vxhidden")  
  
 Ekler bir `input` öğesinin `type="hidden"`. Varsayılan olarak, `id="Hidden1"` ilk gizli alan için eklenen `id="Hidden2"` saniye vb. için.  
  
 Sürüklediğinizde **giriş (gizli)** Tasarım görünümü yüzeyine HTML biçimlendirmeyi aşağıdaki gibi belgenize eklenir:  
  
```  
<input id="Hidden1" type="hidden" name="Hidden1">   
```  
  
 Daha fazla bilgi için [HTML giriş denetimlerine](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [HtmlInputHidden sunucu denetimi bildirim temelli sözdizimi](http://msdn.microsoft.com/en-us/4194e44d-1d74-4bfc-9cc7-743a2e1ea5f9), ve <xref:System.Web.UI.HtmlControls.HtmlInputHidden>.  
  
 **TextArea**  
 ![HTMLpage araç çubuğu metin alanı](../../ide/reference/media/vxtextarea.gif "vxTextarea")  
  
 Ekler bir `textarea` öğesi. Metin alanının yeniden boyutlandırmak veya kendi görüntüleme alanı genişletir metin görüntülemek için kaydırma çubuklarını kullanın. Görüntülenen varsayılan metni değiştirmek için Düzenle `value` özniteliği. Varsayılan olarak, `id="textarea1"` olan ilk metin alanında, eklenen `id=" textarea 2"` saniye vb. için.  
  
 Sürüklediğinizde **Textarea** Tasarım görünümü yüzeyine HTML biçimlendirmeyi aşağıdaki gibi belgenize eklenir:  
  
```  
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>   
```  
  
 Daha fazla bilgi için [HtmlTextArea sunucu denetimi bildirim temelli sözdizimi](http://msdn.microsoft.com/en-us/5a103ffa-235b-4452-ba2b-a4fb8ba8cb87), <xref:System.Web.UI.HtmlControls.HtmlTextArea>, ve <xref:System.Web.UI.WebControls.TextBox>.  
  
> [!IMPORTANT]
>  Tüm kullanıcı girişi doğrulamanız önerilir. Daha fazla bilgi için [kullanıcı girişini doğrulama ASP.NET Web Pages'de](http://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).  
  
 **Tablo**  
 ![HTMLpageToolbarTable ekran](../../ide/reference/media/vxtable.gif "vxTable")  
  
 Ekler bir `table` öğesi.  
  
 Sürüklediğinizde **tablo** Tasarım görünümü yüzeyine HTML biçimlendirmeyi aşağıdaki gibi belgenize eklenir:  
  
```  
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>   
```  
  
 Daha fazla bilgi için [HtmlTable Sunucu denetimi bildirim temelli sözdizimi](http://msdn.microsoft.com/en-us/625b06d8-0f69-4112-a1d4-8ef2a9fbcda9), [tablo TableRow'a ve TableCell Web sunucusu denetimine genel bakış](http://msdn.microsoft.com/library/2fbd0582-cf69-4c8d-9e35-21f35e2cee1a), <xref:System.Web.UI.HtmlControls.HtmlTable>, ve <xref:System.Web.UI.WebControls.Table>.  
  
 **Görüntü**  
 ![HTML sayfası görüntü öğesi](../../ide/reference/media/vximage.gif "vxImage")  
  
 Ekler bir `img` öğesi. Belirtmek için bu öğeyi düzenleyin, `src` ve kendi `alt` metin.  
  
 Sürüklediğinizde **görüntü** Tasarım görünümü yüzeyine HTML biçimlendirmeyi aşağıdaki gibi belgenize eklenir:  
  
```  
<img alt="" src="">  
```  
  
 Daha fazla bilgi için [HtmlImage Sunucu denetimi bildirim temelli sözdizimi](http://msdn.microsoft.com/en-us/528430e8-ced1-47d1-8db2-942e734a61f6), [Görüntü Web sunucusu denetimine genel bakış](http://msdn.microsoft.com/library/096a8d8d-58ee-4ee8-ab82-6594a0f3a0a9), <xref:System.Web.UI.HtmlControls.HtmlImage>, <xref:System.Web.UI.HtmlControls.HtmlInputImage>, ve <xref:System.Web.UI.WebControls.Image>.  
  
 **Seçin**  
 ![Araç kutusu açılır HTML sayfası](../../ide/reference/media/vxdropdown.gif "vxDropdown")  
  
 Bir açılan ekler `select` öğesi (olmadan bir `size` özniteliği). Varsayılan olarak, `id="select1"` ilk liste kutusu için eklenen `id="select2"` saniye vb. için.  
  
 Sürüklediğinizde **seçin** Tasarım görünümü yüzeyine HTML biçimlendirmeyi aşağıdaki gibi belgenize eklenir:  
  
```  
<select id="select1" name="select1"><option selected></option></select>  
```  
  
 Çok satırlı oluşturabilirsiniz `select` boyut özelliğinin değerini artırarak öğesi.  
  
 Daha fazla bilgi için bkz. [HtmlSelect Sunucu denetimi bildirim temelli sözdizimi](http://msdn.microsoft.com/en-us/ee93bdec-b343-441a-a8ff-56ffcafe9ae5), [NIB: nasıl yapılır: betikleri oluşturma ve olay işleyicileri düzenlemek](http://msdn.microsoft.com/en-us/69d71d13-c68b-4ecd-869b-a42edf6d1f6d), [DropDownList Web sunucusu denetimine genel bakış](http://msdn.microsoft.com/library/517dd1a4-8df3-4c9f-8c89-1549a1aee608), [ListBox Web sunucusu denetimine genel bakış](http://msdn.microsoft.com/library/c08ee025-787a-408d-858e-a4a5fdb61d97), <xref:System.Web.UI.HtmlControls.HtmlSelect>, ve <xref:System.Web.UI.WebControls.DropDownList>.  
  
 **Yatay cetvel**  
 ![HTML sayfası yatay cetvel öğesi](../../ide/reference/media/vxhorizontal.gif "vxHorizontal")  
  
 Ekler bir `hr` öğesi. Çizgi kalınlığı artırmak için Düzenle `size` özniteliği.  
  
 Sürüklediğinizde **yatay cetvel** Tasarım görünümü yüzeyine HTML biçimlendirmeyi aşağıdaki gibi belgenize eklenir:  
  
```  
<hr width="100%" size=1>   
```  
  
 Daha fazla bilgi için [HTML yatay kuralı denetimini](http://msdn.microsoft.com/library/bf6df0a8-9844-404d-8a9a-3455b0180f2f).  
  
 **div**  
 ![HTML sayfası etiketi](../../ide/reference/media/vxlabel.gif "vxLabel")  
  
 Ekler bir `div` içeren öğesi bir `ms_positioning="FlowLayout"` özniteliği. Genişlik ve yükseklik dışında bu öğeyi bir akış düzeni paneline aynıdır. İçinde yer alan metni biçimlendirmek için `div` öğe, Ekle bir `class="stylename"` özniteliği için açılış etiketi.  
  
 Sürüklediğinizde **Div** Tasarım görünümü yüzeyine HTML biçimlendirmeyi aşağıdaki gibi belgenize eklenir:  
  
```  
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>  
```  
  
 Daha fazla bilgi için [HTML Div denetimini](http://msdn.microsoft.com/library/585fa702-4408-4af1-a92b-68d77ee5e995), [Web sunucusu için etiket denetimine genel bakış](http://msdn.microsoft.com/library/990558d1-4b22-4f28-b100-78a434b3c5ac), ve <xref:System.Web.UI.WebControls.Label>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Araç kutusu](../../ide/reference/toolbox.md)   
 [Standart sekmesi, araç kutusu](http://msdn.microsoft.com/library/35e9320d-fcbd-474b-8b8f-55705e9a1870)   
 [HTML denetimleri](http://msdn.microsoft.com/library/83bc6f7e-a2b5-4fe9-9a34-eb34aef673be)



