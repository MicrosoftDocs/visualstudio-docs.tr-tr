---
title: Şerit XML
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VSTO.Ribbon.RibbonXMLItem
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, XML
- customizing the Ribbon, XML
- Ribbon [Office development in Visual Studio], XML
- callback methods
- custom Ribbon, displaying
- custom Ribbon, defining behavior
- XML [Office development in Visual Studio], Ribbon
- customizing the Ribbon, defining behavior
- Ribbon [Office development in Visual Studio], customizing
- customizing the Ribbon, displaying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e5502ed118bf5b8bf622f18fd777889127e12aab
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672458"
---
# <a name="ribbon-xml"></a>Şerit XML
  Şerit (XML) öğesini Şerit XML kullanarak özelleştirmenize olanak sağlar. Şerit (Görsel Tasarımcı) öğesi tarafından desteklenmeyen bir biçimde Şerit özelleştirmek istiyorsanız Şerit (XML) öğesini kullanın. Her bir öğeyle neler yapabileceğinizi bir karşılaştırması için bkz [Şerite Genel Bakış](../vsto/Ribbon-overview.md).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## <a name="add-a-ribbon-xml-item-to-a-project"></a>Bir Şerit (XML) öğesini projeye ekleme  
 Ekleyebileceğiniz bir **Ribbon (XML)** herhangi bir Office projesinden öğesine **Yeni Öğe Ekle** iletişim kutusu. Visual Studio, otomatik olarak aşağıdaki dosyaları projenize ekler:  
  
- Bir Şerit XML dosyası. Bu dosya, Şerit kullanıcı arabirimini (UI) tanımlar. Sekmeler, gruplar ve denetimler gibi kullanıcı Arabirimi öğeleri eklemek için bu dosyayı kullanın. Ayrıntılar için bkz [Ribbon XML dosya başvurusu](#RibbonDescriptorFile) bu konuda.  
  
- Bir Şerit kod dosyası. Bu dosyayı içeren *Şerit sınıfı*. Bu sınıf için belirttiğiniz ada sahip **Ribbon (XML)** öğesi **Yeni Öğe Ekle** iletişim kutusu. Microsoft Office uygulamaları, Şerit yüklemek için bu sınıfın bir örneği kullanın. Ayrıntılar için bkz [Şerit sınıf başvurusu](#RibbonExtensionClass) bu konuda.  
  
  Varsayılan olarak, bu dosyaları için özel bir grup ekleme **eklentileri** Şerit sekmesi.  
  
## <a name="display-the-custom-ribbon-in-a-microsoft-office-application"></a>Özel bir Microsoft Office uygulamasının şeridinde görüntüleme  
 Siz ekledikten sonra bir **Ribbon (XML)** öğesi için kod projenize eklemelisiniz **ThisAddIn**, **ThisWorkbook**, veya **ThisDocument** sınıfı Bu geçersiz kılmaları `CreateRibbonExtensibilityObject` Office uygulamasına sınıf yöntemi ve Şerit XML döndürür.  
  
 Aşağıdaki kod örneği geçersiz kılmaları `CreateRibbonExtensibilityObject` adlandırılmış MyRibbon sınıf yöntemi ve bir Şerit XML döndürür.  
  
 [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
 [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]  
  
## <a name="define-the-behavior-of-the-custom-ribbon"></a>Özel Şerit davranışını tanımlayın  
 Oluşturarak Şeritte bir düğmeye tıklanması gibi kullanıcı eylemlerine yanıtlayabilir *geri çağırma yöntemleri*. Windows Forms denetimlerindeki olaylar geri çağırma yöntemleri benzer, ancak UI öğesinin bir öznitelik tarafından tanımlanır. Şerit sınıfında yöntemleri yazın ve bir denetim öznitelik değeri aynı ada sahip bir yöntemi çağırır. Örneğin, bir kullanıcı Şeritteki bir düğmeyi tıkladığında çağrılan bir geri çağırma yöntemi oluşturabilirsiniz. Bir geri çağırma yöntemi oluşturmak için iki adım gerekir:  
  
-   Kodunuzda bir geri çağırma yöntemi tanımlayan Ribbon XML dosyasındaki bir denetim için bir öznitelik atayın.  
  
-   Geri çağırma yöntemi, Şerit sınıfında tanımlayın.  
  
> [!NOTE]  
>  Outlook için ek bir adım gereklidir. Daha fazla bilgi için [Outlook için Şerit özelleştirme](../vsto/customizing-a-ribbon-for-outlook.md).  
  
 Şeritte bir uygulamanın nasıl oluşturulduğunu gösteren bir kılavuz için bkz. [izlenecek yol: Şerit XML kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md).  
  
### <a name="assign-callback-methods-to-controls"></a>Geri çağırma yöntemleri denetimleri atama  
 Ribbon XML dosyasındaki bir denetim için bir geri çağırma yöntemi atamak için geri çağırma yöntemi türünü ve yöntemin adını belirten bir özniteliği ekleyin. Örneğin, aşağıdaki öğe olan iki durumlu düğme tanımlar bir **onAction** adlı geri çağırma yöntemi `OnToggleButton1`.  
  
```xml  
<toggleButton id="toggleButton1" onAction="OnToggleButton1" />  
```  
  
 **onAction** kullanıcı belirli bir denetimle ilişkili ana görev yaptığında çağrılır. Örneğin, **onAction** iki durumlu bir düğmenin geri çağırma yöntemi, kullanıcı düğmeye tıkladığında çağrılır.  
  
 Öznitelik, belirttiğiniz yöntemi herhangi bir ad olabilir. Ancak, bu Şerit kod dosyasını tanımlayan yöntemin adı eşleşmelidir.  
  
 Farklı türlerde Şerit denetimleri atamak için geri çağırma yöntemleri vardır. Her denetim için geri çağırma yöntemleri tam listesi için teknik makaleye bakın [(Bölüm 3 / 3) geliştiriciler için Office (2007) Şerit kullanıcı arabirimini özelleştirme](/previous-versions/office/developer/office-2007/aa722523(v=office.12)).  
  
###  <a name="CallBackMethods"></a> Geri Çağırma yöntemlerini tanımlamak  
 Şerit kod dosyasını Şerit sınıfında, geri çağırma yöntemleri tanımlar. Bir geri çağırma yöntemi, birkaç gereksinim vardır:  
  
- Bu genel olarak bildirilmelidir.  
  
- Ribbon XML dosyasındaki bir denetime atanmış bir geri çağırma yöntemi adını adının eşleşmesi gerekir.  
  
- İmzası bir tür bir geri çağırma yöntemi, ilişkili Şerit denetimi için kullanılabilir imzayla eşleşmelidir.  
  
  Şerit denetimleri için geri çağırma yöntem imzaları tam listesi için teknik makaleye bakın [(Bölüm 3 / 3) geliştiriciler için Office (2007) Şerit kullanıcı arabirimini özelleştirme](/previous-versions/office/developer/office-2007/aa722523(v=office.12)). Visual Studio, Şerit kod dosyasını oluşturma geri çağırma yöntemleri için IntelliSense desteği sağlamaz. Bir geri çağırma yöntemi oluşturursanız, geçerli bir imzası eşleşmiyor, kod derlenir, ancak hiçbir kullanıcı denetimi tıklattığında oluşur.  
  
  Tüm geri çağırma yöntemleri bir <xref:Microsoft.Office.Core.IRibbonControl> yöntem denetimini temsil eden bir parametre. Bu parametre, birden çok denetim aynı geri çağırma yöntemini yeniden kullanabilirsiniz. Aşağıdaki kod örneğinde bir **onAction** bağlı olarak, kullanıcı denetimi tıklattığında farklı görevler gerçekleştiren bir geri çağırma yöntemi.  
  
  [!code-csharp[Trin_RibbonOutlookBasic#2](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#2)]
  [!code-vb[Trin_RibbonOutlookBasic#2](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#2)]  
  
##  <a name="RibbonDescriptorFile"></a> Şerit XML dosyası başvurusu  
 Şerit öğe ekleme ve öznitelikleri için Ribbon XML dosyasındaki tanımlayabilirsiniz. Varsayılan olarak, aşağıdaki XML Ribbon XML dosyasındaki içerir.  
  
```xml  
<?xml version="1.0" encoding="UTF-8"?>  
<customUI xmlns="http://schemas.microsoft.com/office/2006/01/customui" onLoad="OnLoad">  
  <ribbon>  
    <tabs>  
      <tab idMso="TabAddIns">  
        <group id="MyGroup"  
               label="My Group">  
        </group>  
      </tab>  
    </tabs>  
  </ribbon>  
</customUI>  
```  
  
 Aşağıdaki tabloda Ribbon XML dosyasındaki varsayılan öğeleri açıklar.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|**Customuı**|Şerit VSTO eklenti projesinde temsil eder.|  
|**Şerit**|Şerit temsil eder.|  
|**Sekmeleri**|Şerit Sekmeleri kümesini temsil eder.|  
|**sekmesi**|Tek bir Şerit sekmesi temsil eder.|  
|**Grup**|Şerit sekmesinde denetimlerin bir grubu temsil eder.|  
  
 Bu öğeleri görünümünü ve davranışını özel Şerit belirten öznitelikleri vardır. Aşağıdaki tabloda Ribbon XML dosyasındaki varsayılan öznitelikleri açıklar.  
  
|Öznitelik|Üst öğe|Açıklama|  
|---------------|--------------------|-----------------|  
|**Yüklendiğinde**|**Customuı**|Şerit uygulama yüklendiğinde çağrılan bir yöntemi tanımlar.|  
|**idMso**|**sekmesi**|Şeritte görüntülemek için yerleşik bir sekmeyi belirtir.|  
|**id**|**Grup**|Grubu tanımlar.|  
|**Etiket**|**Grup**|Grup üzerinde görüntülenen metni belirtir.|  
  
 Varsayılan öğeler ve öznitelikler Ribbon XML dosyasındaki kullanılabilen öznitelikleri ve öğeleri küçük alt kümesidir. Kullanılabilir öğeler ve öznitelikler tam listesi için teknik makaleye bakın [(Kısım 2 / 3) geliştiriciler için Office (2007) Şerit kullanıcı arabirimini özelleştirme](/previous-versions/office/developer/office-2007/aa338199(v=office.12)).  
  
##  <a name="RibbonExtensionClass"></a> Şerit sınıf başvurusu  
 Visual Studio Şerit sınıfı Şerit kod dosyasını oluşturur. Bu sınıf için Şerit üzerindeki denetimleri için geri çağırma yöntemleri ekleyin. Bu sınıfın uyguladığı <xref:Microsoft.Office.Core.IRibbonExtensibility> arabirimi.  
  
 Aşağıdaki tabloda, bu sınıf varsayılan yöntemleri açıklar.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`GetCustomUI`|Şerit XML dosyasının içeriğini döndürür. Microsoft Office uygulamaları, Şerit kullanıcı arabirimini tanımlayan bir XML dizesi elde etmek için bu yöntemi çağırır. Bu yöntem <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> yöntemi. **Not:** `GetCustomUI` yalnızca Ribbon XML dosyasındaki; içeriğini döndürmek için uygulanması gereken VSTO eklenti başlatmak için kullanılmamalıdır. Özellikle, görünen iletişim kutuları veya diğer windows çalışmamanız gerekir, `GetCustomUI` uygulaması. Aksi takdirde, özel Şerit düzgün çalışmayabilir. VSTO eklenti başlatan kodu çalıştırmak varsa, kodu ekleyin `ThisAddIn_Startup` olay işleyicisi.|  
|`OnLoad`|Atar <xref:Microsoft.Office.Core.IRibbonControl> parametresi `Ribbon` alan. Şerit'i yüklediğinizde, Microsoft Office uygulamaları bu yöntemi çağırın. Özel Şerit dinamik olarak güncelleştirmek için bu alanı kullanabilirsiniz. Daha fazla bilgi için teknik makaleye bakın [(Kısım 1 / 3) geliştiriciler için Office (2007) Şerit kullanıcı arabirimini özelleştirme](/previous-versions/office/developer/office-2007/aa338202(v=office.12)).|  
|`GetResourceText`|Çağıran `GetCustomUI` Ribbon XML dosyasının içeriğini almak için yöntemi.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Şerite Genel Bakış](../vsto/ribbon-overview.md)   
 [İzlenecek yol: Şerit XML kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)   
 [Office kullanıcı arabirimini özelleştirme](../vsto/office-ui-customization.md)  
  
  