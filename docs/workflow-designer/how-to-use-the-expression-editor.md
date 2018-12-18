---
title: "İş Akışı Tasarımcısı - nasıl yapılır: ifade Düzenleyicisi'ni kullanın"
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c1f2ab9cad6f54b8d1106fd68eb017434cf5cfef
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756150"
---
# <a name="how-to-use-the-expression-editor"></a>Nasıl yapılır: ifade Düzenleyicisi'ni kullanın

Birçok iş akışı etkinlikleri girin ve ifadeler değerlendirmek için kullanılan bir iş akışı Tasarımcısı denetimi ifade düzenleyicisidir. İfade Düzenleyicisi düzenleme deneyimi, dahil olmak üzere IntelliSense renklendirme, tam özellikli bir IDE sağlar Paramınfo, diğer özellikler arasında hata dalgalı çizgiler. Bunu girildikten sonra derleyici ifade doğrular. İfade geçersiz ise, bir hata simgesi görüntülenir. Düzenleyici olarak da açılabilir bir **ifade Düzenleyicisi** iletişim kutusu.

Değişmez değerler veya Visual Basic kodu bağımsız değişken veya özellikler bağlı ifadelerini olun. Yeni bir değer verim işlemleriyle birlikte olan değer öğeleri (örneğin, değişkenlerinin, sabitleri, değişmez değerleri, özellikleri) içerir. İfadeler, uygulama C# kullanarak bir programda olsa bile VB.NET sözdizimi kullanılarak yazılır. Bunun anlamı büyük/küçük harf önemli değildir, karşılaştırma tek eşittir kullanarak gerçekleştirilir oturum ("=" "== yerine"), Boole işleçleri sözcüklerdir "ve" ve "veya" simgeleri yerine "& &" ve "||", ve **hiçbir şey** kullanılır yerine **null**. İfadeleri ve Visual Basic'de işleçler hakkında daha fazla bilgi ve bazı örnekler için bkz: [işleçler ve ifadeler Visual Basic'te](/previous-versions/visualstudio/visual-studio-2010/a1w3te48(v=vs.100)).

**İfade Düzenleyicisi** gibi davranır:

- Odağı ifade Düzenleyicisi üzerinde değilse, normal bir TextBlock denetimi gibi görünüyor.

- Odağı ifade Düzenleyicisi olduğunda arar ve ifade Düzenleyicisi denetimi gibi davranır. Odağı kaybettiğinde ifade Düzenleyicisi gibi normal TextBlock yeniden arar.

- Ardından üzerinde ifade Düzenleyicisi rehosted iş akışı Tasarımcısı'nda odaklanmanıza, metin kutusu gibi davranır. Odak rehosted iş akışı Tasarımcısı'nda kesildiğinde ifade Düzenleyicisi gibi normal TextBlock yeniden arar.

> [!NOTE]
> IntelliSense ifade Düzenleyicisi için yalnızca Visual Studio içinde kullanılabilir. Visual Studio hem rehosted senaryoları derleyici ifade girildiği ve ifade geçersiz ifade Düzenleyicisi hata simgesi görüntüler sonra doğrular.

## <a name="use-the-expression-editor"></a>İfade Düzenleyicisi'ni kullanın

1.  Visual Studio'da yeni veya var olan iş akışı projesini açın.

2.  Ekleme, örneğin, <xref:System.Activities.Statements.Assign> , iş akışı için etkinlik.

    > [!NOTE]
    > Birden çok iş akışı etkinlikleri ifade düzenleyicileri vardır. İfade TextBlock'lar değişken Tasarımcısı, bağımsız değişken Tasarımcısı ve dinamik bağımsız değişkeni Tasarımcısı'nı da görünür. <xref:System.Activities.Statements.Assign> Etkinlik, bir örnek olarak kullanılır.

3.  Sol ifade Düzenleyicisi için etkinlik Tasarımcısı'nda <xref:System.Activities.Statements.Assign> etkinlik.

     Gri filigranı dizelerden  **\<için >** ve  **\<bir VB ifadesi girin >** varsayılan ifade Düzenleyicilerde metin dizelerini içindir <xref:System.Activities.Statements.Assign> etkinlik.

4.  İfadeniz girin. Bir dize girin, dize etrafında tırnak işareti koymak emin olun. İfade bağımsız değişkeni bir değişkene bağlamak seçerseniz, iş tırnak işaretleri devre dışı bırakın.

     İşiniz bittiğinde, bir bölge veya alanı dışında ifade Tasarımcısı'nın başka bir bölümüne odağı kaydırılacak Düzenleyicisi'ni seçin. Odağı kaydırma ifade daha önce açıklandığı şekilde doğrulamak derleyici neden olur.

     Alternatif bir yol girin veya bir ifade düzenlemek için özellik kılavuzunda özellik adının yanındaki üç nokta düğmesine olmaktır. Üç nokta seçerek açılır **ifade Düzenleyicisi** bir iletişim kutusu olarak.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.Presentation.View.ExpressionTextBox>