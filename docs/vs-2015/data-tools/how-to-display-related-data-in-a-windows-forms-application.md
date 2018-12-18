---
title: 'Nasıl yapılır: görüntü ilgili verileri bir Windows Forms uygulamalarındaki | Microsoft Docs'
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
- Windows Forms, displaying data
- displaying data, related data
- related data, displaying
- displaying tables, related data
- data [Windows Forms], displaying
- displaying table data
- data [Windows Forms], related
- displaying data on forms, related data
- displaying table information
ms.assetid: 60b1f1ec-6257-42ab-83f0-06d54ed364fd
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 3fd7a29e1de66a5b5fd57dab1adbcf99128001ac
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49215468"
---
# <a name="how-to-display-related-data-in-a-windows-forms-application"></a>Nasıl Yapılır: Windows Forms Uygulamalarındaki İlgili Verileri Görüntüleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aynı ana tablo düğümünden paylaşma öğeleri sürükleyerek, ilgili verileri görüntüleyebilirsiniz [veri kaynakları penceresi](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) formunuza. Örneğin, bir veri kaynağı varsa sahip bir `Customers` tablo ve ilgili `Orders` tablo gördüğünüz her iki tablonun en üst düzey düğüm (ağaç görünümünde) içinde **veri kaynakları** penceresi. Genişletin `Customers` düğüm sütunları görebilirsiniz ve son sütun listesinde genişletilebilir bir düğüm olduğunu fark edeceksiniz temsil eden `Orders` tablo. Bu düğüm, bir müşterinin ilgili siparişlerini temsil eder. Bu, bir müşteri seçin ve ardından o müşteriye ait siparişlerin bir listesini görüntülemek izin veren bir form oluşturmak istiyorsanız, tek bu hiyerarşisinden görüntülemek istediğiniz öğeleri sürükleyin anlamına gelir.  
  
 ![Veri kaynakları penceresi ilişkisini gösteren](../data-tools/media/datasources2.gif "DataSources2")  
İlişkili kayıtları görüntüleyecek verilere bağlı denetimler oluşturma  
  
 ![video bağlantısı](../data-tools/media/playvideo.gif "PlayVideo") bu konunun video sürümü için bkz: [bunu nasıl yaparım güncelleştirme ilgili tabloları](http://go.microsoft.com/fwlink/?LinkId=143527).  
  
### <a name="to-create-controls-that-display-related-records"></a>İlişkili kayıtları görüntüleyecek denetimler oluşturmak için  
  
1.  Formunuzda açın [Windows Form Tasarımcısı](http://msdn.microsoft.com/en-us/3c3d61f8-f36c-4d41-b9c3-398376fabb15).  
  
2.  Açık **veri kaynakları** penceresi. Daha fazla bilgi için [nasıl yapılır: Veri Kaynakları penceresini açma](../data-tools/how-to-open-the-data-sources-window.md).  
  
3.  Üst tablo ilişkisinde temsil eden düğümünü genişletin. (Üst tablonun "bir" bir-çok ilişkisi tarafındaki tablodur.)  
  
4.  İlişki üst tablosundan görüntülemek istediğiniz öğeleri sürükleyin **veri kaynakları** formunuza penceresi.  
  
5.  İlgili alt tablolar üst tablonun sütun listesi altındaki Genişletilebilir düğümleri olarak görünür. Formunuza ilgili düğümden görüntülemek istediğiniz öğeleri sürükleyin.  
  
    > [!NOTE]
    >  Oluşturur ilgisi olmayan ayrı bir öğe bir en üst düzey düğümü sürükleme [BindingSource bileşeni](http://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9) , değil kolaylaştırmak ilgili kayıtların gezinmesi. İlgili verileri bağlamak için tablolar aynı hiyerarşik düğümden seçmeniz gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri izlenecek yollar](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [İzlenecek yol: Bir Windows formunda veri görüntüleme](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [TableAdapter genel bakış](../data-tools/tableadapter-overview.md)   
 [Türü belirtilmiş veri kümeleri oluşturma ve düzenleme](../data-tools/creating-and-editing-typed-datasets.md)   
 [Yeni veri kaynağı ekleme](../data-tools/add-new-data-sources.md)   
 [Nasıl yapılır: bir veritabanındaki verilere bağlanma](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Verileri doğrulama](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Nasıl yapılır: Windows Forms BindingNavigator Denetimi ile Verilerde Gezinme](http://msdn.microsoft.com/library/0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb)