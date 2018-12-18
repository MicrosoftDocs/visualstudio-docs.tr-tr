---
title: Kural kümesi Düzenleyicisi iletişim kutusu (eski) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleSetDialog.UI
helpviewer_keywords:
- Rule Set Editor dialog box
ms.assetid: 7cfd5df1-1115-4e5c-9b72-121f39419e83
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 3469e395ee50e63f8ac76e4181d02b777ccbd4ba
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942406"
---
# <a name="rule-set-editor-dialog-box-legacy"></a>Kural Kümesi Düzenleyicisi İletişim Kutusu (Eski)
Bu konu açıklar nasıl **kural kümesi Düzenleyicisi** eski iletişim kutusunda [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Eski kullanın [!INCLUDE[wfd2](../includes/wfd2-md.md)] hedeflemek gerektiğinde [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] veya [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 **Kural kümesi Düzenleyicisi** iletişim kutusu oluşturmak ve değiştirmek için kullanılan [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) .rules dosya serileştirilmiş kümeleri, kural.  
  
> [!NOTE]
>  .Rules dosyasıyla açmak isteyip istemediğiniz **kodlama ile XML Düzenleyicisi**, etkinlik ve iş akışı için ilişkili Tasarımcı penceresini kapatın.  
  
 Nasıl erişileceği hakkında daha fazla bilgi için **kural kümesi Düzenleyicisi** iletişim kutusu, bakın [nasıl yapılır: bir PolicyActivity kural kümesi (eski) oluşturma](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md).  
  
> [!WARNING]
>  Eski kural düzenleyiciyi [!INCLUDE[wfd2](../includes/wfd2-md.md)] hedeflemek için kullanılan [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] veya [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] çoklu hedefleme desteklemez.  
  
 Aşağıdaki tabloda kullanıcı arabirimi (UI) öğelerini açıklar **kural kümesi Düzenleyicisi** iletişim kutusu.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Kural Ekle**|Yeni bir kural tanımı kural kümesine ekler.|  
|**Delete**|Seçili kuralı kural kümesinden siler.|  
|**Zincirleme**|Kural kümesi ile kullanmak için ileriye doğru zincirleme türü belirtir. Kullanılabilir seçenekler şunlardır:<br /><br /> -   **Tam zincirleme**, tüm ileriye doğru zincirleme mekanizmaları kullanma belirtir: dolaylı yöntem öznitelik atanıyor ve açık bir **güncelleştirme** işlevi.<br />-   **Sıralı**, herhangi bir iletme zincirleme kullanmayacak şekilde belirtir.<br />-   **Yalnızca açık güncelleştirme**, yalnızca üzerinde İleri zincirleme gerçekleştirmek için belirten **güncelleştirme** eylemler.<br /><br /> İleriye doğru zincirleme hakkında daha fazla bilgi için bkz. [PolicyActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65004).|  
|**Ad**|Kural listesi sütun başlığını ayarlayın. Ada göre kural listesini sıralamak için tıklayın.|  
|**Öncelik**|Kural listesi sütun başlığını ayarlayın. Kurallar listesini öncelik sırasına göre sıralamak için tıklayın.|  
|**Yeniden değerlendirme**|Kural listesi sütun başlığını ayarlayın. Kuralları yeniden değerlendirme türü tarafından listesini sıralamak için tıklayın.|  
|**Kural Önizleme**|Kural listesi sütun başlığını ayarlayın. Bir kuralın koşulunu ve eylemlerini önizlemesini kurallarının listesini sıralamak için tıklayın.|  
|**Adı:**|Kural adını girin.|  
|**Önceliği:**|Kural için bir öncelik girin. Varsayılan öncelik 0'dır.|  
|**Yeniden değerlendirme:**|Kural ile kullanılacak kural yeniden değerlendirme türünü belirtir. Kullanılabilir seçenekler şunlardır:<br /><br /> -   **Her zaman**, gerektiği şekilde hesaplanması kural neden olur.<br />-   **Hiçbir zaman**, hiçbir zaman hesaplanması kural neden olur. Bu durumda bir kural yalnızca bir kez çalıştırır.|  
|**Etkin**|Kuralın etkin hale getirmek için bu seçeneği işaretleyin.|  
|**Koşul:**|Kural koşulu için bir ifade girin. İfade sözdizimi hakkında daha fazla bilgi için bu sayfanın "Girerek koşulu ve eylem Expressions" bölümüne bakın.|  
|**Ardından Eylemler:**|Then ifadesi girin eylemler. İfade sözdizimi hakkında daha fazla bilgi için bu sayfanın "Girerek koşulu ve eylem Expressions" bölümüne bakın.|  
|**Başka eylemler:**|Else eylemler için ifade girin. İfade sözdizimi hakkında daha fazla bilgi için bu sayfanın "Girerek koşulu ve eylem Expressions" bölümüne bakın.|  
|**TAMAM**|Kural kümesi .rules dosyasına kaydetmek için tıklatın.|  
  
 Kural kümeleri hakkında daha fazla bilgi için bkz. [PolicyActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65004).  
  
## <a name="entering-condition-and-action-expressions"></a>Koşul ve eylem ifadeleri girme  
 Koşul ve ardından için ifadeler girin ve bunların ilgili metnin eylemleri başka kutularındaki **kural kümesi Düzenleyicisi** iletişim kutusu. Yazabilirsiniz **bu.** alanlar, özellikler ve yöntemler iş akışı içinde kullanılan başvurmak için düzenleyicide yerleşik menünün bir IntelliSense türü kullanıyor. Veya doğrudan bir iş akışı üye adı yazın. Yöntem adından önce gelen sınıf adını yazarak başvurulan türleri üzerinde statik yöntemlerini çağırabilirsiniz.  
  
 Mantıksal işleçler AND, OR'gibi bir koşul ekleyebilirsiniz ve değil. Koşullar da ekleyebilirsiniz. Bir ikili işleç ve iki işlenenden koşuldur. Desteklenen ikili işleçler olan ==, >, \<, > =, ve < =. Desteklenen işlenenler şunlardır: sabit değer, aritmetik işlevi ve kapsamlı bir genel üyeler.  
  
 Karşılaştırma türü belirtebilir ve'karşılaştırabilirsiniz **null** ya da boş bir dize. Örneğin, bir karmaşık tür içeren bir değişkeni üyelerde çağrıları iç içe yerleştirebilirsiniz `this.Address.State == "WA"`.  
  
 İfadeler, aşağıdaki işleçleri destekler:  
  
- İlişkisel işleçleri: ==, =,! =  
  
- Karşılaştırma işleçleri: <, \<=, >, > =  
  
- Aritmetik işleçler: +, -, *, /, MOD  
  
- Mantıksal işleçler: ve, & &, OR &#124; &#124;değil,!  
  
- Bit düzeyinde işleçler: &,&#124;  
  
  İfadenin İşleç önceliği, C# İşleç önceliği kurallarını izler.  
  
  Koşullar hakkında daha fazla bilgi için bkz. [iş akışlarını kullanarak koşullarında](http://msdn.microsoft.com/en-us/541211f5-d382-4810-894f-71f00b34fa77).  
  
### <a name="halt-and-update-functions"></a>Durdurmak ve güncelleştirme işlevleri  
 **Ardından Eylemler:** ve **başka eylemler:** ifadeleri Destek **durdurmak** ve **güncelleştirme** işlevleri. Kullanılacak **durdurmak** işlev, yazın **durdurmak** içine bir **eylemi:** veya **başka eylem:** metin kutusu. **Durdurmak** eylem hemen durdurmak kural kümesi yürütmenin neden olur ve denetim için arama kodunu döndürür. Kullandığınız **güncelleştirme** İleri zincirleme ile işlevi.  
  
 Bir **güncelleştirme** deyimi ifade edilemez iki farklı bir düzenleyicide; her iki biçimi aşağıdaki örnekte gösterilmiştir:  
  
```  
Update(this.Address.State)  
Update("this/Address/State")  
```  
  
 Kullanma hakkında daha fazla bilgi için **güncelleştirme** ileriye doğru zincirleme bkz [PolicyActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65004).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [Select kuralı Ayarla iletişim kutusu (eski)](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [PolicyActivity etkinliğini kullanma](http://go.microsoft.com/fwlink?LinkID=65004)   
 [İş akışlarında koşullar kullanma](http://go.microsoft.com/fwlink?LinkID=65009)