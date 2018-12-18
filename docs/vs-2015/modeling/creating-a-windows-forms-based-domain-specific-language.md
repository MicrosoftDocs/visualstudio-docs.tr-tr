---
title: Bir Windows Forms tabanlı etki alanına özgü dil oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 452318ff-8ecf-46d0-8ca0-4013d0cdafaf
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: a79ffda3a044424cc863472c32d62228e90cc6fd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942029"
---
# <a name="creating-a-windows-forms-based-domain-specific-language"></a>Windows Forms Tabanlı Etki Alanına Özgü Dil Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir DSL diyagramı kullanmak yerine bir etki alanına özgü dil (DSL) model durumunu görüntülemek için Windows Forms kullanabilirsiniz. Bu konuda size kılavuzluk kullanarak, bir Windows Form için bir DSL bağlama [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Görselleştirme ve modelleme SDK'si.  

 ![DSL&#45;Wpf&#45;2](../modeling/media/dsl-wpf-2.png "DSL-Wpf-2")  
Bir Windows formu kullanıcı Arabirimi ve model gezginini gösteren bir DSL örneği.  

## <a name="creating-a-windows-forms-dsl"></a>Bir DSL Windows formları oluşturma  
 **Minimal WinForm Tasarımcısı** DSL şablon kendi gereksinimlerinize uyacak şekilde değiştirebilirsiniz en az bir DSL oluşturur.  

#### <a name="to-create-a-minimal-winforms-dsl"></a>En az bir WinForms DSL oluşturmak için  

1. Bir DSL gelen oluşturma **Minimal WinForm Tasarımcısı** şablonu.  

    Bu kılavuzda, aşağıdaki adlarını kabul edilir:  


   |                       |                 |
   |-----------------------|-----------------|
   | Çözüm ve DSL adı |     FarmApp     |
   |       Ad Alanı       | Company.FarmApp |


2. Şablon sağlar ilk örnek ile denemeler yapın:  

   1.  Tüm Şablonları Dönüştür.  

   2.  Derleme ve çalıştırma örneği (**CTRL + F5**).  

   3.  Visual Studio'nun deneysel örneğinde açın `Sample` hata ayıklama proje dosyasında.  

        Bir Windows Forms denetiminde görüntülendiğini dikkat edin.  

        Gezgini'nde gösterilen model öğelerini de görebilirsiniz.  

        Form veya Gezgini bazı öğeleri ekleyin ve diğer görüntüsünü görüntülendiğine dikkat edin.  

   Ana örneğinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], DSL çözüm hakkında aşağıdaki noktalara dikkat edin:  

-   `DslDefinition.dsl` hiçbir diyagram öğeleri içerir. Bu DSL örneği modelleri görüntülemek için DSL diyagramları kullanmaz olmasıdır. Bunun yerine, bir Windows Form modeline bağlar ve formu üzerindeki öğelerin model görüntülenir.  

-   Ek olarak `Dsl` ve `DslPackage` projeleri, çözümü içeren adlı üçüncü bir proje `UI.` **UI** projesini içeren bir Windows Forms denetiminin tanımı. `DslPackage` bağımlı `UI`, ve `UI` bağlıdır `Dsl`.  

-   İçinde `DslPackage` projesi `UI\DocView.cs` tanımlanan Windows Forms Denetim kod bulunur `UI` proje.  

-   `UI` Projesini içeren bir çalışma örneği DSL için bağlı bir form denetimi. Ancak, DSL tanımını değiştiğinde, çalışmaz. `UI` Proje içerir:  

    -   Adlı bir Windows Forms sınıf `ModelViewControl`.  

    -   Adlı bir dosya `DataBinding.cs` ek kısmi bir tanımını içeren `ModelViewControl`. İçeriği görmek için **Çözüm Gezgini**dosyası için kısayol menüsünü açın ve seçin **kodu görüntüle**.  

### <a name="about-the-ui-project"></a>UI projesi hakkında  
 DSL tanım dosyası kendi DSL tanımlamak için güncelleştirdiğinizde, bağlantı denetimi güncellemek zorunda kalırsınız `UI` DSL'nizi görüntülemek için proje. Farklı `Dsl` ve `DslPackage` projeleri, örnek `UI` gelen proje oluşturulmuyor `DslDefinitionl.dsl`. İsterseniz, bu izlenecek yolda kapsamında olmayan ancak kodunu oluşturmak için .tt dosyaları ekleyebilirsiniz.  

## <a name="updating-the-dsl-definition"></a>DSL tanım güncelleştirme  
 DSL tanımını, bu kılavuzda kullanılan şunlardır:  

 ![DSL&#45;Wpf&#45;1](../modeling/media/dsl-wpf-1.png "DSL-Wpf-1")  

#### <a name="to-update-the-dsl-definition"></a>DSL tanımını güncelleştirmek için  

1.  DslDefinition.dsl DSL Tasarımcısı'nda açın.  

2.  Silme **ExampleElement**  

3.  Yeniden adlandırma **ExampleModel** etki alanı sınıfı `Farm`.  

     Adlı ek bir etki alanı özellikleri vermek `Size` türü **Int32**, ve `IsOrganic` türü **Boole**.  

    > [!NOTE]
    >  Kök etki alanı sınıfını silmek ve ardından yeni bir kök oluşturun, düzenleyici kök sınıfı özelliği döndürme gerekecektir. İçinde **DSL Gezgini**seçin **Düzenleyicisi**. Özellikler penceresinde ayarlayın **kök sınıfı** için `Farm`.  

4.  Kullanım **adlı etki alanı sınıfı** aşağıdaki alan sınıfları oluşturmak için aracı:  

    -   `Field` – Bu adlı bir ek etki alanı özelliği size `Size`.  

    -   `Animal` – Özellikler penceresinde ayarlayın **devralma değiştiricisi** için **soyut**.  

5.  Kullanım **etki alanı sınıfı** aşağıdaki sınıflar oluşturmak için aracı:  

    -   `Sheep`  

    -   `Goat`  

6.  Kullanım **devralma** aracının `Goat` ve `Sheep` devralınacak `Animal`.  

7.  Kullanım **katıştırma** eklemek için araç `Field` ve `Animal` altında `Farm`.  

8.  Diyagram düzenli hale getirmek isteyebilirsiniz. Yinelenen öğe sayısını azaltmak için kullanma **alt ağacı buraya getirin** yaprak öğelerin kısayol menüsündeki komutu.  

9. **Tüm Şablonları dönüştürme** Çözüm Gezgini araç çubuğundaki.  

10. Derleme **Dsl** proje.  

    > [!NOTE]
    >  Bu aşamada, diğer projeleri hatasız derleme değil. Ancak, böylece kendi derlemesi için veri kaynağı Sihirbazı kullanılabilir Dsl projesi oluşturmak istiyoruz.  

## <a name="updating-the-ui-project"></a>UI projesi güncelleştiriliyor  
 Şimdi, DSL modelde tutulan haliyle bilgileri görüntüleyen yeni bir kullanıcı denetimi oluşturabilirsiniz. Veri bağlamaları ile kullanıcı denetimi modele bağlanmak için en kolay yoludur. Veri bağdaştırıcısı türü adlı bağlama **ModelingBindingSource** VMSDK olmayan arabirimleri DSL'ler bağlanmak için özel olarak tasarlanmıştır.  

#### <a name="to-define-your-dsl-model-as-a-data-source"></a>DSL model veri kaynağı olarak tanımlamak için  

1.  Üzerinde **veri** menüsünde seçin **veri kaynaklarını Göster**.  

     **Veri kaynakları** penceresi açılır.  

     Seçin **yeni veri kaynağı Ekle**. **Veri kaynağı Yapılandırma Sihirbazı** açılır.  

2.  Seçin **nesne**, **sonraki**.  

     Genişletin **Dsl**, **Company.FarmApp**seçip **grubu**, modelinizin kök sınıf. Seçin **son**.  

     Çözüm Gezgini'nde **UI** proje artık içeren **Properties\DataSources\Farm.datasource**  

     Özellikler ve ilişkiler model sınıfınızın veri kaynakları penceresinde görünür.  

     ![DslWpf&#45;3](../modeling/media/dslwpf-3.png "DslWpf-3")  

#### <a name="to-connect-your-model-to-a-form"></a>Bir forma modelinizi bağlanmak için  

1. İçinde **UI** projesinde, tüm mevcut .cs dosyaları silin.  

2. Yeni bir **kullanıcı denetimi** adlı dosya `FarmControl` için **UI** proje.  

3. İçinde **veri kaynakları** penceresinde aşağı açılan menüden **grubu**, seçin **ayrıntıları**.  

    Diğer özellikler için varsayılan ayarları bırakın.  

4. FarmControl.cs Tasarım Görünümü'nde açın.  

    Sürükleme **grubu** FarmControl veri kaynakları penceresinden.  

    Bir dizi denetimi görünür, her bir özellik için bir tane. İlişki özellikleri denetimleri oluşturmaz.  

5. Silme **farmBindingNavigator**. Bu da otomatik olarak oluşturulur `FarmControl` Tasarımcısı, ancak bu uygulama için yararlı değildir.  

6. Araç kutusunu kullanma iki örneğini oluşturma **DataGridView**ve bunları `AnimalGridView` ve `FieldGridView`.  

   > [!NOTE]
   >  Alternatif bir adım veri kaynakları penceresinden denetimin üzerine hayvanlar ve alanları öğeleri sürüklemektir. Bu eylem, veri kılavuzları ve bağlamaları kılavuz görünümünü ve veri kaynağı arasında otomatik olarak oluşturur. Ancak, bu bağlama için DSL'ler düzgün çalışmaz. Bu nedenle daha iyi veri kılavuzları ve bağlamaları oluşturmak el ile.  

7. Araç kutusu içermiyorsa **ModelingBindingSource** aracı, ekleyin. Kısayol menüsünde **veri** sekmesini, **öğelerini Seç**. İçinde **araç kutusu öğelerini Seç** iletişim kutusunda **ModelingBindingSource** gelen **.NET Framework sekmesinde**.  

8. Araç kutusunu kullanma iki örneğini oluşturma **ModelingBindingSource**ve bunları `AnimalBinding` ve `FieldBinding`.  

9. Ayarlama **DataSource** her özellik **ModelingBindingSource** için **farmBindingSource**.  

     Ayarlama **DataMember** özelliğini **hayvanlar** veya **alanları**.  

10. Ayarlama **DataSource** özelliklerini `AnimalGridView` için `AnimalBinding`ve `FieldGridView` için `FieldBinding`.  

11. Denemek için Grup denetimin düzenini ayarlayın.  

    **ModelingBindingSource** DSL'ler için özgü çeşitli işlevler gerçekleştiren bir bağdaştırıcı:  

- Bu, VMSDK Store işlem güncelleştirmeleri sarmalar.  

   Örneğin, kullanıcı bir satır veri görünümü kılavuzdan sildiğinde, normal bir bağlama bir işlem özel durum neden olur.  

- Kullanıcı bir satır seçtiğinde, Özellikler penceresinde veri kılavuzu satırı yerine karşılık gelen model öğesinin özelliklerini görüntüler, sağlar.  

  ![DslWpf4](../modeling/media/dslwpf4.png "DslWpf4")  
  Veri kaynakları ve görünümleri arasında bağlantılar şeması.  

#### <a name="to-complete-the-bindings-to-the-dsl"></a>DSL bağlamaları tamamlamak için  

1.  Ayrı bir kod dosyasında aşağıdaki kodu ekleyin **UI** proje:  

    ```csharp  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Modeling;  
    using Microsoft.VisualStudio.Modeling.Design;  

    namespace Company.FarmApp  
    {  
      partial class FarmControl  
      {  
        public IContainer Components { get { return components; } }  

        /// <summary>Binds the WinForms data source to the DSL model.  
        /// </summary>  
        /// <param name="nodelRoot">The root element of the model.</param>  
        public void DataBind(ModelElement modelRoot)  
        {  
          WinFormsDataBindingHelper.PreInitializeDataSources(this);  
          this.farmBindingSource.DataSource = modelRoot;  
          WinFormsDataBindingHelper.InitializeDataSources(this);  
        }  
      }  
    }  
    ```  

2.  İçinde **DslPackage** proje, düzenleme **DslPackage\DocView.tt** aşağıdaki değişken tanımını güncelleştirmek için:  

    ```csharp  
    string viewControlTypeName = "FarmControl";  
    ```  

## <a name="testing-the-dsl"></a>DSL test etme  
 DSL çözümü şimdi oluşturun ve geliştirmeleri daha sonra daha eklemek isteyebilirsiniz ancak çalıştırın.  

#### <a name="to-test-the-dsl"></a>DSL test etmek için  

1.  Derleme ve çözümü çalıştırın.  

2.  Visual Studio'nun deneysel örneğinde açın **örnek** dosya.  

3.  İçinde **FarmApp Gezgini**, kısayol menüsünü açın **grubu** seçin ve kök düğümü **yeni geçmiş ekleme**.  

     `Goat1` görünür **hayvanlar** görünümü.  

    > [!WARNING]
    >  Kısayol menüsünü kullanmanız gerekir **grubu** düğümünü değil **hayvanlar** düğümü.  

4.  Seçin **grubu** kök düğümü ve özelliklerini görüntüleyin.  

     Form görünümünde değiştirme **adı** veya **boyutu** grubunun.  

     Ne zaman formunda, Özellikler penceresinde karşılık gelen özellik değişiklikleri her alanı uzağa gidin.  

## <a name="enhancing-the-dsl"></a>DSL geliştirme  

#### <a name="to-make-the-properties-update-immediately"></a>Hemen güncelleştirme özellikleri yapma  

1.  FarmControl.cs Tasarım görünümünde, ad, boyut veya IsOrganic gibi basit bir alan seçin.  

2.  Özellikler penceresinde genişletin **DataBindings** açın **(Gelişmiş)**.  

     İçinde **biçimlendirme ve Gelişmiş bağlama** iletişim altında **veri kaynağı güncelleştirme modu**, seçin **OnPropertyChanged**.  

3.  Derleme ve çözümü çalıştırın.  

     Alan grubu modeli değişikliklerini hemen karşılık gelen özelliği içeriğini değiştirdiğinizde doğrulayın.  

#### <a name="to-provide-add-buttons"></a>Ekle düğmesini sağlamak için  

1. FarmControl.cs Tasarım görünümünde, araç kutusu, formdaki bir düğme oluşturmak için kullanın.  

    Düğme metni ve adını örneğin için düzenleyin `New Sheep`.  

2. Düğmenin arka plan kod (örneğin, çift tıklayarak) açın.  

    Şu şekilde düzenleyin:  

   ```csharp  
   private void NewSheepButton_Click(object sender, EventArgs e)  
   {  
     using (Transaction t = farm.Store.TransactionManager.BeginTransaction("Add sheep"))  
     {  
       elementOperations.MergeElementGroup(farm,  
         new ElementGroup(new Sheep(farm.Partition)));  
       t.Commit();  
     }  
   }  

   // The following code is shared with other add buttons:  
   private ElementOperations operationsCache = null;  
   private ElementOperations elementOperations  
   {  
     get  
     {  
       if (operationsCache == null)  
       {  
         operationsCache = new ElementOperations(farm.Store, farm.Partition);  
       }  
       return operationsCache;  
     }  
   }  
   private Farm farm  
   {  
     get { return this.farmBindingSource.DataSource as Farm; }  
   }  

   ```  

    Aşağıdaki Direktif Ekle gerekecektir:  

   ```csharp  

   using Microsoft.VisualStudio.Modeling;  

   ```  

3. Goats ve alanları için benzer bir düğme ekleyin.  

4. Derleme ve çözümü çalıştırın.  

5. Yeni düğmesini bir öğe ekler doğrulayın. Yeni öğe FarmApp Gezgini'nde ve uygun veri ızgara görünümünde görüntülenmesi gerekir.  

    Veri Kılavuzu görünümü öğe adını düzenlemeniz mümkün olması gerekir. Ayrıca oradan silebilirsiniz.  

   ![DSL&#45;Wpf&#45;2](../modeling/media/dsl-wpf-2.png "DSL-Wpf-2")  

### <a name="about-the-code-to-add-an-element"></a>Bir öğe eklemek için kod hakkında  
 Yeni öğe düğmeler için aşağıdaki diğer kod biraz daha basittir.  

```csharp  
private void NewSheepButton_Click(object sender, EventArgs e)  
{  
  using (Transaction t = farm.Store.TransactionManager.BeginTransaction("Add sheep"))  
  {  
    farm.Animals.Add(new Sheep(farm.Partition)); ;  
    t.Commit();  
  }  
}  

```  

 Ancak, bu kod yeni öğe için bir varsayılan ad ayarlı değil. İçinde tanımlı herhangi bir özelleştirilmiş birleştirme çalıştırmaz **öğe birleştirme yönergeleri** DSL, ve tanımlanmış herhangi bir özel birleştirme kodu çalışmaz.  

 Bu nedenle kullanmanızı öneririz <xref:Microsoft.VisualStudio.Modeling.ElementOperations> yeni öğeleri oluşturmak için. Daha fazla bilgi için [özelleştirme öğe oluşturma ve hareketini](../modeling/customizing-element-creation-and-movement.md).  

## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir etki alanına özgü dil tanımlama](../modeling/how-to-define-a-domain-specific-language.md)   
 [Bir etki alanına özgü dili özelleştirmek için kod yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [Visual Studio için Modelleme SDK'sı - Etki Alanına Özgü Diller](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)



