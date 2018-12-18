---
title: Ayrı veri kümeleri ve TableAdapters öğelerini farklı projelere ayırma | Microsoft Docs
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
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1e94c76254b14bdf82e4e7a219cbb0f35cb532f1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49824334"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>Veri kümeleri ile TableAdapter’ları farklı projelere ayırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Türü belirtilmiş datasets Gelişmiş böylece [TableAdapters](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) ve veri kümesi sınıfları ayrı projelere oluşturulabilir. Bu, hızla uygulama katmanları ayırmak ve n katmanlı veri uygulamaları oluşturmak sağlar.  
  
 Aşağıdaki yordamda kullanma işlemi açıklanmaktadır[oluşturma ve yazılan veri kümelerini düzenleme](../data-tools/creating-and-editing-typed-datasets.md) oluşturulan içeren projeden farklı bir projeye veri kümesi kodunu oluşturmak için `TableAdapter` kod.  
  
## <a name="separatedatasets-and-tableadapters"></a>Separatedatasets ve TableAdapters öğelerini  
 Veri kümesi koddan ayırdığınızda `TableAdapter` kod, veri kümesi kodunu içeren proje, geçerli çözümde yer alması gerekir. Bu projenin geçerli çözümde yer almıyorsa, kullanılabilir olmayacaktır **DataSet projesi** listesinde **özellikleri** penceresi.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-separate-the-dataset-into-a-different-project"></a>Farklı bir projeye veri kümesini ayırmak için  
  
1. Bir veri kümesi (.xsd dosyasını) içeren bir çözüm açın.  
  
   > [!NOTE]
   >  Veri kümesi kodunuzu ayırmak istediğiniz proje çözüm içermiyorsa, projeyi oluşturmak veya mevcut bir projeyi çözüme ekleyin.  
  
2. Türü belirtilmiş veri kümesi dosyası (.xsd dosyasını) çift tıklayın **Çözüm Gezgini** açmak için **veri kümesi Tasarımcısı**.  
  
3. Boş bir alanı seçin **veri kümesi Tasarımcısı**.  
  
4. İçinde **özellikleri** penceresinde bulun **DataSet projesi** düğümü.  
  
5. İçinde **DataSet projesi** listesinde, istediğiniz veri kümesi kodunu oluşturmak proje adını seçin.  
  
    Veri kümesi kodunu oluşturmak istediğiniz projeyi seçin sonra **veri kümesi dosyası** özelliği, bir varsayılan dosya adıyla doldurulur. Gerekirse, bu adı değiştirebilirsiniz. Ayrıca, belirli bir dizine veri kümesi kodunu oluşturmak istiyorsanız, ayarlayabileceğiniz **proje klasörü** özelliğini bir klasörün adı.  
  
   > [!NOTE]
   >  Veri kümelerini ve TableAdapter bağdaştırıcılarını ayırdığınızda (ayarlayarak **DataSet projesi** özelliği), projedeki varolan kısmi veri kümesi sınıfları olmaz taşınması otomatik olarak. Var olan veri kümesi kısmi sınıflarının veri kümesi projesine el ile taşınması gerekir.  
  
6. Veri kümesini kaydetme.  
  
    Veri kümesi kod içinde seçilen projede oluşturulur **DataSet projesi** özelliği ve **TableAdapter** kod, geçerli projenin içine oluşturulur.  
  
   Veri kümesi ayırdıktan sonra varsayılan olarak ve `TableAdapter` kod sonucu olan her proje bir parçalı sınıf dosyasında. Adlı bir dosya özgün proje sahip DatasetName.Designer.vb (veya DatasetName.Designer.cs) içeren `TableAdapter` kod. İçinde belirtilen projeyi **Dataset projesi** özelliğine sahip bir dosya DatasetName.DataSet.Designer.vb (veya DatasetName.DataSet.Designer.cs) adlı, veri kümesi kodunu içerir.  
  
> [!NOTE]
>  Oluşturulan sınıf dosyayı görüntülemek için veri kümesi seçin veya `TableAdapter` proje. Ardından **Çözüm Gezgini**seçin **tüm dosyaları göster** .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [N katmanlı veri uygulamalarına genel bakış](../data-tools/n-tier-data-applications-overview.md)   
 [İzlenecek yol: bir N katmanlı veri uygulaması oluşturma](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [Hiyerarşik güncelleştirme](../data-tools/hierarchical-update.md)   
 [Visual Studio'da verilere erişme](../data-tools/accessing-data-in-visual-studio.md)   
 [ADO.NET](http://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca)

