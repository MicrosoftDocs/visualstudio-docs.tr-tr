---
title: 'Nasıl yapılır: güncelleştirme, ekleme ve silme (O R Designer) gerçekleştirmek için saklı yordamlar atama | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4f65af06a275dc50afafc70fd95c9b93d9bba458
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49232720"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>Nasıl yapılır: güncelleştirme, ekleme ve silme (O/R Tasarımcısı) gerçekleştirmek için saklı yordamlar atama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Saklı yordamlar için O/R Tasarımcısı eklenebilir ve tipik olarak yürütülen <xref:System.Data.Linq.DataContext> yöntemleri. Varsayılan geçersiz kılmak için de kullanılabilir [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] ekleme, güncelleştirme gerçekleştiren ve bir veritabanına varlık sınıflardan değişiklikler kaydedildiğinde siler çalışma zamanı davranışı (örneğin, çağrılırken <xref:System.Data.Linq.DataContext.SubmitChanges%2A> yöntemi).  
  
> [!NOTE]
>  Depolanmış yordamınızdaki istemciye geri gönderilecek gereken değer döndürürse (örneğin, hesaplanan değerler saklı yordamda), saklı yordamlarınızı çıkış parametreleri oluşturun. Çıktı parametreleri kullanamıyorsanız, O/R tasarımcısı tarafından oluşturulan yazma güvenmek yerine bir kısmi yöntem uygulaması geçersiz kılar. Veritabanı tarafından oluşturulan değerleri için eşlenmiş üyeleri ekleme veya güncelleştirme işlemleri başarıyla tamamlanmadan sonra uygun değerler belirlemeniz gerekir. Daha fazla bilgi için [sorumlulukları geliştirici olarak geçersiz kılma varsayılan davranış](http://msdn.microsoft.com/library/c6909ddd-e053-46a8-980c-0e12a9797be1).  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] otomatik olarak kimlik (otomatik artış), rowguıdcol (veritabanı tarafından oluşturulan GUID) ve zaman damgası sütunları için veritabanı tarafından oluşturulan işler değerler. Veritabanı üretilmiş değerler diğer sütun türlerinde beklenmedik bir null değer neden olur. Veritabanı tarafından oluşturulan değerleri döndürülecek el ile ayarlamanız <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> için `true` ve <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> aşağıdakilerden birine: <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync>, veya <xref:System.Data.Linq.Mapping.AutoSync>.  
  
## <a name="configuring-the-update-behavior-of-an-entity-class"></a>Bir varlık sınıfı güncelleştirme davranışını yapılandırma  
 Varsayılan olarak, bir veritabanı (ekleme, güncelleştirme ve silme) verilerde yapılan değişikliklerle güncelleştirmek için mantığı [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] varlık sınıfları tarafından sağlanır [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] çalışma zamanı. Çalışma zamanı varsayılan tablo (sütun ve birincil anahtar bilgileri) şemaya dayalı INSERT, Update ve Delete komutlarını oluşturur. Varsayılan davranış istenildiği gibi Güncelleştirme davranışı gerekli bir ekleme, güncelleştirme gerçekleştirmek için belirli saklı yordamlar atayarak yapılandırabilirsiniz ve silmeleri Tablonuzdaki verileri işlemek için gerekli. Varlık sınıflarınızı görünümleriyle eşleme, varsayılan davranışı gibi değil oluşturulduğunda, aynı zamanda bunu yapabilirsiniz. Son olarak, veritabanı saklı yordamlar aracılığıyla tablo erişim gerektirdiğinde güncelleştirme varsayılan davranışı geçersiz kılabilirsiniz.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>Bir varlık sınıfı varsayılan davranışı geçersiz kılmak için saklı yordamlar atama  
  
1.  Açık **LINQ to SQL** Tasarımcısı'nda dosya. (.dbml dosyasına çift tıklayarak **Çözüm Gezgini**.)  
  
2.  İçinde **Sunucu Gezgini**/**veritabanı Gezgini**, genişletme **saklı yordamlar** INSERT, Update, kullanmak istediğiniz saklı yordamları bulun ve/veya silme komutlarını varlık sınıfı.  
  
3.  Saklı yordam O/R Tasarımcısı sürükleyin.  
  
     Saklı yordam yöntemler bölmesi eklenen bir <xref:System.Data.Linq.DataContext> yöntemi. Daha fazla bilgi için [DataContext yöntemi (O/R Tasarımcısı)](../data-tools/datacontext-methods-o-r-designer.md).  
  
4.  Güncelleştirmeleri gerçekleştirmek için saklı yordam kullanmak istediğiniz varlık sınıfı seçin.  
  
5.  İçinde **özellikleri** penceresinde komut geçersiz kılmayı seçin (**Ekle**, **güncelleştirme**, veya **Sil**).  
  
6.  Sözcükleri yanındaki üç nokta (...) tıklayın **kullanım çalışma zamanı** açmak için **davranışı Yapılandır** iletişim kutusu.  
  
7.  Seçin **özelleştirme**.  
  
8.  İstenen saklı yordamda **Özelleştir** listesi.  
  
9. Listesini denetleyin **yöntem bağımsız değişkenleri** ve **sınıfı özellikleri** doğrulamak için **yöntem bağımsız değişkenleri** uygun eşleme **sınıfıözellikleri**. Özgün yöntemi bağımsız değişken eşleme (Original_*ArgumentName*) özgün özelliklerine (*PropertyName* (orijinal)) için Update ve Delete komutlarını.  
  
    > [!NOTE]
    >  Adları eşleştiğinde varsayılan olarak, yöntem bağımsız değişkenleri sınıfın özelliklerine eşlenir. Tablo arasında varlık sınıfı adları artık eşleşen özellik değiştirdiyseniz, Tasarımcı doğru Eşleme belirleyemiyorsa eşlemek için eşdeğer sınıf özelliği seçmek olabilir.  
  
10. Tıklayın **Tamam** veya **uygulamak**.  
  
    > [!NOTE]
    >  Tıkladığınız sürece her bir sınıf/davranışını bileşimi davranışını yapılandırmak devam **Uygula** her değişikliği yaptıktan sonra. Tıklamadan önce sınıf veya davranış değiştirirseniz **Uygula**, bir uyarı iletişim kutusu sağlama değişiklikleri uygulamak için bir fırsat görünür.  
  
     Güncelleştirmeler için varsayılan çalışma zamanı mantığını kullanarak geri almak için INSERT, Update, yanındaki üç nokta simgesine tıklayın veya Sil komutu **özellikleri** penceresi ve ardından **çalışma zamanı kullanmak** içinde  **Davranışı Yapılandır** iletişim kutusu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to SQL araçlarını Visual Studio'da](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [DataContext yöntemi (O/R Tasarımcısı)](../data-tools/datacontext-methods-o-r-designer.md)   
 [İzlenecek yol: LINQ to SQL sınıfları (O R Designer) oluşturma](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [İzlenecek yol: Güncelleştirme oluşturmak için Northwind Customers tablosunu saklı yordamları](../data-tools/walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Insert, Update ve Delete İşlemleri](http://msdn.microsoft.com/library/26a43a4f-83c9-4732-806d-bb23aad0ff6b)

