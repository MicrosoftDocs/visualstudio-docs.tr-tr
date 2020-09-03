---
title: .NET türü Iletişim kutusuna gözatıp seçin | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- TypeBrowser.UI
- ActivityTypeResolver.UI
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 922be22619ee0bd16e2e5ac563999be7db81d45e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851431"
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>.NET Türüne Gözat ve Seç İletişim Kutusu
**Türler Için araştır** ' ı seçtiğinizde, **Özellikler** penceresi, iletişim kutuları veya değişken Tasarımcısı gibi tasarımcılar... veri türleri listesinden **bir .NET türü** (kısaltılmış bir biçimde "tür tarayıcısı" olarak adlandırılır) görüntülenir ve seçin. Bu iletişim kutusunda, derlemelerin ve projelerin ağaç görünümünden bir tür seçebilirsiniz.

 Bu iletişim kutusu, aşağıdakiler de dahil olmak üzere çeşitli Kullanıcı senaryolarında işe alındı:

- Bir değişkenin veya bağımsız değişkenin türü ayarlanırken.

- Genel etkinlik için bir tür seçerken.

- Etkinliğe bir catch eklenirken <xref:System.Activities.Statements.TryCatch> .

> [!NOTE]
> Tür tarayıcısı Visual Basic basit dizi türleri görüntüleyebilir, ancak çok boyutlu dizi türleri gösterebilir. Ayrıntılar için bkz. [pürüzlü Diziler](https://msdn.microsoft.com/library/hkhhsz9t(VS.90).aspx) ve [çok boyutlu diziler](https://msdn.microsoft.com/library/d2de1t93(VS.90).aspx) .

## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>Tür tarayıcısından bir değer veya başvuru türü seçme

#### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>Tür tarayıcısından bir değer veya başvuru türü seçmek için

1. **Tür adı** kutusuna, kullanmak istediğiniz türün adını girin.

2. Şunlardan birini yapın:

    - Kullanmak istediğiniz türün adı, **tür adı** kutusundaki ağaçta göründüğünde, seçmek için türe çift tıklayın.

    - Kullanmak istediğiniz türü benzersiz bir şekilde tanımlamak için **tür adı** kutusuna yeterli sayıda karakter yazın ve ardından türü seçmek için ENTER tuşuna basın

#### <a name="to-select-a-generic-type-from-the-type-browser"></a>Tür tarayıcısından genel bir tür seçmek için

1. **Tür adı** kutusuna, kullanmak istediğiniz türün adını yazın.

2. Kullanmak istediğiniz türün adı **tür adı** kutusundaki ağaçta göründüğünde, açılan kutuların görünmesine neden olacak şekilde seçmek için türe tıklayın.

     Açılan kutulardan genel ' i kapatmak için kullanmak istediğiniz türü seçin ve ardından **Tamam**' a tıklayın.

## <a name="types-displayed-in-the-type-browser"></a>Tür tarayıcısında görünen türler
 Tür tarayıcısında görünen türler, tür tarayıcısının nasıl başlatıldığına bağlı olarak farklılık gösterebilir. Tür tarayıcısı **VS2010**içindeki bir iş akışı projesinden başlatılmışsa, varsayılan olarak başvurulan derlemelerdeki tüm türler ve başvurulan projeler gösterilir. Tür tarayıcısı bir **VS2010** projesi sisteminin dışından (örneğin, yeniden barındırılan bir iş akışı uygulamasında veya tek başına bir iş akışı dosyasında) başlatılmışsa, varsayılan olarak, uygulama etki alanında yüklü derlemelerin tümünün türleri gösterilir.

 Tür tarayıcısındaki türler, etkinlik Tasarımcısı geliştiricilerine göre filtrelenebilir. Belirli bir etkinlik için yalnızca türlerin bir alt kümesini görebilirsiniz. Örneğin, <xref:System.Activities.Statements.TryCatch> etkinliğinde, türü tarayıcıda yalnızca öğesinden türetilmiş türler <xref:System.Exception> gösterilir.

## <a name="filtering-search-results-in-the-type-browser"></a>Arama sonuçlarını tür tarayıcısında filtreleme
 **Tür adı** kutusundaki türlerin listesi, bir eşleşme bulmak için daha fazla karakter yazdığınızda daha kısa olur. Yalnızca tam adı yazdığınız dize ile başlayan türler veya kısa adı yazdığınız dize ile başlayan ve filtrelenmiş listede görünen türler.

 Örneğin:

1. Yazma **işlemi** eşleşiyor <xref:System.OperationCanceledException> ancak eşleşmiyor <xref:System.InvalidOperationException> . Eşleştirmek için <xref:System.InvalidOperationException> , System. ı veya geçersiz yazmaya başlayın.

2. **Genel** eşleşmeler yazma <xref:System.GenericUriParser> , ancak <xref:System.Collections.Generic> ad alanındaki türler değil. Ad alanındaki türleri aramak için <xref:System.Collections.Generic> ad alanının tam adını yazın.

## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>Tarayıcı türü iletişim kutusunu kullanarak bir hizmet sözleşmesi seçme
 Bir hizmet sözleşmesi türü seçerken tür tarayıcısı yalnızca özniteliği olan türleri gösterir <xref:System.ServiceModel.ServiceContractAttribute> .

## <a name="see-also"></a>Ayrıca Bkz.
 [Etkinlik Tasarımcılarını kullanma](../workflow-designer/using-the-activity-designers.md)
