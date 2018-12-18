---
title: 'Nasıl yapılır: saklı yordamları ve işlevleri (O R Designer) için eşlenen DataContext-metotları oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8b1864fa87867d2f48179c5215a18f2897d9883c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49196202"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Nasıl yapılır: saklı yordamları ve işlevleri (O/R Tasarımcısı) için eşlenen DataContext-metotları oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Saklı yordamları ve işlevleri eklenebilir [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] olarak <xref:System.Data.Linq.DataContext> yöntemleri. Yöntemini çağırarak ve gerekli parametrelerin geçirme veritabanında saklı yordamı veya işlevi çalıştırır ve verileri dönüş türünü döndüren <xref:System.Data.Linq.DataContext> yöntemi. İlgili ayrıntılı bilgi için <xref:System.Data.Linq.DataContext> yöntemleri bkz [DataContext yöntemi (O/R Tasarımcısı)](../data-tools/datacontext-methods-o-r-designer.md).  
  
> [!NOTE]
>  Saklı yordamlar da Varsayılanı geçersiz kılmak için kullanılabilir [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] ekleme, güncelleştirme gerçekleştiren ve bir veritabanına varlık sınıflardan değişiklikler kaydedildiğinde siler çalışma zamanı davranışı. Daha fazla bilgi için [nasıl yapılır: güncelleştirme, ekleme ve silme (O/R Tasarımcısı) gerçekleştirmek için saklı yordamlar atama](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## <a name="creating-datacontext-methods"></a>DataContext yöntemi oluşturma  
 Oluşturabileceğiniz <xref:System.Data.Linq.DataContext> sürükleyerek yöntemler depolanan yordamları veya işlevlerden **Sunucu Gezgini/veritabanı Gezgini** üzerine [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
> [!NOTE]
>  Dönüş türü oluşturulan <xref:System.Data.Linq.DataContext> yöntemi farklı bağlı olarak burada saklı yordamı bırakın veya işlevini [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Öğeleri doğrudan mevcut bir varlık sınıfı üzerine bırakarak oluşturur bir <xref:System.Data.Linq.DataContext> yöntemi varlık sınıfı dönüş türüne sahip. Öğeleri boş bir alanının bırakarak [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] oluşturur bir <xref:System.Data.Linq.DataContext> otomatik olarak oluşturulan bir tür döndüren yöntem. Dönüş türünü değiştirebilirsiniz bir <xref:System.Data.Linq.DataContext> yöntemleri bölmesine ekledikten sonra yöntemi. İnceleme veya dönüş türünü değiştirmek için bir <xref:System.Data.Linq.DataContext> yöntemi seçin ve İnceleme **dönüş türü** özelliğinde **özellikleri** penceresi. Daha fazla bilgi için [nasıl yapılır: bir DataContext yöntemi (O/R Tasarımcısı) dönüş türünü değiştirme](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>DataContext oluşturmak için otomatik olarak döndüren yöntemler türü oluşturuldu  
  
1.  İçinde **Sunucu Gezgini**/**veritabanı Gezgini**, genişletme **saklı yordamlar** birlikte çalıştığınız veritabanı düğümü.  
  
2.  İstenen saklı yordamı bulun ve boş bir alanı sürükleyin [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
     <xref:System.Data.Linq.DataContext> Yöntemi otomatik olarak oluşturulan bir dönüş türü ile oluşturulur ve görünür **yöntemleri** bölmesi.  
  
#### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Bir varlık sınıfı dönüş türüne sahip bir DataContext yöntemi oluşturmak için  
  
1.  İçinde **Sunucu Gezgini**/**veritabanı Gezgini**, genişletme **saklı yordamlar** birlikte çalıştığınız veritabanı düğümü.  
  
2.  İstenen saklı yordamı bulun ve varolan bir varlık sınıfı sürükleyin [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
     <xref:System.Data.Linq.DataContext> Yöntemi seçili varlık sınıfı, dönüş türü ile oluşturulur ve görünür **yöntemleri** bölmesi.  
  
> [!NOTE]
>  Varolan dönüş türünü değiştirme hakkında bilgi için <xref:System.Data.Linq.DataContext> yöntemleri bkz [nasıl yapılır: bir DataContext yöntemi (O/R Tasarımcısı) dönüş türünü değiştirme](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to SQL araçlarını Visual Studio'da](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [DataContext yöntemi (O/R Tasarımcısı)](../data-tools/datacontext-methods-o-r-designer.md)   
 [İzlenecek yol: LINQ to SQL sınıfları (O R Designer) oluşturma](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Visual Basic'de LINQ'e giriş](http://msdn.microsoft.com/library/3047d86e-0d49-40e2-928b-dc02e46c7984)   
 [Nasıl yapılır: LINQ sorguları yazma C#](http://msdn.microsoft.com/library/45e47fcc-cfa1-4b72-b161-d038ae87bd23)

