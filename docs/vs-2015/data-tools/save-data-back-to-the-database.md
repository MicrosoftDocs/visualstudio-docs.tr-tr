---
title: Verileri yeniden veritabanına kaydetme | Microsoft Docs
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
- datasets [Visual Basic], validating data
- data validation, datasets
- data [Visual Studio], saving
- row version
- updating datasets, constraints
- datasets [Visual Basic], about datasets
- datasets [Visual Basic], merging
- updates, constraints in datasets
- saving data, about saving data
- datasets [Visual Basic], constraints
- TableAdapters
ms.assetid: afe6cb8a-dc6a-428b-b07b-903ac02c890b
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6b6fd99b2b1a41d6baa3a110b2a595afb1dd7e3f
ms.sourcegitcommit: c9a01c599ce19a5845605b3b28c0229fd0abb93f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2018
ms.locfileid: "52281855"
---
# <a name="save-data-back-to-the-database"></a>Verileri yeniden veritabanına kaydetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Veri kümesi, verilerin bir bellek içi kopyasıdır. Bu verileri değiştirirseniz, bu değişiklikleri veritabanına kaydetmek için iyi bir uygulamadır. Üç yoldan biriyle bunu yapabilirsiniz:  
  
- Aşağıdakilerden birini çağırarak `Update` TableAdapter yöntemleri  
  
- TableAdapter DBDirect yöntemleri çağırarak  
  
- Üzerinde UpdateAll yöntemi çağırarak `TableAdapterManager` diğer tablolara veri kümesinde ilişkili tabloları veri kümesi içerdiğinde, Visual Studio sizin için oluşturur.  
  
  Verileri bir Windows Form veya XAML sayfası denetimleri için veri kümesi tablolarını bağladığınızda, veri bağlama mimarisi işin tümünü sizin için halleder.  
  
  TableAdapter'ları ile sahibiyseniz, doğrudan aşağıdaki konulardan birine atlayabilirsiniz:  
  
|Konu|Açıklama|  
|-----------|-----------------|  
|[Veritabanına yeni kayıtlar ekleme](../data-tools/insert-new-records-into-a-database.md)|Gerçekleştirme güncelleştirir ve TableAdapter bağdaştırıcıları veya komut nesneleri kullanarak ekler|  
|[TableAdapter kullanarak verileri güncelleştirme](../data-tools/update-data-by-using-a-tableadapter.md)|TableAdapters güncelleştirmeleriyle gerçekleştirme|  
|[Hiyerarşik güncelleştirme](../data-tools/hierarchical-update.md)|İki veya daha fazla ilgili tablo ile bir veri kümesinden güncelleştirmeleri gerçekleştirme|  
|[Bir eşzamanlılık özel durumunu işleme](../data-tools/handle-a-concurrency-exception.md)|İki kullanıcı aynı anda bir veritabanındaki verilerle aynı değiştirmeye çalıştığında özel durumları işleme|  
|[Bir işlemi kullanarak veri kaydetme](../data-tools/save-data-by-using-a-transaction.md)|System.Transactions ad alanı ve TransactionScope nesnesini kullanarak bir işlemde veri kaydetme|  
|[Bir işlemde veri kaydetme](../data-tools/save-data-in-a-transaction.md)|System.Transactions ad alanı kullanarak bir işlemde veri kaydetme|  
|[Bir veritabanına (birden çok tablo) veri kaydetme](../data-tools/save-data-to-a-database-multiple-tables.md)|Nasıl kayıtlarını düzenleyin ve birden çok tablo veritabanına değişiklikleri kaydetmek için|  
|[Verileri bir nesneden veritabanına kaydetme](../data-tools/save-data-from-an-object-to-a-database.md)|Nasıl bir nesneden veritabanına bir veri kümesinde bir TableAdapter DbDirect yöntemi kullanarak değil veri geçirme|  
|[TableAdapter DBDirect metotlarıyla veri kaydetme](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)|SQL sorguları doğrudan veritabanına göndermek için TableAdapter'ı kullanma|  
|[Bir veri kümesini XML olarak kaydetme](../data-tools/save-a-dataset-as-xml.md)|Bir veri kümesi için bir XML belgesi kaydetme|  
  
## <a name="two-stage-updates"></a>İki aşamalı güncelleştirmeleri  
 Bir veri kaynağını güncelleştirme iki adımlı bir işlemdir. İlk adım, yeni kayıtlar, kayıtlar ve silinen kayıtlar ile DataSet'i güncellemek sağlamaktır. Uygulamanızı hiçbir zaman bu değişiklikleri veri kaynağına geri gönderirse, ardından güncelleştirme ile işiniz bittiğinde.  
  
 Değişiklikleri veritabanına geri göndermek, ikinci bir adım gereklidir. Verilere bağlı denetimler kullanmıyorsanız, el ile aynı TableAdapter (veya veri bağdaştırıcısı) DataSet'i doldurmak için kullanılan güncelleştirme yöntemi çağrısı vardır. Ancak, farklı bağdaştırıcıları verileri bir veri kaynağından diğerine taşımak için veya birden çok veri kaynaklarını güncelleştirmek için kullanabilirsiniz. Veri bağlama kullanmıyorsanız ve ilişkili tablolar için değişiklikleri kaydetme, el ile otomatik olarak oluşturulan TableAdapterManager sınıfın bir değişken oluşturma ve ardından kendi UpdateAll yöntemi çağırmak zorunda.  
  
 ![Visual Basic veri kümesi güncelleştirmeleri](../data-tools/media/vbdatasetupdates.gif "vbDatasetUpdates")  
İki aşamalı güncelleştirme işlemi ve DataRowVersion başarılı bir güncelleştirme görevi  
  
 Bir koleksiyon satır içeren tablolar, koleksiyonları bir veri kümesi içerir. Bir temel alınan veri kaynağına daha sonra güncelleştirmek istiyorsanız, DataTable.DataRowCollection özelliği eklerken veya kaldırırken satırları yöntemlerini kullanmanız gerekir. Bu yöntemleri veri kaynağını güncelleştirmek için gerekli olan değişiklik izleme gerçekleştirin. Satır özelliği RemoveAt koleksiyon çağırırsanız, silme veritabanına geri bildirilmesi olmaz.  
  
## <a name="merge-datasets"></a>Veri kümeleri birleştirme  
 Bir veri kümesi tarafından içeriğini güncelleştirebilirsiniz *birleştirme* başka bir veri kümesi ile. Bu içeriği kopyalamayı bir *kaynak* çağıran veri kümesine veri kümesi (olarak adlandırılan *hedef* veri kümesi). Veri kümeleri birleştirdiğinizde, kaynak veri kümesi yeni kayıt hedef veri kümesine eklenir. Ayrıca, kaynak veri kümesi ek sütunlar hedef veri kümesine eklenir. Veri kümeleri birleştirme yerel bir veri kümeniz ve başka bir uygulamadan ikinci bir veri kümesi alma kullanışlıdır. Ayrıca bir bileşenin bir XML web hizmeti gibi ikinci bir veri kümesi aldığınızda veya birden fazla veri kümesi verileri tümleştirin gerektiğinde kullanışlıdır.  
  
 Veri kümeleri birleştirme işlemi gerçekleştirirken, Boole bir bağımsız değişken geçirebilirsiniz (`preserveChanges`) başarılı olduğunu anlatan <xref:System.Data.DataSet.Merge%2A> yöntemi mi hedef kümesindeki var olan değişiklikleri saklamak. Veri kümeleri kayıtları birden çok sürümünü korumak için birden fazla sürüm kayıtlarının birleştirilmiş olduğunu aklınızda bulundurun önemlidir. Aşağıdaki tablo, bir kayıtta iki veri kümesi nasıl birleştirileceğini gösterir:  
  
|DataRowVersion|Hedef veri kümesi|Kaynak veri kümesi|  
|--------------------|--------------------|--------------------|  
|Özgün|James Wilson|James c Wilson|  
|Geçerli|Jim Wilson|James c Wilson|  
  
 Çağırma <xref:System.Data.DataSet.Merge%2A> yöntemi ile önceki tabloda `preserveChanges=false targetDataset.Merge(sourceDataset)` aşağıdaki sonuçları:  
  
|DataRowVersion|Hedef veri kümesi|Kaynak veri kümesi|  
|--------------------|--------------------|--------------------|  
|Özgün|James c Wilson|James c Wilson|  
|Geçerli|James c Wilson|James c Wilson|  
  
 Çağırma <xref:System.Data.DataSet.Merge%2A> yöntemiyle `preserveChanges = true targetDataset.Merge(sourceDataset, true)` aşağıdaki sonuçları:  
  
|DataRowVersion|Hedef veri kümesi|Kaynak veri kümesi|  
|--------------------|--------------------|--------------------|  
|Özgün|James c Wilson|James c Wilson|  
|Geçerli|Jim Wilson|James c Wilson|  
  
> [!CAUTION]
>  İçinde `preserveChanges = true` senaryosu, varsa <xref:System.Data.DataSet.RejectChanges%2A> hedef dataset kaydı yöntemi çağrılır, ardından özgün verilerin geri döner *kaynak* veri kümesi. Bu, hedef veri kümesi ile özgün veri kaynağını güncelleştirmek çalışırsanız, güncelleştirilecek özgün satır bulmak mümkün olmayabilir, anlamına gelir. Güncelleştirilmiş kayıtları veri kaynağından başka bir dataset doldurma ve ardından bir tutarlılık ihlali önlemek için birleştirme işlemi, bir eşzamanlılık ihlali engelleyebilirsiniz. (Veri kümesi doldurulmuş sonra başka bir kullanıcı bir veri kaynağındaki kaydı değiştirir. eşzamanlılık ihlali meydana gelir.)  
  
## <a name="update-constraints"></a>Kısıtlamaları güncelleştir  
 Mevcut bir veri satırı için değişiklik yapmak için ekleyin veya tek tek sütunlardaki verileri güncelleştirin. Veri kümesi (örneğin, yabancı anahtarlar veya NULL olmayan kısıtlamaları) kısıtlamaları içeriyorsa, bu güncelleştirme gibi kayıt geçici olarak bir hata durumunda olabilir mümkündür. Diğer bir deyişle, bir sütunu güncelleştirme işlemini tamamladıktan sonra ancak bir sonrakine geçmeden önce bir hata durumunda olabilir.  
  
 Erken sabiti ihlallerini önlemek için güncelleştirme kısıtlamaları geçici olarak askıya alabilirsiniz. Bu iki amaca hizmet eder:  
  
- Bir hata, bir sütunu güncelleştirme işlemi tamamlandı, ancak başka bir güncelleştirme başlamamış sonra durum engeller.  
  
- Bazı güncelleştirme engelleyen (genellikle doğrulama için kullanılan olayları) tetiklenen engeller olayları.  
  
  Güncelleştirme tamamlandıktan sonra kısıtlama denetimi, da güncelleştirme olaylarını yeniden etkinleştirir ve bunları başlatır, yeniden etkinleştirebilirsiniz.  
  
> [!NOTE]
>  Windows Formları datagrid içinde yerleşik veri bağlama mimarisi odağı bir satır dışında taşır ve açıkça çağırmanız gerekmez kadar denetleme kısıtlaması askıya alır. <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, veya <xref:System.Data.DataRow.CancelEdit%2A> yöntemleri.  
  
 Kısıtlamaları olan otomatik olarak devre dışı <xref:System.Data.DataSet.Merge%2A> yöntemi, bir veri kümesi üzerinde çağrılır. Birleştirme işlemi tamamlandığında kısıtlamalardan etkinleştirilemez, bir veri kümesini ise bir <xref:System.Data.ConstraintException> oluşturulur. Bu durumda <xref:System.Data.DataSet.EnforceConstraints%2A> özelliği `false,` ve tüm sabiti ihlallerini sıfırlamadan önce çözümlenmelidir <xref:System.Data.DataSet.EnforceConstraints%2A> özelliğini `true`.  
  
 Güncelleştirme tamamlandıktan sonra kısıtlama denetimi, da güncelleştirme olaylarını yeniden etkinleştirir ve bunları başlatır, yeniden etkinleştirebilirsiniz.  
  
 Olayları askıya almayla ilgili daha fazla bilgi için bkz. [bir veri kümesini doldururken kısıtlamaları kapatma kapatma](../data-tools/turn-off-constraints-while-filling-a-dataset.md).  
  
## <a name="dataset-update-errors"></a>Veri kümesi güncelleştirme hataları  
 Bir kayıt kümesindeki güncelleştirdiğinizde, hata olasılığı yoktur. Örneğin, bir sütuna, yanlış türde veri veya çok uzun veri ya da diğer bazı bütünlüğü sorunu olan verilerin yanlışlıkla yazabilirsiniz. Veya özel hatalar, herhangi bir güncelleştirme olay aşamasında yükseltebilirsiniz uygulamaya özgü doğrulama denetimlerini olabilir. Daha fazla bilgi için [veri kümelerindeki verileri doğrulama](../data-tools/validate-data-in-datasets.md).  
  
## <a name="maintaining-information-about-changes"></a>Değişiklikler hakkında bilgi koruma  
 Dataset içindeki değişiklikleri hakkında bilgi, iki yolla saklanır: Bunlar değiştiğini gösteren bir satır işaretlemesini tarafından (<xref:System.Data.DataRow.RowState%2A>) ve bir kayıt birden çok kopyasını tutarak (<xref:System.Data.DataRowVersion>). Bu bilgileri kullanarak, işlemler kümesinde nelerin değiştiğini belirlemek ve uygun güncelleştirmeleri veri kaynağına gönderebilirsiniz.  
  
### <a name="rowstate-property"></a>RowState özelliği  
 <xref:System.Data.DataRow.RowState%2A> Özelliği bir <xref:System.Data.DataRow> nesne belirli bir veri satırının durumu hakkında bilgi sağlayan bir değerdir.  
  
 Aşağıdaki tabloda olası değerlerini ayrıntıları <xref:System.Data.DataRowState> sabit listesi:  
  
|DataRowState değeri|Açıklama|  
|------------------------|-----------------|  
|<xref:System.Data.DataRowState>|Satır için bir öğe olarak eklenmiş olan bir <xref:System.Data.DataRowCollection>. (Bunu mevcut olmadığından bu durumdaki bir satır karşılık gelen bir özgün sürümüne sahip değil, son <xref:System.Data.DataRow.AcceptChanges%2A> yöntemi çağrıldı).|  
|<xref:System.Data.DataRowState>|Kullanarak satır silindi <xref:System.Data.DataRow.Delete%2A> , bir <xref:System.Data.DataRow> nesne.|  
|<xref:System.Data.DataRowState>|Satır oluşturuldu, ancak herhangi bir parçası değil <xref:System.Data.DataRowCollection>. A <xref:System.Data.DataRow> nesnesi oluşturulduktan sonra önce bir koleksiyonuna eklendikten hemen ve koleksiyondan kaldırıldıktan sonra bu durumda olan.|  
|<xref:System.Data.DataRowState>|Bir satırda sütun değeri şekilde değişti.|  
|<xref:System.Data.DataRowState>|Satır bu yana değişmemiştir <xref:System.Data.DataRow.AcceptChanges%2A> son çağrıldı.|  
  
### <a name="datarowversion-enumeration"></a>DataRowVersion numaralandırması  
 Veri kümeleri, birden çok sürümünü kayıtları korur. <xref:System.Data.DataRowVersion> Numaralandırması bir <xref:System.Data.DataRow> nesnedir, belirli bir sürümünü döndürmek için kullanılan bir değeri bir <xref:System.Data.DataRow> nesne.  
  
 Aşağıdaki tabloda olası değerlerini ayrıntıları <xref:System.Data.DataRowVersion> sabit listesi:  
  
|DataRowVersion değeri|Açıklama|  
|--------------------------|-----------------|  
|<xref:System.Data.DataRowVersion>|Bir kaydın geçerli sürümünü son daraltılmasından kayıt üzerinde gerçekleştirilen tüm değişiklikleri içeren <xref:System.Data.DataRow.AcceptChanges%2A> çağrıldı. Satır silinmiş olması durumunda geçerli sürümü yoktur.|  
|<xref:System.Data.DataRowVersion>|Veri kümesi şemasını veya verileri kaynak tarafından tanımlanan bir kaydı, varsayılan değeri.|  
|<xref:System.Data.DataRowVersion>|Son saat değişikliklerini kümesinde kaydedilmiş haliyle bir kaydın orijinal sürümünü kayıt kopyasıdır. Pratikte, bu genellikle bir kaydın okundu olarak bir veri kaynağından sürümüdür.|  
|<xref:System.Data.DataRowVersion>|Ortasında bir güncelleştirme çalışırken geçici olarak kullanılabilir bir kaydın önerilen sürüm — diğer bir deyişle, arasındaki süreyi aradığınız <xref:System.Data.DataRow.BeginEdit%2A> yöntemi ve <xref:System.Data.DataRow.EndEdit%2A> yöntemi. Genellikle bir kayıttaki bir olay işleyicisi önerilen sürümü gibi erişim <xref:System.Data.DataTable.RowChanging>. Çağırma <xref:System.Data.DataRow.CancelEdit%2A> yöntemi değişiklikleri geri alır ve önerilen sürümü veri satırı siler.|  
  
 Geçerli ve orijinal sürümler, bir veri kaynağına güncelleştirme bilgileri iletilirken yararlıdır. Veri kaynağına gönderilen bir güncelleştirme olduğunda, genellikle yeni veritabanı için bir kayıt geçerli sürümünde bilgilerdir. Özgün sürümle bilgileri güncelleştirilecek kaydın bulmak için kullanılır.  
  
 Örneğin, burada bir kaydın birincil anahtarı değiştirildiğinde bir durumda, doğru kaydı değişiklikleri güncelleştirmek için veri kaynağı bulmak için bir yol gerekir. Özgün sürüm varsa, ardından kayıt büyük olasılıkla yalnızca bir ek istenmeyen kaydındaki ancak yanlış ve güncel bir kayıtta kaynaklanan veri kaynağına eklenmiş olacaktı. İki sürümü de eşzamanlılık denetimi kullanılır. Kayıt kümesine yüklendiğinden bu yana değişip değişmediğini belirlemek için veri kaynağındaki bir kaydı karşı özgün sürümle karşılaştırabilirsiniz.  
  
 Önerilen sürüm, aslında veri kümesine değişiklikleri gerçekleştirmeden önce doğrulamayı gerçekleştirmek gerektiğinde faydalıdır.  
  
 Kayıtları değiştirilmiş olsa bile, yok her zaman özgün ya da geçerli satır sürümleri. Tabloya yeni bir satır ekleyin, özgün sürümü, yalnızca geçerli sürümü yoktur. Benzer şekilde, tablonun çağırarak bir satır silerseniz `Delete` yöntemi, orijinal bir sürümünü kullanır, ancak hiçbir geçerli sürümü yoktur.  
  
 Bir veri sıranın sorgulayarak bir kaydın belirli bir sürümü olup olmadığını sınayabilirsiniz <xref:System.Data.DataRow.HasVersion%2A> yöntemi. Ya da bir kaydın sürümünü geçirerek erişebileceğiniz bir <xref:System.Data.DataRowVersion> numaralandırma değeri olarak isteğe bağlı bağımsız değişken bir sütunun değerini istediğinizde.  
  
## <a name="getting-changed-records"></a>Kayıtlar alınıyor  
 Bir veri kümesindeki tüm kayıtların güncelleştirmeyi yaygın bir uygulamadır. Örneğin, bir kullanıcı bir Windows Forms ile çalışmıyor olabilir <xref:System.Windows.Forms.DataGridView> çok sayıda kayıt görüntüleyen denetim. Ancak, kullanıcı yalnızca birkaç kayıtları güncelleştirmek, silmek ve yeni bir tane ekleyin. Veri kümeleri ve veri tabloları bir yöntem sunar (`GetChanges`) değiştirilmiş satırları döndürmek için.  
  
 Kullanarak değiştirilmiş kayıt kümelerine oluşturabilirsiniz `GetChanges` veri tablosunun yöntemi (<xref:System.Data.DataTable.GetChanges%2A>) veya veri kümesinin (<xref:System.Data.DataSet.GetChanges%2A>) kendisi. Veri tablosu için yöntem çağırırsanız, tablo yalnızca değiştirilen kayıtları ile birlikte bir kopyasını döndürür. Veri kümesi üzerinde yöntem çağırırsanız, benzer şekilde, yalnızca kayıtlar ile yeni bir veri kümesi içinde olursunuz.  
  
 `GetChanges` tek başına değişen tüm kayıtları döndürür. Buna karşılık, geçirerek istenen <xref:System.Data.DataRowState> bir parametre olarak `GetChanges` yöntemi, hangi istediğiniz değiştirilmiş kayıt kümesini belirtebilirsiniz: yeni kayıtlar, silinmek üzere işaretlenmiş kayıtları ayrılmış kayıtları eklendi veya değiştirilmiş kayıtlar.  
  
 Bir alt kümesini kayıtlar alınırken işleme için başka bir bileşen kayıtları göndermek istediğinizde yararlıdır. Veri kümesinin tamamının göndermek yerine yalnızca bileşen gereken kayıtları alarak başka bir bileşen ile iletişim kurulurken yükünü azaltabilir. Daha fazla bilgi için [nasıl yapılır: değiştirilen satırları alma](http://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9).  
  
## <a name="committing-changes-in-the-dataset"></a>Veri kümesi değişiklikleri işleme  
 Veri kümesindeki değişiklikler yapıldıkça <xref:System.Data.DataRow.RowState%2A> değiştirilen satırların özelliği ayarlanmış. Kayıtları geçerli ve özgün sürümlerini oluşturulan, korunur ve size sunulan <xref:System.Data.DataRowView.RowVersion%2A> özelliği. Bu değiştirilen satırların özelliklerinde depolanan meta veriler, doğru güncelleştirmeleri veri kaynağına göndermek için gereklidir.  
  
 Değişiklikleri veri kaynağına geçerli durumu yansıtacak, artık bu bilgileri sürdürmeniz gerekir. Genellikle, veri kümesini ve kaynağı zaman eşitlenmiş durumda iki kez vardır:  
  
- Hemen sonra ne zaman veri kaynağından okumak kümesine bilgi yüklediniz.  
  
- Değişiklikleri veri kaynağına, veri kümesinden gönderdikten sonra (ancak daha önce değil çünkü veritabanına değişiklikleri göndermek için gereken değişiklik bilgileri kaybedersiniz).  
  
  Veri kümesine ilişkin bekleyen değişiklikleri çağırarak yürütülemez <xref:System.Data.DataSet.AcceptChanges%2A> yöntemi. Genellikle, <xref:System.Data.DataSet.AcceptChanges%2A> uygulamanızda aşağıdaki saatleri sırasında çağrılır.  
  
- Sonra veri kümesine yükler. Bir veri kümesi, yük TableAdapter bağdaştırıcısının çağırarak `Fill` yöntemi sonra bağdaştırıcı otomatik olarak tamamlar değişiklikleri sizin için. Bir veri kümesi içine başka bir veri kümesini birleştirerek yüklerseniz, ancak, daha sonra değişiklikleri el ile kaydetmek gerekir.  
  
  > [!NOTE]
  >  Bağdaştırıcı çağırdığınızda otomatik olarak değişiklikleri yürütmeyi öğesinden engelleyebilirsiniz `Fill` ayarlayarak yöntemi `AcceptChangesDuringFill` bağdaştırıcısının özellik `false`. Bu ayarlanırsa `false`, ardından <xref:System.Data.DataRow.RowState%2A> doldurma sırasında eklenen her bir satır kümesine <xref:System.Data.DataRowState>.  
  
- XML Web hizmeti gibi başka bir işlem için veri kümesi değişiklikleri gönderdikten sonra.  
  
  > [!CAUTION]
  >  Bu şekilde ardından değişikliği uygulamayı herhangi bir değişiklik bilgi siler. Değil değişiklikleri kadar çalıştırdıktan sonra uygulamanızı kümesinde hangi değişiklikler yapılmıştır bilmek gerektiren işlemler gerçekleştirme son.  
  
  Bu yöntem, aşağıdakileri yerine getirir:  
  
- Yazar <xref:System.Data.DataRowVersion> bir kayıtta sürümü kendi <xref:System.Data.DataRowVersion> sürümü ve özgün sürümle üzerine yazar.  
  
- Satırları kaldıran burada <xref:System.Data.DataRow.RowState%2A> özelliği <xref:System.Data.DataRowState>.  
  
- Kümeleri <xref:System.Data.DataRow.RowState%2A> özelliği için bir kaydın <xref:System.Data.DataRowState>.  
  
  <xref:System.Data.DataSet.AcceptChanges%2A> Yöntemi üç düzeyde kullanılabilir. Üzerinde çağırmak bir <xref:System.Data.DataRow> işlemeler için nesne yalnızca bu satır için değişiklikleri. Üzerinde de çağırabilirsiniz bir <xref:System.Data.DataTable> bir tablodaki tüm satırları işlemek için nesne. Üzerinde çağrı son olarak, <xref:System.Data.DataSet> nesnenin tüm kayıtları veri kümesinin tüm tabloların tüm bekleyen değişiklikleri kaydedin.  
  
  Aşağıdaki tablo, hangi yöntemin çağrıldığı nesne üzerinde göre hangi değişiklikler uygulandıktan açıklar.  
  
|Yöntem|Sonuç|  
|------------|------------|  
|<xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>|Yalnızca belirli satırda değişiklikler uygulanır.|  
|<xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>|Değişiklikler, belirli bir tablodaki tüm satırlar üzerinde uygulanır.|  
|<xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>|Değişiklik kümesinin tüm tablolardaki tüm satırları üzerinde uygulanır.|  
  
> [!NOTE]
>  Bir veri kümesi, yük TableAdapter bağdaştırıcısının çağırarak `Fill` yöntemi, açıkça değişiklikleri kabul etmek zorunda değilsiniz. Varsayılan olarak, `Fill` yöntem çağrılarını `AcceptChanges` veri tablosunu doldurmak bittikten sonra yöntemi.  
  
 İlgili bir yöntem `RejectChanges`, değişikliklerin etkisini kopyalayarak alır <xref:System.Data.DataRowVersion> sürümüne geri <xref:System.Data.DataRowVersion> kayıtları sürümü. Ayrıca ayarlar <xref:System.Data.DataRow.RowState%2A> , her kayıt geri <xref:System.Data.DataRowState>.  
  
## <a name="data-validation"></a>Veri doğrulama  
 Uygulamanızdaki verileri için geçirilen işlemlerin gereksinimlerini karşıladığını doğrulamak için genellikle doğrulama eklemeniz gerekir. Bu form kullanıcının girişi uygulamanız başka bir uygulama tarafından gönderilen verileri doğrulama ya da devre dışı bile bileşeninizin içinde hesaplanan bilgi veri kaynağınızın kısıtlamaları içinde kalan denetimi doğru olup olmadığını denetleyerek gerektirebilir ve uygulama gereksinimleri.  
  
 Verileri farklı şekillerde doğrulayabilirsiniz:  
  
- Verileri doğrulamak için uygulamanıza kod ekleyerek iş katmanı içinde. Veri kümesi, bunu yapmak için bir yerdir. Arka uç doğrulama avantajlarından bazıları veri kümesi sağlar; sütun ve satır değerleri değiştirme gibi değişiklikleri doğrulamak için özelliği gibi. Daha fazla bilgi için [veri kümelerindeki verileri doğrulama](../data-tools/validate-data-in-datasets.md).  
  
- Doğrulama formlar ekleyerek sunu katmanda. Daha fazla bilgi için [Windows Forms'ta kullanıcı girdisi doğrulama](http://msdn.microsoft.com/library/4ec07681-1dee-4bf9-be5e-718f635a33a1).  
  
- Veri kaynağına veri gönderen tarafından arka uç, verileri — Örneğin, veritabanı — ve kabul etme veya reddetme veri olanak tanır. Verileri doğrulama ve hata bilgilerini sağlayarak olanakları karmaşık bir veritabanı ile çalışıyorsanız, verilerin nereden geldiğini ne olursa olsun doğrulayabilirsiniz çünkü bu pratik bir yaklaşım olabilir. Ancak, bu yaklaşım uygulamaya özgü doğrulama gereksinimlerini karşılamaya değil. Ayrıca, verileri doğrulama veri kaynağına sahip çok sayıda gidiş dönüş içinde nasıl, uygulamanızın arka ucu tarafından oluşturulan doğrulama hatalarını çözümlenmesi kolaylaştırır bağlı olarak veri kaynağına neden olabilir.  
  
  > [!IMPORTANT]
  >  Veri komutları ile kullanırken bir <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> ayarlanan özellik <xref:System.Data.CommandType>, dikkatli bir şekilde veritabanına geçirmeden önce bir istemciden gönderilen bilgilere bakın. Kötü amaçlı kullanıcılara gönderilecek deneyin (Ekle) yetkisiz erişim veya veritabanı zarar vermek için çaba değiştirilmiş veya ek SQL deyimlerinde. Bir veritabanına kullanıcı girişi aktarmadan önce her zaman bilgilerin geçerli olduğunu doğrulayın. Parametreli sorgular veya saklı yordamları mümkün olduğunda kullanılması her zaman iyi bir uygulamadır. Daha fazla bilgi için [betik yararlanan genel bakış](http://msdn.microsoft.com/library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07).  
  
  Bir veri kümesinde değişiklik yapıldıktan sonra değişiklikleri veri kaynağına aktarabilir. En yaygın olarak, çağrı yaparak bunu `Update` yöntemi bir TableAdapter (veya veri bağdaştırıcısı). Her bir veri tablosu kayıt yöntemi döner belirler ne tür bir güncelleştirme gerekli değildir (güncelleştirme, ekleme veya silme), varsa, ve ardından uygun komutu çalıştırır.  
  
## <a name="transmitting-updates-to-the-data-source"></a>Veri kaynağına aktaran güncelleştirmeleri  
 Güncelleştirmeleri nasıl yapılacağını ilişkin bir çizim, uygulamanızın kullandığı bir tek veri tablosu içeren bir veri kümesi varsayalım. Uygulama, iki satır veritabanından veri getirir. Sonra alma, bellek içi verileri tablo şöyle görünür:  
  
```  
(RowState)     CustomerID   Name             Status  
(Unchanged)    c200         Robert Lyon      Good  
(Unchanged)    c400         Nancy Buchanan    Pending  
```  
  
 Uygulamanız, Gamze Koç'ın durumu "Tercih edilen olarak." değiştirir. Değeri, bu değişikliğin sonucu olarak <xref:System.Data.DataRow.RowState%2A> ilgili satır için özelliği değişir <xref:System.Data.DataRowState> için <xref:System.Data.DataRowState>. Değerini <xref:System.Data.DataRow.RowState%2A> özelliği ilk satır için kalan <xref:System.Data.DataRowState>. Veri tablosu artık şöyle görünür:  
  
```  
(RowState)     CustomerID   Name             Status  
(Unchanged)    c200         Robert Lyon      Good  
(Modified)     c400         Nancy Buchanan    Preferred  
```  
  
 Uygulama şimdi çağrılarınızı `Update` dataset veritabanına aktarmak için yöntemi. Yöntemi, her satır sırayla denetler. Başlangıçta veritabanından getirildikten sonra satır değişmediği için ilk satırında, veritabanına herhangi bir SQL deyimi yöntemi iletir.  
  
 İkinci satır, ancak `Update` yöntemi otomatik olarak doğru veri komutu çağırır ve veritabanına iletir. Belirli bir söz dizimi SQL deyiminin temel veri deposu tarafından desteklenen bir SQL diyalekti bağlıdır. Ancak, aşağıdaki genel özellikleri iletilen SQL deyiminin kayda değer:  
  
-   İletilen SQL deyimi, bir güncelleştirme ifadedir. Bir UPDATE deyimi için kullanılacak bağdaştırıcı bilir değerini <xref:System.Data.DataRow.RowState%2A> özelliği <xref:System.Data.DataRowState>.  
  
-   İletilen SQL deyimi UPDATE deyiminin hedefi satır olduğunu belirten bir WHERE yan tümcesi içeren burada `CustomerID = 'c400'`. Bu bölüm SELECT deyiminin hedef satır tüm başkalarından çünkü ayıran `CustomerID` hedef tablonun birincil anahtarı. WHERE yan tümcesi kaydının özgün sürümden türetilen bilgileri (`DataRowVersion.Original`), satır tanımlamak için gerekli değerleri değişmesi durumunda.  
  
-   Değiştirilen sütun yeni değerleri ayarlamak için SET yan tümcesi iletilen SQL deyimi içerir.  
  
    > [!NOTE]
    >  TableAdapter bağdaştırıcısının `UpdateCommand` özelliği bir saklı yordam adı için ayarlandı, bağdaştırıcı SQL deyimi oluşturmak değil. Bunun yerine uygun parametrelerle geçirilen saklı yordamını çağırır.  
  
## <a name="passing-parameters"></a>Parametreleri geçirme  
 Genellikle veritabanında güncelleştirilebilir gidip kayıtlar için değerleri geçirmek için parametreleri kullanın.  TableAdapter bağdaştırıcısının `Update` yöntemi bir UPDATE deyimi çalıştırır, parametre değerlerini doldurmanız gerekir. Bu değerleri alır `Parameters` uygun veri komutu için koleksiyon — bu durumda, `UpdateCommand` TableAdapter nesne.  
  
 Bir veri bağdaştırıcısı oluşturmak için Visual Studio Araçları kullandıysanız `UpdateCommand` nesne her parametre yer tutucu deyiminde karşılık gelen parametrelerin bir koleksiyonunu içerir.  
  
 <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A?displayProperty=fullName> Özelliği, her parametrenin veri tablosunda bir sütun işaret eder. Örneğin, `SourceColumn` özelliği `au_id` ve `Original_au_id` parametreleri, veri tablodaki hangi sütunun Yazar kimliğini içeren için ayarlanır. Olduğunda bağdaştırıcının `Update` yöntemi çalıştığında, yazar kimlik sütunu güncelleştiriliyor ve değerleri ifadesine doldurur kaydı okur.  
  
 UPDATE deyiminde, her iki yeni değerler (Bu kaydı için yazılır) eski değerleri olarak (kayıt veritabanında konumlandırılabilir böylece) belirtmeniz gerekir. Bu nedenle her bir değer için iki parametre vardır: biri SET yan tümcesi, farklı bir WHERE yan tümcesi için. Her iki parametre güncelleştirilmekte kayıttan veri okuma, ancak bunlar farklı sürümlerini parametresine ait bağlı sütun değeri elde [SqlParameter.SourceVersion özelliği](https://msdn.microsoft.com/library/system.data.sqlclient.sqlparameter.sourceversion.aspx). Geçerli sürüm parametresi SET yan tümcesi için alır ve özgün sürümle WHERE yan tümcesi için parametre alır.  
  
> [!NOTE]
>  De değerlerini ayarlayabilirsiniz `Parameters` koleksiyon kendiniz bir olay işleyicisi veri bağdaştırıcının için genellikle yaptığınız kodlarda <xref:System.Data.DataTable.RowChanging> olay.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TableAdapter genel bakış](../data-tools/tableadapter-overview.md)   
 [TableAdapter kullanarak verileri güncelleştirme](../data-tools/update-data-by-using-a-tableadapter.md)   
 [Veri uygulamaları Visual Studio'da genel bakış](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Visual Studio'da verilere bağlanma](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Uygulamanızı veri almaya hazırlama](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Uygulamanıza veri getirme](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Uygulamanızdaki verileri düzenleme](../data-tools/editing-data-in-your-application.md)   
 [Verileri doğrulama](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Verileri Kaydetme](../data-tools/saving-data.md)

