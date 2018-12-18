---
title: 'Nasıl yapılır: bir veri kümesini verilerle doldurmak | Microsoft Docs'
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
- TableAdapter.GetData
- TableAdapter.Fill
- datasets [Visual Basic], filling
- DataTable objects, loading
- data [Visual Basic], loading into datasets
ms.assetid: 7ab436d4-54ba-4621-902f-3f193279e18c
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: f36aa2dac656f6fd27b656d0ddfb58a758eb6487
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49296003"
---
# <a name="how-to-fill-a-dataset-with-data"></a>Nasıl yapılır: bir veri kümesi ile veri doldurun
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İçinde tek tek veri yükleme için "bir veri kümesini verilerle doldurma" ifadesini başvuruyor <xref:System.Data.DataTable> veri kümesini oluşturan nesneleri. TableAdapter sorguları yürüterek veya veri bağdaştırıcısı yürüterek veri tablolarını doldurmak (örneğin, <xref:System.Data.SqlClient.SqlDataAdapter>) komutları.  
  
 TableAdapter bağdaştırıcıları veya veri bağdaştırıcısı kullanmanız gerekir, veri kümesinin nasıl oluşturulacağını bağlıdır. Tasarım araçları kullandıysanız [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], gibi [veri kaynağı Yapılandırma Sihirbazı](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f), Veri kümenizi TableAdapter bağdaştırıcıları içerir. TableAdapter'ları hakkında daha fazla bilgi için bkz. [TableAdapter genel bakışı](../data-tools/tableadapter-overview.md). Veri kümeniz program aracılığıyla oluşturduysanız, genellikle verileri verileri tablolara yüklemek için veri bağdaştırıcıları oluşturmanız gerekir.  
  
> [!NOTE]
>  Öğeleri sürüklerken [veri kaynakları penceresi](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) formunuza, verilerle veri tablosunu doldurmak için kod otomatik olarak eklenir `Form_Load` olay işleyicisi. Formunuza belirli tablolarınızı doldurmak için söz dizimi görmek için Kod Düzenleyicisi'nde açın. Form yüklendiğinde tablosunu doldurmak istemiyorsanız başka bir yöntem için bu kodu taşıyın ya da tamamen kaldırın.  
  
## <a name="filling-a-dataset-using-a-tableadapter"></a>Bir TableAdapter kullanarak Dataset doldurma  
 Verileri bir veri kümesindeki verileri tablolara yüklemek için TableAdapter sorgu çağırabilirsiniz. Geçirmek <xref:System.Data.DataTable> TableAdapter sorgusu doldurmak istediğiniz. Sorgunuzu parametre alırsa, bu yöntemin de geçirin. Birden çok tablodan veri kümesini içeren, ayrı TableAdapter'ları için her bir tablo olması gerekir ve bu nedenle her tablo ayrı ayrı doldurmanız gerekir.  
  
> [!NOTE]
>  Her bir TableAdapter sorgu çalıştırmanızda varsayılan olarak, tabloya yüklenen sorgunun sonuçlarını önce tablodaki verileri temizlenir. Mevcut verileri tabloda tutmak ve TableAdapter bağdaştırıcısının ayarlayarak sonuçları sona Ekle `ClearBeforeFill` özelliğini `false`.  
  
#### <a name="to-fill-a-dataset-with-data-using-a-tableadapter"></a>Bir veri kümesi bir TableAdapter kullanarak verilerle doldurmak için  
  
1.  Form veya bileşeni **Kod Düzenleyicisi**.  
  
2.  Kodu uygulamanızda bir veri tablosuna veri yüklemek için gerek duyduğunuz herhangi bir yere ekleyin. Sorgunuzu parametre almaz, geçirin <xref:System.Data.DataTable> doldurmak istediğiniz. Kod aşağıdaki gibi görünmelidir:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#4)]
     [!code-vb[VbRaddataFillingAndExecuting#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#4)]  
  
3.  Sorgunuzu parametre alırsa, geçirin <xref:System.Data.DataTable> dolgu ve beklenen sorgu parametreleri istiyorsunuz. Sorgunuzda gerçek parametre bağlı olarak kod aşağıdaki örneklere benzer olacaktır:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#5)]
     [!code-vb[VbRaddataFillingAndExecuting#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#5)]  
  
## <a name="filling-a-dataset-using-a-dataadapter"></a>DataAdapter kullanarak Dataset doldurma  
 Veri bağdaştırıcının çağrı `Fill` yöntemi. Bu SQL deyimi yürütmek bağdaştırıcı neden veya saklı yordam başvuruda kendi `SelectCommand` özelliği ve sonuçları kümesindeki bir tabloya yerleştirin. Veri kümesi birden fazla tablo varsa, her tablo için ayrı veri bağdaştırıcıları olmalıdır ve bu nedenle her tablo ayrı ayrı doldurmanız gerekir.  
  
#### <a name="to-fill-a-dataset-with-data-using-a-dataadapter"></a>Bir veri kümesi DataAdapter kullanarak verilerle doldurmak için  
  
-   Çağrı <xref:System.Data.Common.DataAdapter.Fill%2A> yöntemi <xref:System.Data.Common.DataAdapter>, içinde geçen <xref:System.Data.DataSet> veya <xref:System.Data.DataTable> verileri yüklenemedi. Örneğin:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#6)]
     [!code-vb[VbRaddataFillingAndExecuting#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#6)]  
  
     Genellikle adı sağlamalıdır <xref:System.Data.DataTable> verileri yüklenemedi. Name, başarılı olursa bir <xref:System.Data.DataSet> bir özel veri tablosu yerine bir <xref:System.Data.DataTable> adlı `Table1` veri kümesine eklenir ve sonuçları veritabanından yüklendi (mevcut verileri yükleme aksine <xref:System.Data.DataTable> veri kümesinde). Daha fazla bilgi için [dataadapter'dan bir DataSet doldurma](http://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TableAdapters'ı kullanarak veri kümelerini doldurma](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Uygulamanıza veri getirme](../data-tools/fetching-data-into-your-application.md)   
 [Uygulamanızı veri almaya hazırlama](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Uygulamanızdaki verileri düzenleme](../data-tools/editing-data-in-your-application.md)   
 [Verileri doğrulama](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Verileri Kaydetme](../data-tools/saving-data.md)