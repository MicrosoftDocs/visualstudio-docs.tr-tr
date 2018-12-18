---
title: DataContext yöntemi (O R Designer) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2ccf32d4af0bd16032c4601b054be6407071753f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49200466"
---
# <a name="datacontext-methods-or-designer"></a>DataContext yöntemi (O/R Tasarımcısı)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
DataContext] (assetId:///T:System.Data.Linq.DataContext?qualifyHint=False & autoUpgrade = True) yöntemleri (bağlamında [LINQ to SQL araçlarını Visual Studio'da](../data-tools/linq-to-sql-tools-in-visual-studio2.md)), yöntemler <xref:System.Data.Linq.DataContext> saklı çalıştırılan sınıfı yordamları ve işlevleri bir veritabanında.  
  
 <xref:System.Data.Linq.DataContext> Sınıfı bir [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] bir conduit arasında bir SQL Server veritabanı olarak davranan bir sınıf ve [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] veritabanına eşlenen varlık sınıfları. <xref:System.Data.Linq.DataContext> Sınıfı bağlantı dizesi bilgilerini ve bir veritabanına bağlanma ve veritabanındaki verileri işlemek için yöntemler içerir. Varsayılan olarak, <xref:System.Data.Linq.DataContext> sınıfı içerir, gibi çağırabileceğiniz birkaç yöntem <xref:System.Data.Linq.DataContext.SubmitChanges%2A> gönderen yöntemi güncelleştirilmiş verileri [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] veritabanına sınıfları. Ayrıca, ek oluşturabilirsiniz <xref:System.Data.Linq.DataContext> saklı yordamları ve işlevleri için eşleme yöntemleri. Diğer bir deyişle, bu özel metotları çağırma saklı yordamı veya işlevi veritabanında, çalışacak <xref:System.Data.Linq.DataContext> yöntemi eşlenmiş durumda. İçin yeni yöntemler ekleyebilirsiniz <xref:System.Data.Linq.DataContext> herhangi bir sınıf genişletmek için yöntemleri eklemek gibi sınıf. Hakkında tartışmalar, ancak <xref:System.Data.Linq.DataContext> bağlamında yöntemleri [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], bu <xref:System.Data.Linq.DataContext> saklı yordamlar ve ele alınmıştır işlevlere eşleme yöntemleri.  
  
## <a name="methods-pane"></a>Yöntemler bölmesi  
 <xref:System.Data.Linq.DataContext> saklı yordamları ve işlevleri için eşleme yöntemlerini yöntemleri bölmesinde görüntülenen [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Yöntemler bölmesini tarafında bölmesidir **varlıkları** bölmesinde (ana tasarım yüzeyi). Yöntemler bölmesini listeler <xref:System.Data.Linq.DataContext> kullanarak oluşturduğunuz yöntemleri [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Yöntemler bölmesini varsayılan olarak boştur; saklı yordamları ve işlevleri sürükleyin **Sunucu Gezgini**/**veritabanı Gezgini** üzerine [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] oluşturmak için <xref:System.Data.Linq.DataContext> yöntemleri ve yöntemler bölmesi doldurabilirsiniz. Daha fazla bilgi için [nasıl yapılır: saklı yordamları ve işlevleri (O/R Tasarımcısı) için eşlenen DataContext oluşturma yöntemleri](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).  
  
> [!NOTE]
>  Açın ve sağ tıklayarak yöntemler bölmesini kapatmak [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] tıklayıp **yöntemler Bölmesini Gizle** veya **yöntemler bölmesini göster**, veya klavye kısayolunu CTRL + 1 kullanın.  
  
## <a name="two-types-of-datacontext-methods"></a>İki tür DataContext yöntemi  
 DataContext yöntemi saklı yordamları ve işlevleri veritabanında eşleyen bu yöntemlerdir. Oluşturun ve yöntemleri bölmesinde DataContext yöntemler [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. İki ayrı türü vardır <xref:System.Data.Linq.DataContext> yöntemleri; Bu, bir veya daha fazla sonuç kümesi döndüren ve desteklemeyenler:  
  
-   <xref:System.Data.Linq.DataContext> bir veya daha fazla sonuç kümesi döndüren yöntemler:  
  
     Bu tür oluşturma <xref:System.Data.Linq.DataContext> saklı yordamları ve işlevleri veritabanında çalıştırın ve sonuçları döndürmek uygulamanızı yalnızca gerektiğinde yöntemi. Daha fazla bilgi için [nasıl yapılır: saklı yordamları ve işlevleri (O/R Tasarımcısı) için eşlenen DataContext oluşturma yöntemleri](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), System.Data.Linq.ISingleResult\<T >, ve <xref:System.Data.Linq.IMultipleResults>.  
  
-   <xref:System.Data.Linq.DataContext> Sonuç kümesi döndürmüyor yöntemleri: gibi ekler, güncelleştirmeler ve özel varlık sınıfı için siler.  
  
     Bu tür oluşturma <xref:System.Data.Linq.DataContext> uygulamanızın varsayılan kullanmak yerine saklı yordamları çalıştırmak sahip olduğunda yöntemi [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] kaydetme davranışını değiştiren bir varlık sınıfı ve veritabanı arasında veri. Daha fazla bilgi için [nasıl yapılır: güncelleştirme, ekleme ve silme (O/R Tasarımcısı) gerçekleştirmek için saklı yordamlar atama](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## <a name="return-types-of-datacontext-methods"></a>DataContext yöntemlerinin dönüş türleri  
 Saklı yordamları ve işlevleri sürüklediğinizde **Sunucu Gezgini**/**veritabanı Gezgini** üzerine [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], dönüş türü oluşturulan <xref:System.Data.Linq.DataContext> yöntemi farklıdır Öğeyi Bırak yere bağlı olarak. Öğeleri doğrudan mevcut bir varlık sınıfı üzerine bırakarak oluşturur bir <xref:System.Data.Linq.DataContext> yöntemi varlık sınıfı dönüş türüne sahip; bırakma öğeleri boş bir alanı üzerine [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] oluşturur (ya da bölmesinde) bir <xref:System.Data.Linq.DataContext> döndüren yöntem bir otomatik olarak oluşturulan tür. Oluşturulan otomatik olarak oluşturulan tür saklı yordam veya işlev adı ve saklı yordamı veya işlevi tarafından döndürülen alanlarla eşlenen özellikler eşleşen bir ada sahip.  
  
> [!NOTE]
>  Dönüş türünü değiştirebilirsiniz bir <xref:System.Data.Linq.DataContext> yöntemleri bölmesine ekledikten sonra yöntemi. İnceleme veya dönüş türünü değiştirmek için bir <xref:System.Data.Linq.DataContext> yöntemi seçin ve İnceleme **dönüş türü** özelliğinde **özellikleri** penceresi. Daha fazla bilgi için [nasıl yapılır: bir DataContext yöntemi (O/R Tasarımcısı) dönüş türünü değiştirme](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
 Veritabanından O/R Tasarımcısı yüzeyine sürükleyin nesneleri veritabanındaki nesneleri adına göre otomatik olarak yeniden adlandırılacaktır. Aynı nesne birden çok kez sürüklerseniz, bir sayı adlarını ayırır yeni adın sonuna eklenir. Veritabanı nesne adları, boşluk veya Visual Basic veya C# içinde desteklenmeyen karakterler içerdiğinde, boşluk veya geçersiz bir karakter bir alt çizgi ile değiştirilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to SQL araçlarını Visual Studio'da](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Saklı yordamlar](http://msdn.microsoft.com/library/4d23dd7a-a85f-44ff-a717-af7d0950c0fc)   
 [Nasıl yapılır: saklı yordamları ve işlevleri (O/R Tasarımcısı) için eşlenen DataContext-metotları oluşturma](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [Nasıl yapılır: güncelleştirme, ekleme ve silme (O/R Tasarımcısı) gerçekleştirmek için saklı yordamlar atama](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [İzlenecek yol: INSERT özelleştirme, güncelleştirme ve silme davranışı varlık sınıflarının](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)   
 [İzlenecek yol: LINQ to SQL sınıfları (O R Designer) oluşturma](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)

