---
title: İş Akışı Tasarımcısı - göz atın ve bir .NET türünü seç iletişim kutusu
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- TypeBrowser.UI
- ActivityTypeResolver.UI
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 686969c233f50dd1df743590206966183be48da9
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39513204"
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>.NET Türüne Gözat ve Seç İletişim Kutusu

İçinde **özellikleri** pencere, iletişim kutuları ve tasarımcıları gibi değişken tasarımcısını seçtiğinizde, **vyhledat Typy** veri türleri bir listede olan **göz atın ve bir .NET türüseçin** iletişim kutusu (kısaltılmış biçimdeki "türü tarayıcı" olarak adlandırılır). Bu iletişim kutusunda, derlemeleri ve projeleri bir ağaç görünümünden bir türü seçebilirsiniz.

Bu iletişim kutusu, kullanıcı senaryoları, aşağıdakiler dahil olmak üzere bir dizi içinde kullanılır:

-   Bir değişken veya bağımsız değişken türü ayarlarken.

-   Genel etkinlik için bir türü seçerken.

-   Bir catch eklenirken <xref:System.Activities.Statements.TryCatch> etkinlik.

> [!NOTE]
> Tür tarayıcı olmayan çok boyutlu dizi türleri, ancak Visual Basic Basit dizi türlerini görüntüleyebilirsiniz. Bkz: [basit diziler](http://go.microsoft.com/fwlink/?LinkId=195226) ve [çok boyutlu diziler](http://go.microsoft.com/fwlink/?LinkId=195227) Ayrıntılar için.

## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>Bir değer veya başvuru türü tür tarayıcısından seçme

### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>Bir değer veya başvuru türü tür tarayıcısından seçin

1.  İçinde **tür adı** kutusunda, kullanmak istediğiniz türün adını girin.

2.  Aşağıdakilerden birini yapın:

    -   Kullanmak istediğiniz türün adını ağaçta göründüğünde **tür adı** kutusunda, seçmek için türü'ne çift tıklayın.

    -   Yeterli karakterler girdiğinizde, bu **tür adı** türünü seçmek için ENTER tuşuna basın ve kullanmak istediğiniz türü benzersiz olarak tanımlanabilmesi için kutusu

### <a name="to-select-a-generic-type-from-the-type-browser"></a>Genel tür tür tarayıcısından seçmek için

1.  İçinde **tür adı** kutusunda, kullanmak istediğiniz tür adını yazın.

2.  Kullanmak istediğiniz türün adını ağaçta göründüğünde **tür adı** kutusunda, açılır kutuları neden seçmek için türü görünür tıklatın.

     Açılan kutu genel kapatın ve ardından kullanmak istediğiniz türü seçin **Tamam**.

## <a name="types-displayed-in-the-type-browser"></a>Tür tarayıcıda görüntülenen türleri

Tür tarayıcıda görüntülenen türleri türü tarayıcı nasıl başlatıldı bağlı olarak değişebilir. Tür tarayıcı içinde bir iş akışı projeden başlatıldı, **vs2010**, tüm bütünleştirilmiş kodlardaki türleri varsayılan olarak ve başvurulan projeler gösterilir. Tarayıcı Türü alanından dışında başlatıldıysa bir **vs2010** proje sistemine (Bu tür bir yeniden barındırılan iş akışı uygulaması olduğu gibi veya tek başına bir iş akışı dosyası), sonra tüm derleme AppDomain'e türleri varsayılan olarak gösterilir .

Tür tarayıcı türleri, etkinlik Tasarımcısı geliştiriciler tarafından filtrelenebilir. Verilen herhangi bir etkinlik için yalnızca bir alt türleri görebilirsiniz. Örneğin, <xref:System.Activities.Statements.TryCatch> etkinliği yalnızca türler türetilen <xref:System.Exception> türü tarayıcıda görüntülenir.

## <a name="filtering-search-results-in-the-type-browser"></a>Türü tarayıcı arama sonuçlarını filtreleme

Türleri listesini **tür adı** kutusu daha kısa bir eşleştirme bulmak üzere daha fazla karakter türü olarak alır. Yalnızca fullyqualified adı yazdığınız dize ile başlayan türleri veya kısa adı yazdığınız dize ile başlayan türleri filtrelenen listede görünür.

Örneğin:

1.  Yazarak **işlemi** eşleşen <xref:System.OperationCanceledException> ama <xref:System.InvalidOperationException>. Eşleştirilecek <xref:System.InvalidOperationException>, System.I ya da geçersiz yazmaya başlayın.

2.  Yazarak **genel** eşleşen <xref:System.GenericUriParser> ancak türlerini değil <xref:System.Collections.Generic> ad alanı. Türler için aranacak <xref:System.Collections.Generic> ad alanı, ad alanının tam adını yazın.

## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>Tür Tarayıcı iletişim kutusunu kullanarak bir hizmet sözleşmesini seçme

Bir hizmet sözleşme türünü seçerken, türü tarayıcı türleri yalnızca gösterir. <xref:System.ServiceModel.ServiceContractAttribute> özniteliği.

## <a name="see-also"></a>Ayrıca bkz.

- [Etkinlik Tasarımcılarını kullanma](../workflow-designer/using-the-activity-designers.md)