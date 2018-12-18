---
title: Basit veri bağlamayı destekleyen bir Windows Forms kullanıcı denetimi oluşturun | Microsoft Docs
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
- custom controls [Visual Studio], Data Sources Window
- Data Sources Window, controls
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 607c324e11591211593522957dcd08747d230279
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219834"
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>Basit veri bağlamayı destekleyen bir Windows Forms kullanıcı denetimi oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Windows uygulamalarında formların üzerindeki verileri görüntülerken, mevcut denetimleri seçebilirsiniz **araç kutusu**, veya standart denetimlerinde kullanılamıyor işlevi uygulamanızı gerektiriyorsa, özel denetimler yazabilirsiniz. Bu izlenecek yol, uygulayan bir denetim oluşturma işlemi gösterilmektedir <xref:System.ComponentModel.DefaultBindingPropertyAttribute>. Denetimleri uygulayan <xref:System.ComponentModel.DefaultBindingPropertyAttribute> verilere bağlı bir özellik içerebilir. Bu tür denetimler benzer bir <xref:System.Windows.Forms.TextBox> veya <xref:System.Windows.Forms.CheckBox>.  
  
 Denetim yazma ile ilgili daha fazla bilgi için bkz: [tasarım zamanında Windows Forms denetimleri geliştirme](http://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).  
  
 Veri bağlama senaryoları denetimler yazarken, aşağıdaki veri bağlama özniteliklerden birini uygulamanız gerekir:  
  
|Veri bağlama öznitelik kullanımı|  
|-----------------------------------|  
|Uygulama <xref:System.ComponentModel.DefaultBindingPropertyAttribute> basit denetimlerinde gibi bir <xref:System.Windows.Forms.TextBox>, tek bir sütun (veya özellik) veri görüntüler. (Bu işlem, bu izlenecek yol sayfasında açıklanmıştır.)|  
|Uygulama <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> denetimler üzerinde gibi bir <xref:System.Windows.Forms.DataGridView>, veri listeleri'ı (veya tablo) görüntüler. Daha fazla bilgi için [karmaşık veri bağlamayı destekleyen bir Windows Forms kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|  
|Uygulama <xref:System.ComponentModel.LookupBindingPropertiesAttribute> denetimler üzerinde gibi bir <xref:System.Windows.Forms.ComboBox>, görünen veri listeleri (veya tablo) ancak tek bir sütun veya özelliği sunmak de gerekir. Daha fazla bilgi için [arama verileri bağlamayı destekleyen bir Windows Forms kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|  
  
 Bu izlenecek yol, bir tablodaki tek bir sütun verileri görüntüleyen basit bir denetim oluşturur. Bu örnekte `Phone` sütununun `Customers` Northwind örnek veritabanından tablo. Basit kullanıcı denetimini kullanarak müşterilerin telefon numaralarını standart bir telefon numarası biçiminde görüntüler bir <xref:System.Windows.Forms.MaskedTextBox> ve maskeyi ayarlamak için bir telefon numarası.  
  
 Bu kılavuz boyunca, öğreneceksiniz nasıl yapılır:  
  
-   Yeni bir **Windows uygulama**.  
  
-   Yeni bir **kullanıcı denetimi** projenize.  
  
-   Görsel olarak kullanıcı denetiminin tasarım.  
  
-   Uygulama `DefaultBindingProperty` özniteliği.  
  
-   Bir veri kümesi oluşturmak **veri kaynağı yapılandırması** Sihirbazı.  
  
-   Ayarlama **telefon** sütununda **veri kaynakları** yeni denetimi kullanmak için pencere.  
  
-   Verileri yeni denetimde görüntülemek için bir form oluşturun.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için şunlar gerekir:  
  
-   Northwind örnek veritabanına erişim. Daha fazla bilgi için [nasıl yapılır: örnek veritabanları yükleme](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="create-a-windows-application"></a>Bir Windows uygulaması oluşturma  
 İlk adım oluşturmaktır bir **Windows uygulama**.  
  
#### <a name="to-create-the-new-windows-project"></a>Yeni Windows projesi oluşturmak için  
  
1.  Visual Studio'da gelen **dosya** menüsünden Yeni bir **proje**.  
  
2.  Projeyi adlandırın **SimpleControlWalkthrough**.  
  
3.  Seçin **Windows uygulama** tıklatıp **Tamam**. Daha fazla bilgi için [istemci uygulamaları](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     **SimpleControlWalkthrough** projesi oluşturulur ve eklenen **Çözüm Gezgini**.  
  
## <a name="add-a-user-control-to-the-project"></a>Projeye kullanıcı denetimi Ekle  
 Bu izlenecek yol basit bir veri bağlanabilir denetiminden oluşturur bir **kullanıcı denetimi**, bu nedenle ekleyin bir **kullanıcı denetimi** öğesinin **SimpleControlWalkthrough** proje.  
  
#### <a name="to-add-a-user-control-to-the-project"></a>Projeye kullanıcı denetimi eklemek için  
  
1.  Gelen **proje** menüsünde seçin **kullanıcı denetimi Ekle**.  
  
2.  Tür `PhoneNumberBox` ad alanı seçeneğine tıklayıp **Ekle**.  
  
     **PhoneNumberBox** denetim eklenir **Çözüm Gezgini**ve tasarımcıda açılır.  
  
## <a name="design-the-phonenumberbox-control"></a>Tasarım PhoneNumberBox denetimi  
 Bu izlenecek yolda mevcut bağlı genişletir <xref:System.Windows.Forms.MaskedTextBox> oluşturmak için `PhoneNumberBox` denetimi.  
  
#### <a name="to-design-the-phonenumberbox-control"></a>Tasarım PhoneNumberBox denetimi  
  
1.  Sürükleme bir <xref:System.Windows.Forms.MaskedTextBox> gelen **araç kutusu** kullanıcı denetiminin tasarım yüzeyine.  
  
2.  Akıllı etiket seçin <xref:System.Windows.Forms.MaskedTextBox> yalnızca sürüklenebilen ve seçin **maskesini ayarlama**.  
  
3.  Seçin **telefon numarası** içinde **giriş maskesi** iletişim kutusu seçeneğine tıklayıp **Tamam** maskeyi ayarlamak için.  
  
## <a name="add-the-required-data-binding-attribute"></a>Gerekli veri bağlama öznitelik Ekle  
 Basit, destek veri bağlama denetimleri için uygulama <xref:System.ComponentModel.DefaultBindingPropertyAttribute>.  
  
#### <a name="to-implement-the-defaultbindingproperty-attribute"></a>DefaultBindingProperty öznitelik uygulamak için  
  
1.  Anahtar `PhoneNumberBox` kod görünümü denetimi. (Üzerinde **görünümü** menüsünde seçin **kod**.)  
  
2.  Değiştirin `PhoneNumberBox` aşağıdaki:  
  
     [!code-csharp[VbRaddataDisplaying#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/PhoneNumberBox.cs#3)]
     [!code-vb[VbRaddataDisplaying#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/PhoneNumberBox.vb#3)]  
  
3.  Gelen **derleme** menüsünde seçin **Çözümü Derle**.  
  
## <a name="create-a-data-source-from-your-database"></a>Veritabanından bir veri kaynağı oluşturun  
 Bu adımı kullanan **veri kaynağı yapılandırması** bir veri kaynağı oluşturmak için Sihirbazı'nı temel alan `Customers` Northwind örnek veritabanındaki tablo. Bağlantı oluşturmak için Northwind örnek veritabanına erişiminiz olmalıdır. Northwind örnek veritabanını ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: örnek veritabanları yükleme](../data-tools/how-to-install-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>Veri kaynağı oluşturmak için  
  
1.  Üzerinde **veri** menüsünü tıklatın **veri kaynaklarını Göster**.  
  
2.  İçinde **veri kaynakları** penceresinde **yeni veri kaynağı Ekle** başlatmak için **veri kaynağı yapılandırması** Sihirbazı.  
  
3.  Üzerinde **bir veri kaynağı türü seçin** sayfasında **veritabanı**ve ardından **sonraki**.  
  
4.  Üzerinde **veri bağlantınızı seçin** sayfasında, aşağıdakilerden birini yapın:  
  
    -   Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.  
  
    -   Seçin **yeni bağlantı** başlatmak için **Bağlantı Ekle/Değiştir** iletişim kutusu.  
  
5.  Veritabanınız parola gerektiriyorsa, hassas verileri eklemek ve ardından seçeneğini **sonraki**.  
  
6.  Üzerinde **bağlantı dizesini uygulama yapılandırma dosyasına Kaydet** sayfasında **sonraki**.  
  
7.  Üzerinde **veritabanı nesnelerinizi seçin** sayfasında **tabloları** düğümü.  
  
8.  Seçin `Customers` tablosunu ve ardından **son**.  
  
     **NorthwindDataSet** projenize eklenir ve `Customers` tablo görünür **veri kaynakları** penceresi.  
  
## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>Telefon sütunu PhoneNumberBox denetimi kullanmak için ayarlayın  
 İçinde **veri kaynakları** penceresindeki öğeleri formunuza sürükleyerek önce oluşturulacak denetimi ayarlayabilirsiniz.  
  
#### <a name="to-set-the-phone-column-to-bind-to-the-phonenumberbox-control"></a>PhoneNumberBox denetimine bağlamak için telefon sütununu ayarlamak için  
  
1.  Açık **Form1** Tasarımcısı'nda.  
  
2.  Genişletin **müşteriler** düğümünde **veri kaynakları** penceresi.  
  
3.  Aşağı açılan oka tıklayın **müşteriler** düğümünü seçip **ayrıntıları** denetim listesinden.  
  
4.  Aşağı açılan oka tıklayın **telefon** sütunu seçip **Özelleştir**.  
  
5.  Seçin **PhoneNumberBox** listesinden **ilişkili denetimler** içinde **veri kullanıcı Arabirimi özelleştirme seçenekleri** iletişim kutusu.  
  
6.  Aşağı açılan oka tıklayın **telefon** sütunu seçip **PhoneNumberBox**.  
  
## <a name="addcontrols-to-the-form"></a>Forma Addcontrols  
 Öğe sürükleyerek veriye bağlı denetimler oluşturabilirsiniz **veri kaynakları** forma penceresi.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Form üzerinde veri bağlama denetimleri oluşturmak için  
  
-   Ana sürükleyin **müşteriler** düğümünden **veri kaynakları** form penceresinden doğrulayın `PhoneNumberBox` denetim verileri görüntülemek için kullanılan `Phone` sütun.  
  
     Araç şeridi yanı sıra form üzerindeki verilere bağlı denetimler, tanımlayıcı etiketlerle görünür (<xref:System.Windows.Forms.BindingNavigator>) Kayıtlarda gezinmek için. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, ve <xref:System.Windows.Forms.BindingNavigator> bileşen tepsisinde görünür.  
  
## <a name="run-the-application"></a>Uygulamayı çalıştırın  
  
#### <a name="to-run-the-application"></a>Uygulamayı çalıştırmak için  
  
-   Uygulamayı çalıştırmak için F5 tuşuna basın.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Uygulama gereksinimlerinize bağlı olarak, veri bağlamayı destekleyen bir denetim oluşturma sonra gerçekleştirmek isteyebileceğiniz birkaç adım vardır. Tipik bir sonraki adımlardan birkaçı şunlardır:  
  
-   Diğer uygulamalarda yeniden kullanabilir, böylece bir denetim kitaplığı içinde özel kontrollerinizi yapılıyor.  
  
-   Daha karmaşık veri bağlama senaryoları desteklemek denetimler oluşturma. Daha fazla bilgi için [karmaşık veri bağlamayı destekleyen bir Windows Forms kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) ve [arama verileri bağlamayı destekleyen bir Windows Forms kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Deneti veri kaynakları penceresinden sürüklendiğinde oluşturulacak şekilde ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)

