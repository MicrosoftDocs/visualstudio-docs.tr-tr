---
title: Hiyerarşik güncelleştirme | Microsoft Docs
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
- saving data, changed data
- data [Visual Basic], hierarchical update
- saving updated data
- datasets [Visual Basic], hierarchical update
- hierarchical update
- saving data, hierarchical update
- modified data saving
- updated data saving
- related tables, saving
ms.assetid: 68bae3f6-ec9b-45ee-a33a-69395029f54c
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d0176f203f7decb701d678a110856acdad36750b
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220185"
---
# <a name="hierarchical-update"></a>Hiyerarşik güncelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Hiyerarşik güncelleştirme * tutarlılığı korurken (bir veri kümesinden iki veya daha fazla ilgili tablo ile) güncelleştirilmiş verileri bir veritabanına geri kaydediliyor işlemini ifade eder. *Bilgi tutarlılığını* veritabanında ve ekleme, güncelleştirme ve ilgili kayıt silme davranışını kontrol kısıtlamaları tarafından sağlanan tutarlık kuralları ifade eder. Örneğin, o müşteri için oluşturulacak siparişler izin vermeden önce bir müşteri kaydı oluşturulmasını zorlar tutarlılığı olur.  Veri kümelerindeki ilişkiler hakkında daha fazla bilgi için bkz: [veri kümelerindeki ilişkiler](../data-tools/relationships-in-datasets.md)  
  
 Hiyerarşik güncelleştirme özelliğini kullanan bir `TableAdapterManager` yönetmek için `TableAdapter`s'te bir türü belirtilmiş veri kümesi. `TableAdapterManager` Bileşeni bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-sınıfı, bu şekilde oluşturulan parçası [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Bir tablo veri kaynakları penceresinden bir Windows Form veya WPF sayfasına sürüklediğinizde, Visual Studio TableAdapterManager türünde bir değişken bir form veya sayfa ekler ve bileşen tepsisinde Tasarımcısı'nda bkz. İlgili ayrıntılı bilgi için `TableAdapterManager` TableAdapterManager başvuru bölümüne bakın, sınıf [TableAdapterManager genel bakışı](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650).  
  
 Varsayılan olarak, bir veri kümesi ilişkili tablolar "yalnızca ilişkileri" yabancı anahtar kısıtlamaları zorunlu değildir, yani değerlendirir. Veri kümesi Tasarımcısı kullanarak tasarım zamanında bu ayarı değiştirebilirsiniz. Ortaya çıkarmak için iki tablo arasında ilişki satırı **ilişkisi** iletişim kutusu. Burada yaptığınız değişiklikler TableAdapterManager ne zaman nasıl davranacağını belirlemek göndermeden değişiklikleri ilişkili tabloların veritabanına geri.  
  
## <a name="enablehierarchical-update-in-a-dataset"></a>Bir veri kümesindeki Enablehierarchical güncelleştirme  
 Varsayılan olarak, hiyerarşik güncelleştirme eklenen ya da bir projede oluşturulan tüm yeni veri kümeleri için etkinleştirilir. Hiyerarşik güncelleştirme Aç veya kapat ayarlayarak **hiyerarşik güncelleştirme** bir türü belirtilmiş veri kümesinde özelliği [oluşturma ve yazılan veri kümelerini düzenleme](../data-tools/creating-and-editing-typed-datasets.md) için **True** veya **False**:  
  
 ![Hiyerarşik güncelleştirme ayarı](../data-tools/media/hierarchical-update-setting.png "hiyerarşik güncelleştirme ayarı")  
  
## <a name="create-a-new-relation-between-tables"></a>Yeni tablolar arasında ilişki oluşturma  
 İki tablo arasında yeni bir ilişki oluşturmak için veri kümesi Tasarımcısı'nda, her tablonun başlık çubuğunu seçin, sonra sağ tıklayıp**ilişkisi ekleme**.  
  
 ![Hiyerarşik güncelleştirme ilişkisi menü Ekle](../data-tools/media/hierarchical-update-add-relation-menu.png "hiyerarşik güncelleştirme ilişkisi menü ekleme")  
  
## <a name="understand-foreign-key-constraints-cascading-updates-and-deletes"></a>Yabancı anahtar kısıtlamaları, geçişli güncelleştirme ve silme anlama  
 Nasıl FOREIGN key kısıtlamalarını anlamak önemlidir ve davranışı veritabanındaki geçişli üretilen veri kümesi kod oluşturulur.  
  
 Varsayılan olarak, bir veri kümesindeki veri tablolarının ilişkilerle oluşturulur (<xref:System.Data.DataRelation>) ilişkileri veritabanında eşleşen. Ancak, ilişki veri kümesinde yabancı anahtar kısıtlama olarak oluşturulmaz. <xref:System.Data.DataRelation> Olarak yapılandırılmış **ilişkisi yalnızca** olmadan <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> veya <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> etkin.  
  
 Varsayılan olarak, geçişli güncelleştirmeler ve silmeleri basamaklı güncelleştirmeleriyle veritabanı ilişkisi ve/veya silmenin açık olsa bile devre dışı bırakılmıştır. Örneğin, yeni bir müşteri ve yeni bir sipariş oluşturmak ve ardından veri kaydetmeye çalışırken bir çakışma veritabanında tanımlanan yabancı anahtar kısıtlamalarıyla neden olabilir. Daha fazla bilgi için [nasıl yapılır: bir veri kümesinde yabancı anahtar kısıtlamaları yapılandırmak](http://msdn.microsoft.com/library/3954c388-e209-4a67-a34e-5ca106282f8e).  
  
## <a name="set-the-order-to-perform-updates"></a>Güncelleştirmeleri gerçekleştirmek için sırasını ayarlama  
 Güncelleştirmeleri gerçekleştirmek için sırasını ayarlama ekler, güncelleştirir ve silme işlemlerini ayrı ayrı sırasını ayarlar tüm değiştirilmiş verileri bir veri kümesinin tüm tablolarda kaydetmek için gereklidir. Hiyerarşik güncelleştirme etkinleştirildiğinde, ekler önce gerçekleştirilir sonra güncelleştirir ve siler. `TableAdapterManager` Sağlayan bir `UpdateOrder` özelliği, ilk olarak, güncelleştirmeleri gerçekleştirmek üzere sonra ekler ve siler.  
  
> [!NOTE]
>  Güncelleştirme sırası her şey dahil olduğunu anlamak önemlidir. Güncelleştirme yapıldığında, diğer bir deyişle, ekleme ve silme kümesindeki tüm tabloların gerçekleştirilir.  
  
 Ayarlanacak `UpdateOrder` sürüklemeye sonra özelliği [veri kaynakları penceresi](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) bir forma seçin `TableAdapterManager` bileşeni Tepsi ve ardından `UpdateOrder` özelliğinde **özellikleri** penceresi. Daha fazla bilgi için [nasıl yapılır: hiyerarşik güncelleştirme sırası olduğunda gerçekleştirme ayarlayın](http://msdn.microsoft.com/library/a0734935-78dd-4c0b-80d7-5e7925789c83).  
  
## <a name="create-a-backup-copy-of-a-dataset-before-performing-a-hierarchical-update"></a>Hiyerarşik güncelleştirme gerçekleştirmeden önce yedek bir kopyası, bir veri kümesi oluşturma  
 Veri kaydettiğinizde (çağırarak `TableAdapterManager.UpdateAll()` yöntemi), `TableAdapterManager` tek bir işlemde her tablo için verileri güncelleştirmek çalışır. Herhangi bir bölümünü herhangi bir tabloda güncelleştirmesi başarısız olursa, tüm işlem geri alınır. Çoğu durumda, uygulamanızı özgün durumuna geri döndürür.  
  
 Ancak, bazen dataset yedek kopyadan geri yüklemek isteyebilirsiniz. Otomatik artış değerlerini kullanırken bu gerçekleşebilir. Örneğin, kaydetme işlemi başarılı değil, otomatik artış değerleri kümesinde sıfırlanır ve veri kümesini otomatik artan değerleri oluşturmak devam eder. Bu, uygulamanızda kabul edilebilir olmayabilir, numaralandırma, boşluk bırakır. Durumlarda bu bir sorun olduğu `TableAdapterManager` sağlayan bir `BackupDataSetBeforeUpdate` özelliği, işlem başarısız olursa mevcut veri kümesini bir yedek kopyasıyla değiştirir.  
  
> [!NOTE]
>  Yedekleme sırasında bellekte yalnızca kopyasıdır `TableAdapterManager.UpdateAll` yöntemi çalışıyor. Bu nedenle, programlı erişimi yoktur yedekleme bu veri kümesine özgün veri kümesinden değiştirir ya kapsamın dışına çıkıncaya çünkü hemen sonra `TableAdapterManager.UpdateAll` yöntemi tamamlandıktan çalışıyor.  
  
## <a name="modify-the-generated-save-code-to-perform-the-hierarchical-update"></a>Oluşturulan kodu hiyerarşik güncelleştirmeyi gerçekleştirmek için ' değiştirin  
 Değişiklik kümesindeki ilgili veri tablolarında veritabanına çağırarak kaydetmek `TableAdapterManager.UpdateAll` yöntemi ve ilişkili tabloları içeren bir veri kümesi adını geçirerek. Örneğin, `TableAdapterManager.UpdateAll(NorthwindDataset)` NorthwindDataset tüm tablolardaki için arka uç veritabanı güncelleştirmeleri göndermek için yöntemi.  
  
 Öğeleri bırak sonra **veri kaynakları** penceresinde kodu otomatik olarak eklenir `Form_Load` her tabloyu doldurmak için olay ( `TableAdapter.Fill` yöntemleri). Kodu da eklenir **Kaydet** düğme tıklatma olayını, <xref:System.Windows.Forms.BindingNavigator> veri kümesinden veritabanına geri kaydedin ( `TableAdapterManager.UpdateAll` yöntemi).  
  
 Oluşturulan kodu kaydetmek bir çağıran kod satırı içerecek `CustomersBindingSource.EndEdit` yöntemi. Özellikle, çağıran <xref:System.Windows.Forms.BindingSource.EndEdit%2A> yöntemi ilk <xref:System.Windows.Forms.BindingSource>formuna eklenir. Diğer bir deyişle, bu kod yalnızca gelen sürüklediğiniz ilk tablo için oluşturulan **veri kaynakları** forma penceresi. <xref:System.Windows.Forms.BindingSource.EndEdit%2A> Çağrısı şu anda düzenlenmekte olan herhangi bir veriye bağlı denetim işleminde değişiklikleri kaydeder. Odak ve bu nedenle, bir veri bağlı denetim hala varsa tıklayın **Kaydet** denetim kaydedilir, gerçek kaydetme önce tüm bekleyen düzenlemeler düğmesine ( `TableAdapterManager.UpdateAll` yöntemi).  
  
> [!NOTE]
>  Dataset Designer yalnızca ekler `BindingSource.EndEdit` forma bırakılan ilk tablo için kod. Bu nedenle, bir çağırmak için kod satırı eklemeniz gerekir `BindingSource.EndEdit` formunda ilgili her tablo için yöntemi. Bu kılavuz için bu çağrı eklemek sahip olduğunuz anlamına gelir `OrdersBindingSource.EndEdit` yöntemi.  
  
#### <a name="to-update-the-code-to-commit-changes-to-the-related-tables-before-saving"></a>Kod değişiklikleri kaydetmeden önce ilişkili tabloları için güncelleştirmek için  
  
1. Çift **Kaydet** düğmesini <xref:System.Windows.Forms.BindingNavigator> açmak için **Form1** Kod Düzenleyicisi'nde.  
  
2. Çağırmak için kod satırını ekleyin `OrdersBindingSource.EndEdit` yöntemi çağıran satırdan `CustomersBindingSource.EndEdit` yöntemi. Kodda **Kaydet** düğmesi tıklamasından olay aşağıdaki benzemesi gerekir:  
  
    [!code-csharp[VSProDataOrcasHierarchicalUpdate#1](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/CS/Form1.cs#1)]
    [!code-vb[VSProDataOrcasHierarchicalUpdate#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/VB/Form1.vb#1)]  
  
   Verileri bir veritabanına kaydetme önce ilgili alt tablo üzerinde değişiklikler işleniyor ek olarak, bir veri kümesi için yeni alt kayıtları eklemeden önce yeni oluşturulan işleme üst kayıtlar için de olabilir. Yeni alt kayıtları (veri kümesine eklenecek siparişler) yabancı anahtar kısıtlamalarını etkinleştirmeden önce başka bir deyişle, yeni üst kayıt (müşteri) eklemek veri kümesine olabilir. Bunu yapmak için alt kullanabilirsiniz `BindingSource.AddingNew` olay.  
  
> [!NOTE]
>  Yeni üst kayıtlar işleme gerekip gerekmediğini, veri kaynağına bağlamak için kullanılan denetim türünü bağlıdır. Bu kılavuzda, üst tabloya bağlamak için tek tek denetimleri kullanın. Bu, yürütme yeni üst kaydı için ek kod gerektirir. Bunun yerine üst kayıtlar Karmaşık bağlama denetimde görüntülenen hoşlanıyorsanız <xref:System.Windows.Forms.DataGridView>, bu ek <xref:System.Windows.Forms.BindingSource.EndEdit%2A> ana kayıt gerekli olmaz için çağırın. Temel alınan veri bağlama denetimi işlevlerini yürüten yeni kayıtları işleme olmasıdır.  
  
#### <a name="to-add-code-to-commit-parent-records-in-the-dataset-before-adding-new-child-records"></a>Yeni alt kayıtları eklemeden önce üst kayıtlar veri kümesini yürütmek için kodu eklemek için  
  
1.  İçin bir olay işleyicisi oluşturun `OrdersBindingSource.AddingNew` olay.  
  
    -   Açık **Form1** Tasarım görünümünde seçin **OrdersBindingSource** bileşen tepsisinde seçin **olayları** içinde **özellikleri** penceresinde ve ardından çift **AddingNew** olay.  
  
2.  Çağıran olay işleyicisine kod satırını ekleyin `CustomersBindingSource.EndEdit` yöntemi. Kodda `OrdersBindingSource_AddingNew` olay işleyicisi aşağıdaki benzemesi gerekir:  
  
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#2](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/CS/Form1.cs#2)]
     [!code-vb[VSProDataOrcasHierarchicalUpdate#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/VB/Form1.vb#2)]  
  
## <a name="tableadaptermanager-reference"></a>TableAdapterManager başvurusu  
 Varsayılan olarak, bir `TableAdapterManager` sınıfı ilişkili tabloları içeren bir veri kümesi oluşturduğunuzda oluşturulur. Sınıf oluşturulmasını önlemek için değerini değiştirmek `Hierarchical Update` özelliği false kümesi. WPF sayfası ya da Windows Form Tasarım yüzeyine bir ilişkisi olan bir tabloda sürüklediğinizde, Visual Studio sınıfının bir üye değişkeni bildirir. Veri bağlama kullanmazsanız, el ile değişkenini tanımlamak zorunda.  
  
 `TableAdapterManager` Sınıfı değil parçası [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Bu nedenle, bu belgelerde bakarak olamaz. Tasarım zamanında veri kümesi oluşturma işleminin bir parçası olarak oluşturulur.  
  
 Sık kullanılan yöntemleri ve özellikleri verilmiştir `TableAdapterManager` sınıfı:  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`UpdateAll` Yöntemi|Tüm veriler, tüm veri tablolarından kaydeder.|  
|`BackUpDataSetBeforeUpdate` Özelliği|Yürütmeden önce yedek bir kopyası, veri kümesinin oluşturulup oluşturulmayacağını belirler `TableAdapterManager.UpdateAll` yöntemi. Boole değeri.|  
|*tableName* `TableAdapter` özelliği|Temsil eden bir `TableAdapter`. Oluşturulan `TableAdapterManager` her biri için bir özellik içeriyor `TableAdapter` yönettiği. Örneğin, müşteriler ve siparişler bir tablo olan bir veri kümesi ile oluşturulan bir `TableAdapterManager` içeren `CustomersTableAdapter` ve `OrdersTableAdapter` özellikleri.|  
|`UpdateOrder` Özelliği|Ayrı ayrı INSERT, update ve delete komutlarını sırasını denetler. Bu değerler birine `TableAdapterManager.UpdateOrderOption` sabit listesi.<br /><br /> Varsayılan olarak, `UpdateOrder` ayarlanır **InsertUpdateDelete**. Ekler, sonra güncelleştirir ve siler Bunun anlamı, veri kümesindeki tüm tabloların gerçekleştirilir. Daha fazla bilgi için [nasıl yapılır: hiyerarşik güncelleştirme sırası olduğunda gerçekleştirme ayarlayın](http://msdn.microsoft.com/library/a0734935-78dd-4c0b-80d7-5e7925789c83).|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)

