---
title: 'Nasıl yapılır: TableAdapter sorguları oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- TableAdapters, creating queries
- queries [Visual Studio], creating
- data [Visual Studio], TableAdapter queries
- queries [Visual Studio], TableAdapters
ms.assetid: df0cf4a5-e9cc-4de6-8b94-ce74fb7b2452
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: c4b800bcb70e41e1d80bf9a0a37d72f08f78c7a6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49195552"
---
# <a name="how-to-create-tableadapter-queries"></a>Nasıl Yapılır: TableAdapter Sorguları Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

TableAdapter sorguları SQL deyimleri ya da uygulamanızı bir veritabanına karşı çalıştırabilirsiniz saklı yordamlar ' dir.  
  
 Bir TableAdapter için uygulamanızın gerektirdiği sayıda sorgu ekleyin. TableAdapter sorguları bir TableAdapter yöntemleri olarak görünür. Adlı bir sorgu oluşturduğunuzda `FillByCity` , şehir değeri temsil eden bir parametre alır, sorgu Tableadapter'a eklenir. Doğru türde parametre bağımsız değişken olarak alan türü belirtilmiş bir metot olarak eklenir; bu durumda Şehir değeri temsil eden bir dize. TableAdapter sorgusu herhangi bir yöntemi gibi herhangi bir nesne çağırırsınız. Örneğin, aşağıdaki kodu çalıştırır `FillByCity` sorgu ve dolguları `Customers` Şehir değeri olan tüm müşterileri tabloyla `Seattle`:  
  
 [!code-csharp[VbRaddataTableAdapters#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Form1.cs#1)]
 [!code-vb[VbRaddataTableAdapters#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Form1.vb#1)]  
  
 Veri tablosunu TableAdapter sorguları doldurabileceğiniz (`Fill` ve `FillBy` sorguları) veya sorgu tarafından döndürülen verilerle doldurulmuş yeni veri tabloları döndürmek (`GetData` ve `GetDataBy` sorguları).  
  
 Çalıştırarak için varolan TableAdapter sorguları ekleyebilirsiniz [TableAdapters düzenleme](../data-tools/editing-tableadapters.md). (Herhangi bir TableAdapter'ı sağ tıklatın ve seçin **Sorgu Ekle**.)  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="create-a-query-in-the-dataset-designer"></a>Veri kümesi Tasarımcısı'nda bir sorgu oluşturun  
  
#### <a name="to-add-a-query-to-a-tableadapter-in-the-dataset-designer"></a>Veri kümesi Tasarımcısı'nda TableAdapter bir sorgu eklemek için  
  
1.  Bir veri kümesini açın **veri kümesi Tasarımcısı**. Daha fazla bilgi için [nasıl yapılır: bir veri kümesini veri kümesi Tasarımcısı'nda açma](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  İstenen TableAdapter'ı sağ tıklatın ve seçin **Sorgu Ekle**.  
  
     veya  
  
3.  Sürükleme bir **sorgu** gelen **veri kümesi** sekmesinde **araç kutusu** Tablo Tasarımcısı'ndaki üzerine.  
  
     **TableAdapter sorgu Yapılandırma Sihirbazı'nı** açılır.  
  
4.  Sihirbazı tamamlayın; TableAdapter sorgu eklenir.  
  
## <a name="create-a-query-directly-on-a-form-in-your-windows-application"></a>Windows uygulamanızda bir Form üzerinde doğrudan bir sorgu oluşturun.  
 Formunuzdaki bir TableAdapter örneği varsa kullanarak bir sorgu ekleyebilirsiniz [arama ölçütleri derleyici iletişim kutusu](http://msdn.microsoft.com/library/0b306b92-f35e-45ef-a4be-3f653cd00c3d), hangi ekler bir <xref:System.Windows.Forms.ToolStrip> kabul eden herhangi bir giriş sorgu için gerekli parametreleri forma yanı sıra bir Sorguyu çalıştırmak için düğme.  
  
#### <a name="to-add-a-query-to-a-tableadapter-using-the-search-criteria-dialog-box"></a>Arama ölçütleri iletişim kutusunu kullanarak bir TableAdapter için bir sorgu ekleme  
  
1.  Bir TableAdapter bileşen tepsisinde seçin.  
  
2.  TableAdapter bağdaştırıcısının akıllı etiket tıklatın ve seçin **Sorgu Ekle**.  
  
3.  İletişim kutusunu doldurun ve TableAdapter sorgu eklenir. Daha fazla bilgi için [arama ölçütleri derleyici iletişim kutusu](http://msdn.microsoft.com/library/0b306b92-f35e-45ef-a4be-3f653cd00c3d).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TableAdapter genel bakış](../data-tools/tableadapter-overview.md)   
 [Nasıl yapılır: TableAdapter sorgularını düzenleme](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Türü belirtilmiş veri kümeleri oluşturma ve düzenleme](../data-tools/creating-and-editing-typed-datasets.md)   
 [Yeni veri kaynağı ekleme](../data-tools/add-new-data-sources.md)   
 [Nasıl yapılır: bir veritabanındaki verilere bağlanma](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Verileri doğrulama](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Nasıl yapılır: Windows Forms BindingNavigator denetimi ile verilerde gezinme](http://msdn.microsoft.com/library/0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb)   
 [İzlenecek yol: Bir Windows formunda veri görüntüleme](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [İzlenecek yol: bir TableAdapter ile birden çok sorgu oluşturma](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)