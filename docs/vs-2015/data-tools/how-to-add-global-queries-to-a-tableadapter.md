---
title: 'Nasıl yapılır: bir TableAdapter veritabanına genel sorgular ekleme | Microsoft Docs'
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
- global functions, datasets
- scalar functions, datasets
- TableAdapters, global queries
- data [Visual Studio], TableAdapters
- datasets [Visual Basic], scalar functions
- TableAdapter Query Configuration Wizard
- datasets [Visual Basic], global functions
- TableAdapter queries
- queries [Visual Studio], TableAdapters
ms.assetid: 4abffd6b-2e9f-4ef3-99b2-6e9ae4ad4679
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: fd185c9a6803a5e66b1fdaac0f040815328ddb82
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49193901"
---
# <a name="how-to-add-global-queries-to-a-tableadapter"></a>Nasıl yapılır: bir TableAdapter veritabanına genel sorgular ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Genel sorgular* tek bir (sayı) değerini veya herhangi bir değer döndüren SQL sorguları. Genellikle, genel işlevler ekler, güncelleştirmeler, siler ve bir tablo ya da belirli bir sırada tüm öğeler için Toplam ücret müşterilerin sayısını döndüren gibi bilgi toplama gibi veritabanı işlemlerini gerçekleştirir.  
  
 Genel sorgular çalıştırarak eklemek **TableAdapter sorgu Yapılandırma Sihirbazı'nı** içinden **veri kümesi Tasarımcısı**.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-global-query-to-a-dataset"></a>Bir veri kümesi için genel bir sorgu eklemek için  
  
1.  Bir veri kümesini açın **veri kümesi Tasarımcısı**. Daha fazla bilgi için [nasıl yapılır: bir veri kümesini veri kümesi Tasarımcısı'nda açma](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Sürükleme bir **sorgu** gelen **veri kümesi** sekmesinde **araç kutusu** boş bir alanı üzerine **veri kümesi Tasarımcısı**.  
  
     [TableAdapters düzenleme](../data-tools/editing-tableadapters.md) açılır.  
  
3.  Bir bağlantı için kullanılacak sorguyu seçin. Listeden birini seçin veya yeni bir bağlantı oluşturun. Yeni bir bağlantı oluşturmak, uygulama yapılandırma dosyasına kaydetmek için seçeneğine sahip olursunuz. Daha fazla bilgi için [nasıl yapılır: Kaydet ve bağlantı dizeleri düzenleme](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md).  
  
4.  SQL deyimlerinin veya saklı yordamların kullanmak isteyip istemediğinizi seçin.  
  
5.  Kullanmak için saklı yordam seçin veya **bir sorgu türü seçin** sayfasında sihirbazın istediğiniz ve ardından sorgu türünü seçin **sonraki**.  
  
6.  Örneğin, istenen bir görevi gerçekleştiren bir sorgu sağlamanız `SELECT COUNT(*) AS CustomerCount FROM Customers`.  
  
    > [!NOTE]
    >  Bir sorgu doğrudan üzerine sürükleyerek **veri kümesi Tasarımcısı** yalnızca bir skaler (tek) değer döndürür bir metot oluşturur. Sorgu veya saklı yordam seçtiğiniz birden çok tek bir değer döndürebilir sırasında sihirbaz tarafından oluşturulan yöntemi yalnızca tek bir değer döndürür. Örneğin, sorgu döndürülen verileri ilk satırının ilk sütununu döndürebilir.  
  
7.  Sihirbazı tamamlayın; Sorgu eklenir **veri kümesi Tasarımcısı**. Sorgu çalıştırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: TableAdapter sorgularını yürütme](http://msdn.microsoft.com/library/c7518855-f896-41c1-b3de-1a8116280593).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tableadapter'lar oluşturma ve yapılandırma](../data-tools/create-and-configure-tableadapters.md)   
 [Nasıl yapılır: TableAdapter sorguları oluşturma](../data-tools/how-to-create-tableadapter-queries.md)   
 [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [TableAdapter genel bakış](../data-tools/tableadapter-overview.md)   
 [Türü belirtilmiş veri kümeleri oluşturma ve düzenleme](../data-tools/creating-and-editing-typed-datasets.md)   
 [Yeni veri kaynağı ekleme](../data-tools/add-new-data-sources.md)   
 [Nasıl yapılır: bir veritabanındaki verilere bağlanma](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Verileri doğrulama](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Nasıl yapılır: Windows Forms BindingNavigator denetimi ile verilerde gezinme](http://msdn.microsoft.com/library/0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb)   
 [İzlenecek yol: Bir Windows formunda veri görüntüleme](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)