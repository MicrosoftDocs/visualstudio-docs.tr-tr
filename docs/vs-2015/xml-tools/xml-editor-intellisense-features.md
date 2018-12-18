---
title: XML Düzenleyicisi IntelliSense özellikleri | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b26f214-cc3a-46bf-b260-14eb8e599182
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4dbb96ffcca47303a90b1ff4c71643a63f6b4aa5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49830751"
---
# <a name="xml-editor-intellisense-features"></a>XML Düzenleyicisi IntelliSense Özellikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
XML Düzenleyicisi Visual Studio'da sağlanan diğer dil düzenleyicilere karşılaştırılabilir tam IntelliSense özelliklerini sağlar. Bu bölümde, XSLT belgeleri ve XML Şeması Tanım Dili (XSD) ile IntelliSense nasıl kullanabileceğiniz açıklanmaktadır.  
  
## <a name="intellisense-in-an-xsd-document"></a>Bir XSD belgesi IntelliSense  
 Bir şema, belge ile ilişkili olduğunda, yazdığınız dilediğiniz zaman beklenen öğeleri açılan listesini alma `"<"` veya **bir nesne üye listesini görüntüle** XML Düzenleyicisi araç çubuğunda. Şemaları XML belgelerinizi ile ilişkilendirme hakkında daha fazla bilgi için bkz: [XML belgesi doğrulama](../xml-tools/xml-document-validation.md).  
  
 Bir başlangıç etiketi içinde ALANINDAN yazdığınızda, ayrıca geçerli öğeye eklediğiniz tüm öznitelikler gösteren bir açılan listesini alın.  
  
 Yazdığınızda `"="` bir öznitelik değeri veya tırnak değeri için siz de bu öznitelik için olası değerler listesini alın. Değerleri yalnızca şema aracılığıyla numaralandırılmış değerlerden sağlıyorsa sağlanan `xsd:enumeration` modelleri, veya öznitelik ise bir `Boolean` türü. Bilinen dil kodlarının bir IntelliSense listesini de için sağlanan `xml:lang` veya tüm `simpleType` türetilen `xsd:language`. Bilinen bir IntelliSense listesini `targetNamespace` değerleri için ad alanı bildirimi sağlanır.  
  
 Olası değerler bir IntelliSense listesini de yazarken sağlanan `">"` öğesi ise bir başlangıç etiketi kapatmak için bir `simpleType`. Benzer şekilde önceki paragrafta açıklanan öznitelikleri davranışını öğeler için davranıştır.  
  
 Araç ipuçları da görünür göre bu IntelliSense listelerde `xsd:annotation` ve `xsd:documentation` ilişkili şemasında bilgi bulunamadı.  
  
## <a name="intellisense-in-an-xslt-document"></a>XSLT belge Intellisense'te  
 Adlandırılmış bir şablon ya da bir öznitelik XSLT belgenize ekledikten sonra aşağıdaki eklemek için IntelliSense kullanabilirsiniz:  
  
- Öznitelik adları ayarlayın.  
  
- Şablon mod.  
  
- Şablon adları.  
  
- Belirli bir mod için parametre adları.  
  
- Belirtilen adlandırılmış bir şablon parametresi adları.  
  
  Daha fazla bilgi için [izlenecek yol: XSLT IntelliSense kullanarak](../xml-tools/walkthrough-using-xslt-intellisense.md) konu.  
  
## <a name="auto-completion"></a>Otomatik Tamamlama  
 XML Düzenleyicisi'ni de gerekli XML sözdiziminde doldurarak daha kolay XML düzenleme olmasını sağlar. Örneğin aşağıdaki başlangıç etiketi yazın:  
  
 `<book>`  
  
 XML Düzenleyicisi'ni bitiş etiketinde doldurur ve imleci sonra başlangıç etiketi yerleştirir. Buna örnek olarak verilmiştir ("&#124;" imleç konumu notları):  
  
 `<book>`&#124;`</book>`  
  
 Öznitelik değerlerine tırnak her zaman sahip olmanız gerektiğinden, XML Düzenleyicisi'ni tırnak doldurur. Örneğin, aşağıdaki komutu yazın:  
  
 `<book title=`  
  
 XML Düzenleyicisi'ni tırnak ekler ve tırnak işaretleri arasında imleci geçir yerleştirir:  
  
 `<book title="`&#124;`"`  
  
 Benzer şekilde, XML Düzenleyicisi'ni de aşağıdaki XML sözdizimini otomatik olarak ekler:  
  
- Son bir işlem yönergesi:  `?>`  
  
- [[CDATA bloğunun sonu: `]]>`  
  
- Bir açıklama sonu: `-->`  
  
- Son DTD bildirimi: `>`  
  
  XML Düzenleyicisi'ni bir ad alanı Ekle özelliğine de sahiptir bildirimi bir ad alanı tam öğesi seçin veya bir IntelliSense listesi ve bu öğe veya öznitelik için ad alanı özniteliği henüz kapsam içinde değil.  
  
  Örneğin, `e:Book` nerede bağlı öneki için IntelliSense listesinden öğe `http://books` XML Düzenleyicisi'ni ekler, gerekli ad alanı bildirimi belge içinde bildirilmedi ad alanı. Sonuçta elde edilen XML metni aşağıda verilmiştir:  
  
  `<e:Book xmlns:e="http://books"`  
  
## <a name="brace-matching"></a>Ayraç eşleştirme  
 XML Düzenleyicisi'ni küme parantezi vurgulama kapalı öğelerde size anında geri bildirim sağlar. Klavye kısayolu (CTRL +]), bir küme ayracı eşleşen Ayraca atlamak için de kullanabilirsiniz.  
  
 XML Düzenleyicisi bu için aşağıdakileri yapar:  
  
-   Başlangıç ve bitiş etiketleri eşleşen.  
  
-   Bir çift "\<" veya ">" açılı ayraçlar.  
  
-   Başlangıç ve bitiş açıklama.  
  
-   Başlangıç ve bitiş işleme yönergeleri.  
  
-   Başlangıç ve bitiş CDATA bloğu.  
  
-   Başlangıç ve bitiş DTD'nin bildirimlerinin.  
  
-   Açma ve özniteliklerde tırnak kapatma.  
  
## <a name="modifying-the-intellisense-options"></a>IntelliSense seçenekleri değiştirme  
 IntelliSense ve otomatik tamamlama özellikleri varsayılan olarak etkindir. Ancak, bu Araçlar-Seçenekler ayarlarınızı değiştirerek değiştirebilirsiniz.  
  
 **Otomatik ekleme** bölümünü **çeşitli** sayfa aşağıdaki davranışı denetler:  
  
|Ad|Açıklama|  
|----------|-----------------|  
|Kapatma etiketleri|Yeni öğeler için etiketleri ekler kapatın.|  
|Öznitelik tırnak işaretleri|Yeni bir öznitelik adı girin, öznitelik değer tırnakları ekler.|  
|Diğer biçimlendirme|Açıklamalar, CDATA, DOCTYPE, işleme yönergeleri ve diğer işaretleme bildirimlerinde tamamlar.|  
  
#### <a name="to-change-the-auto-completion-behavior"></a>Otomatik Tamamlama davranışını değiştirmek için  
  
1.  Seçin **seçenekleri** gelen **Araçları** menüsü.  
  
2.  Genişletin **metin düzenleyici**, genişletme **XML**seçip **çeşitli**.  
  
3.  Değişiklik **otomatik Ekle** tıklayın ve bölüm **Tamam**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Düzenleyicisi](../xml-tools/xml-editor.md)   
 [IntelliSense kullanma](../ide/using-intellisense.md)   
 [İzlenecek Yol: XSLT IntelliSense Kullanma](../xml-tools/walkthrough-using-xslt-intellisense.md)



