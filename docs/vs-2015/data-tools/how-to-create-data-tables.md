---
title: 'Nasıl yapılır: veri tabloları oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Microsoft.VSDesigner.DataSource.DesignTable
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], creating data tables
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
ms.assetid: 0e8bf4c4-3d05-4b20-9926-9d29914b26ed
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 8b26bf0cfbd387f33f9f038d5927db795a8f2769
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49288918"
---
# <a name="how-to-create-data-tables"></a>Nasıl yapılır: Veri Tabloları Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Veri, bellekte depolanabilir <xref:System.Data.DataTable> nesneleri. (Veri kümeleri yapılan <xref:System.Data.DataTable> nesneleri.) Genellikle TableAdapter'ı kullanmaya yeni veri tabloları oluşturma [TableAdapter Yapılandırma Sihirbazı'nı](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8) veya veritabanı nesnelerini sürükleyerek **Sunucu Gezgini** üzerine **veri kümesi Tasarımcısı** .  
  
 İçinde yeni bir TableAdapter oluşturduğunuzda, veri tabloları bir byproduct oluşturulur [veri kaynağı Yapılandırma Sihirbazı](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) yanı, ancak bunlar da bağımsız olarak oluşturulabilir. Sürükleyerek bir tek başına veri tablosu oluşturma bir <xref:System.Data.DataTable> nesnesinden **veri kümesi** sekmesinde **araç kutusu** üzerine **veri kümesi Tasarımcısı**.  
  
> [!NOTE]
>  Veri tablolarını program aracılığıyla oluşturmak için bkz [DataTable oluşturma](http://msdn.microsoft.com/library/eecf9d78-60e3-4fdc-8de0-e56c13a89414).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="creating-a-datatable-with-tableadapter"></a>TableAdapter ile bir DataTable oluşturma  
 TableAdapter bağdaştırıcılarını veri tablolarını tablo ile veri doldurun ve değişiklikleri veritabanına geri yazma yöntemleri içerir. Çalıştırarak TableAdapters oluşturma **TableAdapter Yapılandırma Sihirbazı'nı** veya veritabanı nesnelerini sürükleyerek **Sunucu Gezgini** üzerine **veri kümesi Tasarımcısı**.  
  
#### <a name="to-create-a-new-data-table-with-tableadapter"></a>TableAdapter ile yeni bir veri tablosu oluşturmak için  
  
1.  Kümenizde açın **veri kümesi Tasarımcısı**. Bilgi için [nasıl yapılır: bir veri kümesini veri kümesi Tasarımcısı'nda açma](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Sürükleme bir **TableAdapter** gelen **veri kümesi** sekmesinde **araç kutusu** üzerine **veri kümesi Tasarımcısı**.  
  
     **TableAdapter Yapılandırma Sihirbazı'nı** açılır.  
  
3.  Sihirbazı tamamlayın. Daha fazla bilgi için [TableAdapter Yapılandırma Sihirbazı](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8)  
  
#### <a name="to-create-a-new-data-table-with-a-tableadapter-from-server-explorer"></a>Sunucu Gezgini'nden bir TableAdapter ile yeni bir veri tablosu oluşturmak için  
  
1.  Kümenizde açın **veri kaynağı Tasarımcısı**.  
  
2.  Bir veritabanı nesnesi (örneğin, bir tablo) sürükleyin **Sunucu Gezgini** üzerine **veri kümesi Tasarımcısı**.  
  
## <a name="creating-a-standalone-datatable"></a>Tek başına DataTable oluşturma  
 Tek başına tablo olması gerekir `Fill` mantıksal uygulanan verilerle doldurulması için. Tek başına veri tablolarını doldurmak hakkında daha fazla bilgi için bkz: [dataadapter'dan bir DataSet doldurma](http://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153).  
  
#### <a name="to-create-a-new-stand-alone-data-table"></a>Yeni bir tek başına veri tablosu oluşturmak için  
  
1.  Kümenizde açın **veri kümesi Tasarımcısı**.  
  
2.  Sürükleme bir <xref:System.Data.DataTable> gelen **veri kümesi** sekmesinde **araç kutusu** üzerine **veri kümesi Tasarımcısı**.  
  
3.  Veri tablosu tanımlamak için sütunları ekleyin. Daha fazla bilgi için [nasıl yapılır: bir DataTable sütunları ekleme](http://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Data.DataTable>   
 [Veri izlenecek yollar](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [İzlenecek yol: Bir Windows formunda veri görüntüleme](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [TableAdapter genel bakış](../data-tools/tableadapter-overview.md)   
 [Türü belirtilmiş veri kümeleri oluşturma ve düzenleme](../data-tools/creating-and-editing-typed-datasets.md)   
 [Yeni veri kaynağı ekleme](../data-tools/add-new-data-sources.md)   
 [Veri kaynakları penceresi](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [Nasıl yapılır: bir veritabanındaki verilere bağlanma](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Verileri doğrulama](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)