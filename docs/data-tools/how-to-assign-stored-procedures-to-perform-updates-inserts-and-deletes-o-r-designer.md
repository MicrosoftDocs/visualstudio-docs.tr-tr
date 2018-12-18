---
title: Güncelleştirme gerçekleştirmek için saklı yordamları Ekle ve LINQ to SQL O/R Tasarımcısı Sil
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b7fd690997b7d7b58f8d1c1f84ea7f471d4fe496
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089782"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>Nasıl yapılır: güncelleştirme, ekleme ve silme (O/R Tasarımcısı) gerçekleştirmek için saklı yordamlar atayın

Saklı yordamlar eklenebilir **O/R Tasarımcısı** ve tipik olarak yürütülen <xref:System.Data.Linq.DataContext> yöntemleri. Varsayılan LINQ ekler, güncelleştirmeleri gerçekleştiren ve değişiklikleri veritabanına varlık sınıflardan kaydedildiğinde siler SQL çalışma zamanı davranışını geçersiz kılmak için de kullanılabilir (örneğin, çağrılırken <xref:System.Data.Linq.DataContext.SubmitChanges%2A> yöntemi).

> [!NOTE]
> Saklı yordam istemciye gönderilmesi gereken değerler döndürürse (örneğin, hesaplanan değerler saklı yordamda), çıktı parametreleri saklı yordamlarda oluşturun. Çıkış parametreleri kullanamıyorsanız, O/R tasarımcısı tarafından oluşturulan yazma güvenmek yerine bir kısmi yöntemi uygulama geçersiz kılar. Veritabanı oluşturulan değerler için eşlenen üyelerinin ekleme veya güncelleştirme işlemleri başarıyla tamamlandıktan sonra uygun değerlere ayarlanmış olması gerekir. Daha fazla bilgi için bkz: [Geliştirici içinde geçersiz kılma varsayılan davranışı sorumluluklarını](/dotnet/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior).

> [!NOTE]
> LINQ-SQL veritabanı tarafından üretilen değerler kimlik (otomatik artım), rowguıdcol (veritabanında oluşturulan GUID) ve zaman damgası sütunları için otomatik olarak işler. Diğer sütun türleri veritabanında oluşturulan değerlerde beklenmedik bir null değer neden olur. Veritabanında oluşturulan değer döndürmek için el ile ayarlamanız gerekir <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> için **true** ve <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> aşağıdakilerden birine: [AutoSync.Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>), [AutoSync.OnInsert ](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>), veya [AutoSync.OnUpdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>).

## <a name="configure-the-update-behavior-of-an-entity-class"></a>Bir varlık sınıfı güncelleştirme davranışını yapılandırın

Varsayılan olarak, bir veritabanını (ekler, güncelleştirmeleri ve silme) LINQ veri SQL varlık sınıfı için yapılan değişikliklerle güncelleştirmek için mantık LINQ to SQL çalışma zamanı tarafından sağlanır. Çalışma zamanı (sütun ve birincil anahtar bilgilerini) tablonun şemasını temel alan INSERT, UPDATE ve DELETE komutları varsayılan oluşturur. Varsayılan davranış değil istendiğinde, gerekli ekler, güncelleştirmeleri ve silme, tablodaki verileri işlemek için gerekli gerçekleştirmek için özel saklı yordamları atayarak güncelleştirme davranışını yapılandırabilirsiniz. Varlık sınıflarınızı görünümlerine eşlediğinizde varsayılan davranışı, örneğin, değil oluşturulduğunda de bunu yapabilirsiniz. Son olarak, veritabanı saklı yordamları aracılığıyla tablo erişim gerektirdiğinde varsayılan güncelleştirme davranışı geçersiz kılabilirsiniz.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>Bir varlık sınıfı varsayılan davranışını geçersiz kılmak için saklı yordamlar atamak için

1.  Açık **LINQ-SQL** Tasarımcısı'nda dosya. (Çift **.dbml** dosyasını **Çözüm Gezgini**.)

2.  İçinde **Sunucu Gezgini** veya **Database Explorer**, genişletin **saklı yordamlar** ve INSERT, Update, kullanın ve/veya silmek istediğiniz saklı yordamlar bulun Varlık sınıfı komutları.

3.  Saklı yordam üzerine sürükleyin **O/R Tasarımcısı**.

     Saklı yordam yöntemleri bölmesi olarak eklenen bir <xref:System.Data.Linq.DataContext> yöntemi. Daha fazla bilgi için bkz: [DataContext yöntemleri (O/R Tasarımcısı)](../data-tools/datacontext-methods-o-r-designer.md).

4.  Saklı yordam güncelleştirmeleri gerçekleştirmek için kullanmak istediğiniz varlık sınıfı seçin.

5.  İçinde **özellikleri** penceresinde, geçersiz kılmak için komutu seçin (**Ekle**, **güncelleştirme**, veya **silmek**).

6.  Sözcükleri yanındaki üç nokta işaretine (...) tıklatın **kullanım çalışma zamanı** açmak için **yapılandırma davranışı** iletişim kutusu.

7.  Seçin **özelleştirme**.

8.  İstenen saklı yordamı seçin **Özelleştir** listesi.

9. Listesini inceleyin **yöntem bağımsız değişkenleri** ve **sınıf özelliklerini** doğrulamak için **yöntem bağımsız değişkenleri** uygun harita **sınıf özelliklerini**. Özgün yöntemi bağımsız değişken eşleme (`Original_<ArgumentName>`) özgün özelliklerine (`<PropertyName> (Original)`) için `Update` ve `Delete` komutları.

    > [!NOTE]
    > Adları eşleştiğinde varsayılan olarak, yöntem bağımsız değişkenleri sınıfın özelliklerine eşlenir. Özellik adlarının artık tablo ve varlık sınıfı arasında eşleştiğini değiştirdiyseniz, Tasarımcı doğru Eşleme belirleyemiyorsa eşlemek için eşdeğer sınıfı özelliği seçin gerekebilir.

10. Tıklatın **Tamam** veya **uygulamak**.

    > [!NOTE]
    >  Tıklattığınız sürece her sınıf ve davranış birleşimini davranışını yapılandırmaya devam edebilirsiniz **Uygula** her değişikliği yaptıktan sonra. Tıklatmadan önce sınıf veya davranışı değiştirirseniz **Uygula**, bir uyarı iletişim kutusu görünür ve değişikliklerinizi uygulamak için bir fırsat sunar.

Varsayılan çalışma zamanı mantığı güncelleştirmeleri kullanmaya dönmek için üç nokta yanındaki tıklayın **Ekle**, **güncelleştirme**, veya **silmek** komutunu **özellikleri**  penceresini açın ve ardından **çalışma zamanı kullanmak** içinde **yapılandırma davranışı** iletişim kutusu.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ-SQL Visual Studio Araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [DataContext metotları](../data-tools/datacontext-methods-o-r-designer.md)
- [LINQ-SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Ekleme, güncelleştirme ve silme işlemleri (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/insert-update-and-delete-operations)