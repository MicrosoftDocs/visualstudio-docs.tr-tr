---
title: 'İzlenecek Yol: Veri Kümesi Tasarımcısında DataTable Oluşturma'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 2cff383b6e06d8793a7730c36df01e2538b02c36
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174502"
---
# <a name="walkthrough-create-a-datatable-in-the-dataset-designer"></a>İzlenecek yol: veri kümesi tasarımcısında DataTable oluşturma

Bu izlenecek yolda nasıl oluşturulacağını açıklar bir <xref:System.Data.DataTable> (olmadan bir TableAdapter) kullanarak **veri kümesi Tasarımcısı**. TableAdapter'ları içeren veri tabloları oluşturma hakkında daha fazla bilgi için bkz. [oluştur ve TableAdapter yapılandırma](../data-tools/create-and-configure-tableadapters.md).

## <a name="create-a-new-windows-forms-application"></a>Yeni bir Windows Forms uygulaması oluşturma

1. Visual Studio'da üzerinde **dosya** menüsünde **yeni** > **proje**.

2. Ya da genişletin **Visual C#** veya **Visual Basic** seçip sol bölmedeki **Windows Masaüstü**.

3. Orta bölmede seçin **Windows Forms uygulaması** proje türü.

4. Projeyi adlandırın **DataTableWalkthrough**ve ardından **Tamam**.

     **DataTableWalkthrough** projesi oluşturulur ve eklenen **Çözüm Gezgini**.

## <a name="add-a-new-dataset-to-the-application"></a>Uygulamaya yeni bir veri kümesi ekleyin

1.  Üzerinde **proje** menüsünde **Yeni Öğe Ekle**.

     **Yeni Öğe Ekle** iletişim kutusu görüntülenir.

2.  Sol bölmede seçin **veri**, ardından **veri kümesi** orta bölmesinde.

3.  Seçin **ekleme**.

     Visual Studio adlı bir dosya ekler **dataSet1.xsd dosyasını** projeye ve onu açar **veri kümesi Tasarımcısı**.

## <a name="add-a-new-datatable-to-the-dataset"></a>Veri kümesine yeni bir DataTable ekleme

1.  Sürükleme bir **DataTable** gelen **veri kümesi** sekmesinde **araç kutusu** üzerine **veri kümesi Tasarımcısı**.

     Adlı bir tablo **DataTable1** veri kümesine eklenir.

2.  Başlık çubuğuna tıklayın **DataTable1** ve yeniden adlandırmak `Music`.

## <a name="add-columns-to-the-datatable"></a>DataTable tablosuna sütun ekleme

1.  Sağ **müzik** tablo. İşaret **Ekle**ve ardından **sütun**.

2.  Sütun adı `SongID`.

3.  İçinde **özellikleri** penceresinde <xref:System.Data.DataColumn.DataType%2A> özelliğini <xref:System.Int16?displayProperty=fullName>.

4.  Bu işlemi tekrarlayın ve aşağıdaki sütunları ekleyin:

     `SongTitle`: <xref:System.String?displayProperty=fullName>

     `Artist`: <xref:System.String?displayProperty=fullName>

     `Genre`: <xref:System.String?displayProperty=fullName>

## <a name="set-the-primary-key-for-the-table"></a>Tablonun birincil anahtarı Ayarla

Tüm veri tablolarının birincil anahtarı olmalıdır. Bir birincil anahtar, bir veri tablosu belirli bir kaydı benzersiz olarak tanımlar.

Birincil anahtarı ayarlamak için **SongID** sütun ve ardından **birincil anahtarı Ayarla**. Bir anahtar simgesi görünür **SongID** sütun.

## <a name="save-your-project"></a>Projenizi kaydedin

Kaydetmek için **DataTableWalkthrough** projesi **dosya** menüsünde **Tümünü Kaydet**.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio’da veri kümeleri oluşturma ve yapılandırma](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Verileri doğrulama](../data-tools/validate-data-in-datasets.md)