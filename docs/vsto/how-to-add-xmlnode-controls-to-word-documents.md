---
title: 'Nasıl yapılır: Word belgelerine XMLNode denetimleri ekleme'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control, adding to documents
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bd0429374b175da3260c3605f39c90cf2dffb841
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544904"
---
# <a name="how-to-add-xmlnode-controls-to-word-documents"></a>Nasıl yapılır: Word belgelerine XMLNode denetimleri ekleme
  **Önemli** Microsoft Word ile ilgili bu konu başlığı altında verilen bilgiler, Microsoft Word 'deki özel XML ile ilgili belirli bir işlevselliğin uygulanmasını kaldırdıkları zaman, Birleşik Devletler ve bölgeleri dışında bulunan veya Microsoft tarafından Microsoft tarafından lisanslanan Microsoft Word ürünleri, Microsoft 'un Microsoft Word ile ilgili belirli işlevlerin bir uygulamasını kaldırdığınızda Microsoft 'un 2010 Ocak 'tan önce lisanslı olduğu kişiler ve kuruluşların avantajı ve kullanımı için özel olarak sunulur. Microsoft Word ile ilgili bu bilgiler, Birleşik Devletler veya şirket içinde çalışan ya da Microsoft tarafından, 10 Ocak 2010 ' den sonra Microsoft tarafından lisanslanan Microsoft Word ürünlerini kullanan bireyler veya kuruluşlar tarafından okunamaz veya kullanılmıyor olabilir. Bu ürünler, bu tarihten önce lisanslanan ürünlerle aynı veya satın alınmadan ve Birleşik Devletler dışında kullanılmak üzere lisanslanmaz.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Yinelenmeyen bir XML şeması öğesini bir Microsoft Office Word belgesiyle eşleştirdiğinizde, Visual Studio belgenize otomatik olarak bir <xref:Microsoft.Office.Tools.Word.XMLNode> denetim ekler. Yinelenen XML şeması öğelerini eşleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: Word belgelerine XMLNodes denetimleri ekleme](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md).

> [!NOTE]
> <xref:Microsoft.Office.Tools.Word.XMLNode>Denetim, **araç kutusu** veya **veri kaynakları** penceresinde kullanılamaz ve program aracılığıyla oluşturulamaz.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-an-xmlnode-control-to-a-document"></a>Belgeye bir XMLNode denetimi eklemek için

1. Visual Studio Tasarımcısı ' nın belgesinde, şeritte, **Geliştirici** sekmesine tıklayın.

    > [!NOTE]
    > **Geliştirici** sekmesi görünür değilse, önce onu göstermelisiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Şeritte Geliştirici sekmesini gösterme](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

2. **XML** grubunda, **şema**' ya tıklayın.

     **Şablonlar ve eklentiler** iletişim kutusu açılır.

3. **XML şeması** sekmesine tıklayın.

4. **Şema ekle**' ye tıklayın.

     **Şema ekle** iletişim kutusu açılır.

5. **Şema ekle** iletişim kutusundan tekrarlamayan şema öğelerini IÇEREN bir XML şeması seçin ve **Aç**' a tıklayın.

     **Şema ayarları** iletişim kutusu görüntülenir.

6. Bir diğer ad atayın veya şemayı bir diğer ad olmadan eklemek için **Tamam 'a** tıklayın.

     Şema, **şema ekle** iletişim kutusuna eklenir.

7. **Şema ekle** Iletişim kutusunda **Tamam**' a tıklayın.

8. **XML yapısı** görev bölmesi açılır.

9. **XML yapısı** görev bölmesindeki tekrarlamayan şema öğesine tıklayarak belgeyi belgeye ekleyin.

     Bir <xref:Microsoft.Office.Tools.Word.XMLNode> Denetim oluşturulup projeye eklenir.

## <a name="see-also"></a>Ayrıca bkz.
- [XMLNode denetimi](../vsto/xmlnode-control.md)
- [Genişletilmiş nesneleri kullanarak Word 'Ü otomatikleştirme](../vsto/automating-word-by-using-extended-objects.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
