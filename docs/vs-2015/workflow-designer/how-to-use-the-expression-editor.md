---
title: 'Nasıl yapılır: ifade düzenleyicisini kullanma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 0c41de63b4163f1fd259ffa4adcef63cad92e351
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49181726"
---
# <a name="how-to-use-the-expression-editor"></a>Nasıl yapılır: ifade düzenleyicisini kullanma
İfade Düzenleyicisi olduğu bir [!INCLUDE[wfd1](../includes/wfd1-md.md)] birçok iş akışı etkinliklerinde girme ve şu ifadeleri değerlendirme bir yol kullanılan bir denetim. İfade Düzenleyicisi düzenleme deneyimi, IntelliSense dahil olmak üzere tam özellikli bir IDE sağlar, renklendirme Paramınfo, diğer özellikler arasında hata ilişkilendirmelerini. Bunu girildikten sonra derleyici ifadesini doğrular. İfade geçersizse, bir hata simgesi görüntülenir. Düzenleyici olarak de açılabilir bir **ifade Düzenleyicisi** iletişim kutusu.  
  
 İfadelerdir değişmez değerler veya [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] kod bağlı bağımsız değişkenler veya özellikleri. Yeni bir değer yield işlemleriyle birlikte değeri öğeleri (örneğin değişkenleri, sabitleri, sabit değerleri, özellikleri) içerirler. İfadeler, C# kullanarak bir programda uygulaması olsa bile VB.NET söz dizimini kullanarak yazılır. Büyük/küçük harf önemli değildir, karşılaştırma kullanarak gerçekleştirilir yani tek bir eşittir ("=") işareti ("==") yerine, Boole işleçleri sözcüklerdir "ve" ve "veya" sembolleri yerine "& &" ve "&#124;&#124;", ve **hiçbir şey**  yerine kullanılan **null**. İfadeler ve işleçler hakkında daha fazla bilgi için [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ve bazı örnekler için bkz: [işleçler ve ifadeler Visual Basic'te](http://go.microsoft.com/fwlink/?LinkId=186818).  
  
 **İfade Düzenleyicisi** gibi davranır:  
  
-   Odağı ifade Düzenleyicisi üzerinde değilse, normal bir TextBlock denetimi gibi görünüyor.  
  
-   Odağı ifade düzenleyicisini olduktan sonra görünür ve ifade Düzenleyicisi denetimi gibi davranır. Odağı kaybettiğinde sonra BT normal bir TextBlock gibi tekrar görünür.  
  
-   Daha sonra yeniden barındırılan iş akışı Tasarımcısı'nda ifade Düzenleyicisi üzerinde odaklanmak, bir metin kutusu gibi davranır. Yeniden barındırılan iş akışı Tasarımcısı'nda odağı kaybettiğinde ifade Düzenleyicisi gibi normal bir TextBlock yeniden görünür.  
  
> [!NOTE]
>  IntelliSense için ifade Düzenleyicisi yalnızca içinde kullanılabilir [!INCLUDE[vs2010](../includes/vs2010-md.md)]. Hem de [!INCLUDE[vs2010](../includes/vs2010-md.md)] ve derleyici ifade girildiği sonra ifade geçersiz bir hata simgesi ifade düzenleyicisini görüntüler yeniden barındırılan senaryoları doğrular.  
  
### <a name="using-the-expression-editor"></a>İfade Düzenleyicisi kullanma  
  
1.  İçinde [!INCLUDE[vs2010](../includes/vs2010-md.md)], yeni veya var olan iş akışı projesi açın.  
  
2.  Ekleme, örneğin, <xref:System.Activities.Statements.Assign> etkinlik akışınıza.  
  
    > [!NOTE]
    >  Birden çok iş akışı etkinlikleri ifade düzenleyicileri vardır. İfade TextBlock'lar değişken tasarımcısını, bağımsız değişken tasarımcısını ve dinamik bağımsız değişken tasarımcısını da görünür. <xref:System.Activities.Statements.Assign> Etkinliği, örnek olarak kullanılır.  
  
3.  Sol ifade Düzenleyicisi için etkinlik Tasarımcısı'nda <xref:System.Activities.Statements.Assign> etkinlik.  
  
     Gri Filigran dizeleri  **\<için >** ve  **\<zadejte Výraz jazyka vb. >** varsayılan ifade Düzenleyicilerde metin dizelerini içindir <xref:System.Activities.Statements.Assign> etkinlik.  
  
4.  İfadeniz girin. Bir dize girin, dize etrafında tırnak işareti koymak emin olun. İfade bağımsız değişkeni bir değişkene bağlamak isterseniz, tırnak işaretleri bırakın.  
  
     İşiniz bittiğinde, bir bölge ya da alanı dışında ifade odağı tasarımcının başka bir parçası için Düzenleyici'yi seçin. Bu, daha önce açıklandığı şekilde ifadeyi doğrulamak derleyicinin neden olur.  
  
     Bir ifade girin/düzenlemek için alternatif bir yolu, özellik kılavuzunda özellik adının yanındaki üç noktaya tıklayın sağlamaktır. Bu açılır **ifade Düzenleyicisi** iletişim kutusu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Activities.Presentation.View.ExpressionTextBox>