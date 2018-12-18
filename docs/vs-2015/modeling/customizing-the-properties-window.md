---
title: Özellikler penceresini özelleştirme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, Properties window
ms.assetid: b6658de5-4e85-4628-93b2-5cc12f63d25b
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: ab8f1e85bec4c8a12a122030d2b9487a13e826a6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49845751"
---
# <a name="customizing-the-properties-window"></a>Özellikler Penceresini Özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İçinde etki alanına özgü dil (DSL) görünümünü ve davranışını özellikler penceresinin özelleştirebilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. DSL tanımındaki her etki alanı sınıfı üzerinde etki alanı özelliklerini tanımlayın. Diyagram üzerinde veya Model Gezgini'nde sınıfının bir örneğini seçtiğinizde varsayılan olarak, her etki alanı özelliği Özellikler penceresinde listelenir. Bunları diyagramdaki şekil alanları eşlenmedi olsa bile bu görmek ve etki alanı özelliklerinin değerlerini düzenlemek, sağlar.  
  
## <a name="names-descriptions-and-categories"></a>Adları ve açıklamaları kategorileri  
 **Adı ve görünen adı**. Bir alan özelliği tanımında, özellik görünen adı Özellikler penceresinde çalışma zamanında görüntülenen adıdır. Özellik Güncelleştirme için program kodu yazarken aksine, adı kullanılır. Adın doğru bir CLR alfasayısal adı olması gerekir, ancak görünen adı boşluk içeremez.  
  
 DSL tanımındaki bir özelliğin adını ayarladığınızda, onun görünür ismini adının bir kopyasını otomatik olarak ayarlanır. "FuelGauge" gibi bir Pascal cased adını yazarsanız, görünen adı otomatik olarak bir boşluk içeriyor: "Yakıt ölçer". Ancak, görünen ad başka bir değere açıkça ayarlayabilirsiniz.  
  
 **Açıklama**. Bir etki alanı özelliğin açıklamasını iki yerde görüntülenir:  
  
- Kullanıcı özelliği seçtiğinde Özellikler penceresinin alt. Kullanıcıya ne özelliği temsil eden açıklamak için kullanabilirsiniz.  
  
- Oluşturulan program kodu içinde. API belgeleri ayıklamak için belge özelliklerini kullanıyorsanız, bu özelliğin API açıklamasını olarak görünür.  
  
  **Kategori**. Özellikler penceresinde başlık kategorisidir.  
  
## <a name="exposing-style-features"></a>Stil özelliklerini gösterme  
 Grafik öğelerin dinamik özelliklerin bazıları temsil edilebilir veya *kullanıma sunulan* olarak etki alanı özellikleri. Bu şekilde sunulan bir özellik kullanıcı tarafından güncelleştirilebilir ve daha fazlasını kolayca program kodu tarafından güncelleştirilebilir.  
  
 Bir DSL tanımındaki şekil sınıf sağ tıklatın, **ekleme kullanıma sunulan**, bir özellik seçin.  
  
 Diyagramdaki şekilleri kullanıma sunabileceğiniz **FillColor**, **OutlineColor**, **TextColor**, **OutlineDashStyle**,  **OutlineThickness** ve **FillGradientMode** özellikleri. Bağlayıcılarda kullanıma sunabileceğiniz **renk**`,`**TextColor**, **DashStyle**, ve **kalınlığı** özellikleri. Diyagramlar üzerinde kullanıma sunabileceğiniz **FillColor** ve **TextColor** özellikleri.  
  
## <a name="forwarding-displaying-properties-of-related-elements"></a>İletme: İlgili öğelerin özelliklerini görüntüleme  
 Kullanıcı, DSL'nin bir model bir öğe seçtiğinde, o öğenin özellikleri Özellikler penceresinde görüntülenir. Ancak, belirtilen ilgili öğelerin özelliklerini görüntüleyebilirsiniz. Birlikte çalışan bir grup öğelerin tanımladıysanız, bu yararlıdır. Örneğin, bir ana öğesi ve isteğe bağlı bir eklenti öğesi tanımlayabilir. Main öğesi bir şekle eşlenir ve diğer değil, bir öğede değilmiş gibi tüm özelliklerini görmek kullanışlıdır.  
  
 Bu etkiyi adlı *özelliği iletme*, ve bazı durumlarda otomatik olarak gerçekleşir. Diğer durumlarda, bir etki alanı tür tanımlayıcısı tanımlayarak iletme özellik elde edebilirsiniz.  
  
### <a name="default-property-forwarding-cases"></a>Varsayılan özellik iletme durumlar  
 Kullanıcı Gezgini'nde bir şekil veya Bağlayıcısı veya bir öğe seçtiğinde, aşağıdaki özellikleri Özellikler penceresinde görüntülenir:  
  
-   Etki alanı sınıfı, temel sınıflarında tanımlanan de dahil olmak üzere model öğesi üzerinde tanımlanan etki alanı özellikleri. Etki alanı özellikleri, ayarladığınız bir istisnası **olan gözatılabilir** için `False`.  
  
-   0..1 çokluğu olan ilişkileri bağlı öğelerin adları. İlişki için bir bağlayıcı eşlemesi tanımlanmamış olsa bile bu isteğe bağlı olarak görmek için kullanışlı bir yöntem öğeleri, bağlı sağlar.  
  
-   Öğesini hedefleyen bir gömme ilişkisi etki alanı özellikleri. Gömme ilişkiler genellikle açıkça gösterilmez olduğundan, bu kullanıcının özelliklerine bakın olanak tanır.  
  
-   Seçilen şekil veya bağlayıcının üzerinde tanımlanan etki alanı özellikleri.  
  
### <a name="adding-property-forwarding"></a>İletme özelliği ekleme  
 Bir özellik iletmek için bir etki alanı tür tanımlayıcısı tanımlayın. İki alan sınıfı arasındaki bir etki alanı ilişkisi varsa, ikinci etki alanı sınıfı, bir etki alanı özelliğinin değeri ilk sınıf bir etki alanı özelliği ayarlamak için bir etki alanı tür tanımlayıcısı'nı kullanabilirsiniz. Arasında bir ilişki varsa, örneğin, bir **kitap** etki alanı sınıfı ve bir **Yazar** etki alanı sınıfı, bir etki alanı tür tanımlayıcısı yapmak için kullanabileceğiniz **adı** özelliği bir Kitaptaki **Yazar** kullanıcının kitaptan seçtiğinde, Özellikler penceresinde görünür.  
  
> [!NOTE]
>  Kullanıcı bir model düzenlerken iletme özelliği yalnızca Özellikler penceresini etkiler. Alıcı sınıfta bir alan özelliği tanımlamıyor. İletilen domain özelliği DSL tanımının diğer bölümlerinde veya program kodunda erişmek istiyorsanız, iletme öğesi erişmeniz gerekir.  
  
 Aşağıdaki yordam, DSL oluşturmuş olduğunuzu varsayar. İlk birkaç adım önkoşulları özetler.  
  
##### <a name="to-forward-a-property-from-another-element"></a>Başka bir öğeden bir özellik iletmek için  
  
1.  Oluşturma bir [!INCLUDE[dsl](../includes/dsl-md.md)] olarak adlandırılır, bu örnekte, en az iki sınıf içeren çözüm **kitap** ve **Yazar**. İki tür arasında bir ilişki olmalıdır **kitap** ve **Yazar**.  
  
     Kaynak rolünün çokluğu (rolün **kitap** tarafı) 0.. 1 veya 1..1, olmalıdır böylece her **kitap** varsa **Yazar**.  
  
2.  İçinde **DSL Gezgini**, sağ **kitap** etki alanı sınıfı ve ardından **ekleme yeni DomainTypeDescriptor**.  
  
     Adlı bir düğüm **özel özellik tanımlayıcılarının yolları** altında görünür **özel tür tanımlayıcısının** düğümü.  
  
3.  Sağ **özel tür tanımlayıcısının** düğümünü ve ardından **ekleme yeni PropertyPath**.  
  
     Yeni bir özellik yolu altında görünür **özel özellik tanımlayıcılarının yolları** düğümü.  
  
4.  Yeni özellik yolu seçin ve **özellikleri** penceresinde **özelliğinin yolu** uygun model öğesi yolu.  
  
     Bu özellik sağındaki aşağı oka tıklayarak ağaç görünümünde yolu düzenleyebilirsiniz. Etki alanı yolları hakkında daha fazla bilgi için bkz. [etki alanı yolu sözdizimi](../modeling/domain-path-syntax.md). Düzenlediğinizde, yolun benzemelidir **BookReferencesAuthor.Author/! Yazar**.  
  
5.  Ayarlama **özelliği** için **adı** etki alanı özelliğine **Yazar**.  
  
6.  Ayarlama **görünen adı** için **yazar adı**.  
  
7.  Tüm Şablonları dönüştürme, oluşturma ve DSL çalıştırın.  
  
8.  Bir modeli diyagramı yazar, kitap oluşturur ve başvuru ilişkisi kullanarak bunları bağlayabilirsiniz. Kitap öğesini seçin ve Özellikler penceresinde kitabı özelliklerine ek olarak yazar adını görmeniz gerekir. Bağlantılı yazarının adını değiştirin veya başka bir yazar kitap bağlayın ve kitap yazar adını değiştiğini gözlemleyin.  
  
## <a name="custom-property-editors"></a>Özel özellik düzenleyicileri  
 Özellik penceresi, düzenleme deneyimi her bir etki alanı özellik türü için uygun bir varsayılan sağlar. Örneğin, bir listeden seçimli türü için bir açılan liste kullanıcının gördüğü ve sayısal bir özellik için kullanıcı basamak girebilirsiniz. Bu yalnızca yerleşik türler için geçerlidir. Dış tür belirtirseniz, kullanıcının özellik değerleri görebilirsiniz, ancak düzenleme olmadan mümkün olacaktır.  
  
 Ancak, aşağıdaki düzenleyiciler ve türleri belirtebilirsiniz:  
  
1. Standart türüyle kullanılan başka bir düzenleyici. Örneğin, bir dize özelliği için bir dosya yolu Düzenleyicisi belirtebilirsiniz.  
  
2. Etki alanı özelliği ve bunun için bir düzenleyici için dış tür.  
  
3. Bir .NET Düzenleyicisi gibi dosya yolu Düzenleyicisi veya kendi özel özellik düzenleyici oluşturabilirsiniz.  
  
    Bir dış tür ve varsayılan Düzenleyicisi olan dize gibi bir tür arasında dönüştürme.  
  
   Bir DSL içinde bir *dış tür* basit türleri (örneğin, Boole veya Int32) veya dize biri değil herhangi bir tür.  
  
#### <a name="to-define-a-domain-property-that-has-an-external-type"></a>Bir dış türe sahip bir alan özelliği tanımlamak için  
  
1. İçinde **Çözüm Gezgini**, dış tür içeren derleme (DLL) bir başvuru ekleyin **Dsl** proje.  
  
    Derleme, bir .NET bütünleştirilmiş kodu ya da sizin tarafınızdan sağlanan derleme olabilir.  
  
2. Türüne eklemek **etki alanı türleri** zaten yapmış sürece listesi.  
  
   1.  DslDefinition.dsl, açın ve **DSL Gezgini**kök düğümüne sağ tıklayın ve ardından **yeni dış türü Ekle**.  
  
        Altında yeni bir giriş belirir **etki alanı türleri** düğümü.  
  
       > [!WARNING]
       >  Menü öğesi DSL kök düğümde değil **etki alanı türleri** düğümü.  
  
   2.  Özellikler penceresinde, adı ve yeni türünün ad alanını ayarlayın.  
  
3. Bir alan özelliği için bir etki alanı sınıfı, her zamanki şekilde ekleyin.  
  
    Özellikler penceresinde, aşağı açılan listeden dış türünü seçin. **türü** alan.  
  
   Bu aşamada, kullanıcılar özelliğinin değerlerini görüntüleyebilir, ancak panoyu düzenleyemez. Görüntülenen değerleri elde edilir `ToString()` işlevi. Özelliğinin değeri, örneğin bir komut veya kuralın ayarlar program kodu yazabilirsiniz.  
  
### <a name="setting-a-property-editor"></a>Özellik Düzenleyicisi'ni ayarlama  
 Etki alanı özelliğine aşağıdaki biçimde bir CLR özniteliği ekleyin:  
  
```  
[System.ComponentModel.Editor (  
   typeof(AnEditor),  
   typeof(System.Drawing.Design.UITypeEditor))]  
  
```  
  
 Bir özellik özniteliğini kullanarak ayarlayabilirsiniz **özel özniteliği** Özellikler penceresindeki girişi.  
  
 Türünü `AnEditor` ikinci parametresinde belirtilen türünden türetilmesi gerekir. İkinci parametre olmalıdır <xref:System.Drawing.Design.UITypeEditor> veya <xref:System.ComponentModel.ComponentEditor>. Daha fazla bilgi için bkz. <xref:System.ComponentModel.EditorAttribute>.  
  
 Kendi düzenleyicinizi ya da bir düzenleyici sağlanan belirtebilirsiniz [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], gibi <xref:System.Windows.Forms.Design.FileNameEditor> veya <xref:System.Drawing.Design.ImageEditor>. Örneğin, kullanıcının bir dosya adı girebilirsiniz bir özelliği için aşağıdaki yordamı kullanın.  
  
##### <a name="to-define-a-file-name-domain-property"></a>Bir dosya adı etki alanı özelliği tanımlamak için  
  
1.  Bir etki alanı sınıfı, DSL tanımındaki alan özelliği ekleyin.  
  
2.  Yeni özellik seçin. İçinde **özel özniteliği** alanına Özellikler penceresinde, aşağıdaki öznitelik. Bu öznitelik girmek için üç noktaya tıklayın **[...]**  ve öznitelik adı ve parametreleri ayrı olarak girin:  
  
    ```  
    [System.ComponentModel.Editor (  
       typeof(System.Windows.Forms.Design.FileNameEditor)  
       , typeof(System.Drawing.Design.UITypeEditor))]  
  
    ```  
  
3.  Etki alanı özelliğinin türü, kendi varsayılan ayarını bırakın **dize**.  
  
4.  Düzenleyici test etmek için kullanıcılar, etki alanı özelliği düzenlemek için dosya adı Düzenleyicisi'ni açabilir doğrulayın.  
  
    1.  CTRL + F5 veya F5 tuşuna basın. Hata ayıklama çözümde test dosyasını açın. Etki alanı sınıfı, bir öğe oluşturun ve seçin.  
  
    2.  Özellikler penceresinde etki alanı özelliğini seçin. Üç nokta değerini alan gösterir **[...]** .  
  
    3.  Üç nokta simgesine tıklayın. Dosya iletişim kutusu görünür. Bir dosya seçin ve iletişim kutusunu kapatın. Dosya yolu, etki alanı özelliğinin değeri bir sunulmuştur.  
  
### <a name="defining-your-own-property-editor"></a>Kendi özellik Düzenleyici tanımlama  
 Kendi düzenleyicinizi tanımlayabilirsiniz. Kullanıcı, tanımladığınız bir türü düzenleyin veya standart bir türü özel bir şekilde düzenlemek için izin vermek için bunu. Örneğin, bir formül temsil eden bir dize girişi kullanıcıya izin verebilir.  
  
 Türetilen bir sınıf yazarak bir düzenleyici tanımladığınız <xref:System.Drawing.Design.UITypeEditor>. Sınıfınıza geçersiz kılmanız gerekir:  
  
- <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>, kullanıcı ile etkileşim kurmanızı ve özellik değerini güncelleştirin.  
  
- <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>, Düzenleyici bir iletişim kutusunu açın veya bir açılan menü sağlamak belirtmek için.  
  
  Grafik gösterimi özellik kılavuzunda görüntülenecek özelliğin değerini de sağlayabilirsiniz. Bunu yapmak için geçersiz kılma `GetPaintValueSupported`, ve `PaintValue`.  Daha fazla bilgi için bkz. <xref:System.Drawing.Design.UITypeEditor>.  
  
> [!NOTE]
>  Ayrı bir kod dosyasında kod ekleme **Dsl** proje.  
  
 Örneğin:  
  
```  
internal class TextFileNameEditor : System.Windows.Forms.Design.FileNameEditor  
{  
  protected override void InitializeDialog(System.Windows.Forms.OpenFileDialog openFileDialog)  
  {  
    base.InitializeDialog(openFileDialog);  
    openFileDialog.Filter = "Text files(*.txt)|*.txt|All files (*.*)|*.*";  
    openFileDialog.Title = "Select a text file";  
  }  
}  
  
```  
  
 Bu düzenleyici kullanmak için ayarlanmış **özel özniteliği** etki alanı özellik:  
  
```  
[System.ComponentModel.Editor (  
   typeof(MyNamespace.TextFileNameEditor)  
   , typeof(System.Drawing.Design.UITypeEditor))]  
  
```  
  
 Daha fazla bilgi için bkz. <xref:System.Drawing.Design.UITypeEditor>.  
  
## <a name="providing-a-drop-down-list-of-values"></a>Aşağı açılan listesini değerleri sağlama  
 Aralarından seçim yapabileceğiniz bir kullanıcı için değerler listesini sağlayabilirsiniz.  
  
> [!NOTE]
>  Bu teknik, çalışma zamanında değiştirebileceğiniz değerler listesini sağlar. Değişmeyen bir listesini sağlamak istiyorsanız, bunun yerine göz önünde bulundurun, etki alanı özellik türü olarak bir listeden seçimli türü kullanarak.  
  
 Standart değerlerin bir listesini tanımlamak için aşağıdaki biçimde bir CLR özniteliğinin, etki alanı özelliğine ekleyin:  
  
```  
[System.ComponentModel.TypeConverter   
(typeof(MyTypeConverter))]  
  
```  
  
 Türetilen bir sınıf tanımlama <xref:System.ComponentModel.TypeConverter>. Ayrı bir dosyaya kod eklemek **Dsl** proje. Örneğin:  
  
```csharp  
/// <summary>  
/// Type converter that provides a list of values   
/// to be displayed in the property grid.  
/// </summary>  
/// <remarks>This type converter returns a list   
/// of the names of all "ExampleElements" in the   
/// current store.</remarks>  
public class MyTypeConverter : System.ComponentModel.TypeConverter  
{  
  /// <summary>  
  /// Return true to indicate that we return a list of values to choose from  
  /// </summary>  
  /// <param name="context"></param>  
  public override bool GetStandardValuesSupported  
    (System.ComponentModel.ITypeDescriptorContext context)  
  {  
    return true;  
  }  
  
  /// <summary>  
  /// Returns true to indicate that the user has   
  /// to select a value from the list  
  /// </summary>  
  /// <param name="context"></param>  
  /// <returns>If we returned false, the user would   
  /// be able to either select a value from   
  /// the list or type in a value that is not in the list.</returns>  
  public override bool GetStandardValuesExclusive  
      (System.ComponentModel.ITypeDescriptorContext context)  
  {  
    return true;  
  }  
  
  /// <summary>  
  /// Return a list of the values to display in the grid  
  /// </summary>  
  /// <param name="context"></param>  
  /// <returns>A list of values the user can choose from</returns>  
  public override StandardValuesCollection GetStandardValues  
      (System.ComponentModel.ITypeDescriptorContext context)  
  {  
    // Try to get a store from the current context  
    // "context.Instance"  returns the element(s) that   
    // are currently selected i.e. whose values are being  
    // shown in the property grid.   
    // Note that the user could have selected multiple objects,   
    // in which case context.Instance will be an array.  
    Store store = GetStore(context.Instance);  
  
    List<string> values = new List<string>();  
  
    if (store != null)  
    {  
      values.AddRange(store.ElementDirectory  
        .FindElements<ExampleElement>()  
        .Select<ExampleElement, string>(e =>   
      {  
        return e.Name;  
      }));  
    }  
    return new StandardValuesCollection(values);  
  }  
  
  /// <summary>  
  /// Attempts to get to a store from the currently selected object(s)  
  /// in the property grid.  
  /// </summary>  
  private Store GetStore(object gridSelection)  
  {  
    // We assume that "instance" will either be a single model element, or   
    // an array of model elements (if multiple items are selected).  
  
    ModelElement currentElement = null;  
  
    object[] objects = gridSelection as object[];  
    if (objects != null && objects.Length > 0)  
    {  
      currentElement = objects[0] as ModelElement;  
    }  
    else  
    {  
        currentElement = gridSelection as ModelElement;  
    }  
  
    return (currentElement == null) ? null : currentElement.Store;  
  }  
  
}  
  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Program Kodunda Modeli Gezinme ve Güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md)



