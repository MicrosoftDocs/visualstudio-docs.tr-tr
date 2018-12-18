---
title: Etki alanına özgü dil Tanımıma izleme özelliği ekleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tracking properties [Domain-Specific Language Tools], walkthrough
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
ms.assetid: 4aa47777-de75-4897-a423-a3c4426b4125
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 6103f9601c55b9b29b83866d261d889c5555c86f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894384"
---
# <a name="adding-a-tracking-property-to-a-domain-specific-language-definition"></a>Etki Alanına Özgü Dil Tanımıma İzleme Özelliği Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, bir etki alanı modeline izleme özelliği ekleme işlemi gösterilmektedir.  
  
 A *etki alanı izleme* özellik kullanıcı tarafından güncelleştirilebilir, ancak diğer etki alanı özellikleri veya öğe değerlerini kullanarak hesaplanan bir varsayılan değer olan bir özelliktir.  
  
 Örneğin, etki alanına özgü dil Araçları (DSL araçları), bir alan sınıfının özelliği etki alanı sınıfı, ancak bir kullanıcı adını kullanarak hesaplanan bir varsayılan değere sahip görünen ad değeri tasarım zamanında değiştirebilir veya hesaplanan değere sıfırlayın.  
  
 Bu kılavuzda, modelin varsayılan Namespace özelliği temelinde bir varsayılan değere sahip özellik izleme bir Namespace sahip bir etki alanına özgü dil (DSL) oluşturun. İzleme özellikleri hakkında daha fazla bilgi için bkz. [izleme özellikleri tanımlama](http://msdn.microsoft.com/en-us/0538b0e4-6221-4e7d-911a-b92cd622f0be).  
  
- Özellik tanımlayıcılarının izleme DSL araçları desteği. Ancak, DSL Tasarımcısı izleme özelliği için bir dil eklemek için kullanılamaz. Bu nedenle, izleme özelliği tanımlaması ve özel kod eklemeniz gerekir.  
  
  İki durumlu bir izleme özelliği vardır: izleme ve kullanıcı tarafından güncelleştirilmiş. İzleme özellikleri, aşağıdaki özelliklere sahiptir:  
  
- İzleme durumda olduğu zaman, izleme özelliğinin değeri hesaplanır ve değeri, model değişikliği diğer özellikleri olarak güncelleştirilir.  
  
- Güncelleştirilmiş durumlarda kullanıcı durumuna göre izleme özelliğinin değeri, kullanıcının son özellik değer kümesi korur.  
  
- İçinde **özellikleri** penceresinde **sıfırlama** özelliği güncelleştirilmiş içinde olduğunda yalnızca izleme özelliği etkinleştirilmişse komut kullanıcı durumuna göre. **Sıfırlama** komut izleme özelliği ayarlar durumunu izleme.  
  
- İçinde **özellikleri** normal bir yazı tipinde izleme özelliği değeri izleme durumunda olduğunda penceresinde görüntülenir.  
  
- İçinde **özellikleri** izleme özelliği güncelleştirilmiş olduğunda penceresi kullanıcı durumuna göre bir kalın yazı tipinde değeri görüntülenir.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu kılavuzda başlamadan önce bu bileşenleri yüklemelisiniz:  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|  
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|  
|[!INCLUDE[dsl](../includes/dsl-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185581](http://go.microsoft.com/fwlink/?LinkID=185581)|  
  
## <a name="creating-the-dsl-project"></a>DSL projesi oluşturma  
 Etki alanına özgü dil projesi oluşturun.  
  
#### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
1.  Bir etki alanına özgü dil tasarımcısını projesi oluşturun. Adlandırın `TrackingPropertyDSL`.  
  
2.  İçinde **etki alanına özgü dil Tasarımcısı Sihirbazı**, aşağıdaki seçenekleri belirleyin:  
  
    1.  Seçin **MinimalLanguage** şablonu.  
  
    2.  Etki alanına özgü dil için varsayılan adı kullanın `TrackingPropertyDSL`.  
  
    3.  Model dosyaları uzantı ayarlanmaya `trackingPropertyDsl`.  
  
    4.  Model dosyaları için varsayılan şablon simgesi kullanın.  
  
    5.  Ürüne adını ayarlayın `Product Name`.  
  
    6.  Şirket adı ayarlayın `Company Name`.  
  
    7.  Çözümdeki projelerin kök ad alanı için varsayılan değeri kullanın `CompanyName.ProductName.TrackingPropertyDSL`.  
  
    8.  Derlemeleriniz için bir tanımlayıcı ad anahtar dosyası oluşturmak için Sihirbazı sağlar.  
  
    9. Çözüm ayrıntılarını gözden geçirin ve ardından **son** DSL tanımı projesi oluşturmak için.  
  
## <a name="customizing-the-default-dsl-definition"></a>Varsayılan DSL tanımını özelleştirme  
 Bu bölümde, DSL tanımını aşağıdaki öğeleri içerecek şekilde özelleştirin:  
  
-   Bir Namespace özelliği modelinin her öğe için izleme.  
  
-   Modelin her öğe için bir Boole IsNamespaceTracking özelliği. Bu özellik izleme özelliği durumunu izlemek veya güncelleştirilmiş olup olmadığını belirten kullanıcı durumuna göre.  
  
-   Modelin varsayılan Namespace özelliği. Bu özellik, özellik izleme Namespace varsayılan değerini hesaplamak için kullanılır.  
  
-   Modelin CustomElements hesaplanan özellik. Bu özellik, özel bir ad alanı olan öğeler oranını gösterir.  
  
#### <a name="to-add-the-domain-properties"></a>Etki alanı özellikleri eklemek için  
  
1.  DSL Tasarımcısı'nda sağ **ExampleModel** etki alanı sınıfı, noktasına **Ekle**ve ardından **DomainProperty**.  
  
    1.  Yeni özellik adı `DefaultNamespace`.  
  
    2.  İçinde **özellikleri** penceresini yeni bir özellik için **varsayılan değer** için `DefaultNamespace`, ayarlayıp **türü** için **dize**.  
  
2.  İçin **ExampleModel** etki alanı sınıfı, adlı bir alan özelliği eklemek `CustomElements`.  
  
     İçinde **özellikleri** penceresini yeni bir özellik için **tür** için **hesaplanan**.  
  
3.  İçin **ExampleElement** etki alanı sınıfı, adlı bir alan özelliği eklemek `Namespace`.  
  
     İçinde **özellikleri** penceresini yeni bir özellik için **olan gözatılabilir** için **False**, ayarlayıp **tür** için **CustomStorage** .  
  
4.  İçin **ExampleElement** etki alanı sınıfı, adlı bir alan özelliği eklemek `IsNamespaceTracking`.  
  
     İçinde **özellikleri** penceresini yeni bir özellik için **olan gözatılabilir** için **False**ayarlayın **varsayılan değer** için `true`ve ayarlayın **Türü** için **Boole**.  
  
#### <a name="to-update-the-diagram-elements-and-dsl-details"></a>DSL ayrıntıları ve diyagram öğeleri güncelleştirmek için  
  
1.  DSL Tasarımcısı'nda sağ **ExampleShape** geometri şekli, noktasına **Ekle**ve ardından **metin Dekoratör**.  
  
    1.  Yeni metin dekoratörün adı `NamespaceDecorator`.  
  
    2.  İçinde **özellikleri** metin dekoratör için penceresini ayarlamak **konumu** için **InnerBottomLeft**.  
  
2.  DSL Tasarımcısı'nda bağlanan satırı seçin **ExampleElement** sınıfının **ExampleShape** şekli.  
  
    1.  İçinde **DSL ayrıntıları** penceresinde **Dekoratör eşlemeleri** sekmesi.  
  
    2.  İçinde **dekoratörler** listesinden **NamespaceDecorator**, onay kutusunu seçin ve ardından **görüntü özelliği** listesinden **Namespace**.  
  
3.  İçinde **DSL Gezgini**, genişletin **alan sınıfları** klasörü sağ tıklatın **ExampleElement** düğümünü ve ardından **ekleme yeni etki alanı tür tanımlayıcısı**.  
  
    1.  Genişletin **ExampleElement** düğüm ve select **özel tür tanımlayıcı (etki alanı tür tanımlayıcısı)** düğümü.  
  
    2.  İçinde **özellikleri** etki alanı tür tanımlayıcısı için penceresini ayarlamak **özel kodlanmış** için **True**.  
  
4.  İçinde **DSL Gezgini**seçin **Xml serileştirme davranışı** düğümü.  
  
    1.  İçinde **özellikleri** penceresinde **özel son yükleme** için **True**.  
  
## <a name="transforming-templates"></a>Şablonları dönüştürülüyor  
 DSL'nizi için etki alanı sınıfları ve özellikleri tanımlayarak, DSL tanımını projeniz için kodu yeniden oluşturmak için doğru şekilde dönüştürülebilir doğrulayabilirsiniz.  
  
#### <a name="to-transform-the-text-templates"></a>Metin şablonlarını dönüştürmek için  
  
1.  Üzerinde **Çözüm Gezgini** araç çubuğunda tıklatın **tüm Şablonları Dönüştür**.  
  
2.  Sistem, çözüm için kod oluşturur ve DslDefinition.dsl kaydeder. Tanım dosyalarını XML biçimi hakkında daha fazla bilgi için bkz. [DslDefinition.dsl dosyası](../modeling/the-dsldefinition-dsl-file.md).  
  
## <a name="creating-files-for-custom-code"></a>Dosyaları için özel kod oluşturma  
 Tüm Şablonları dönüştürdüğünüzde, sistem, etki alanına özgü dil tanımlayan Dsl ve DslPackage projelerinde kaynak kodunu oluşturur. Oluşturulan metin ile müdahaleyi önlemek, böylece özel kodunuz tarafından oluşturulan kodun dosyalarından farklı olan dosyaları yazın.  
  
 Değer ve izleme özelliğinizi durumunu korumak için kod sağlamanız gerekir. Özel kodunuz üretilen koddan ayırt etmenize yardımcı olmak ve dosya adlandırma çakışmalarını önlemek için özel kod dosyalarınızı ayrı bir alt klasöre yerleştirin.  
  
#### <a name="to-create-the-code-files"></a>Kod dosyaları oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, sağ **DSL** proje, işaret **Ekle**ve ardından **yeni klasör**. Yeni klasör adı `CustomCode`.  
  
2.  Yeni sağ **CustomCode** klasörünü **Ekle**ve ardından **yeni öğe**.  
  
3.  Seçin **kod dosyası** şablonu, **adı** için `NamespaceTrackingProperty.cs`ve ardından **Tamam**.  
  
     NamespaceTrackingProperty.cs dosya oluşturulur ve düzenleme için açılır.  
  
4.  Klasöründe, aşağıdaki kod dosyalarını oluşturun: `ExampleModel.cs,``HelperClasses.cs`, `Serialization.cs`, ve `TypeDescriptor.cs`.  
  
5.  İçinde **DslPackage** oluşturabilir, proje bir `CustomCode` klasör ve eklemek bir `Package.cs` kod dosyası.  
  
## <a name="adding-helper-classes-to-support-tracking-properties"></a>İzleme özellikleri desteklemek için yardımcı sınıfları ekleme  
 HelperClasses.cs dosyasına ekleme `TrackingHelper` ve `CriticalException` gibi sınıfları. Bu kılavuzda daha sonra bu sınıfların başvurur.  
  
#### <a name="to-add-the-helper-classes"></a>Yardımcı sınıfları eklemek için  
  
1.  HelperClasses.cs dosyaya aşağıdaki kodu ekleyin.  
  
    ```csharp  
    using System;  
    using System.Collections;  
    using System.Diagnostics;  
    using Microsoft.VisualStudio.Modeling;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        internal static class TrackingHelper  
        {  
            /// <summary>Notify each model element in a collection that a tracked  
            /// property has changed.</summary>  
            /// <param name="store">The store for the model.</param>  
            /// <param name="collection">The collection of model elements that  
            /// contain the tracking property.</param>  
            /// <param name="propertyId">The ID of the tracking property.</param>  
            /// <param name="trackingPropertyId">The ID of the property that  
            /// indicates whether the tracking property is tracking.</param>  
            internal static void UpdateTrackingCollectionProperty(  
                Store store,  
                IEnumerable collection,  
                Guid propertyId,  
                Guid trackingPropertyId)  
            {  
                DomainPropertyInfo propInfo =  
                    store.DomainDataDirectory.GetDomainProperty(propertyId);  
  
                DomainPropertyInfo trackingPropInfo =  
                    store.DomainDataDirectory.GetDomainProperty(trackingPropertyId);  
  
                Debug.Assert(propInfo != null);  
                Debug.Assert(trackingPropInfo != null);  
                Debug.Assert(trackingPropInfo.PropertyType.Equals(typeof(bool)),  
                    "Tracking property not specified as a boolean");  
  
                foreach (ModelElement element in collection)  
                {  
                    // If the tracking property is currently tracking, then notify  
                    // it that the tracked property has changed.  
                    bool isTracking = (bool)trackingPropInfo.GetValue(element);  
                    if (isTracking)  
                    {  
                        propInfo.NotifyValueChange(element);  
                    }  
                }  
            }  
        }  
  
        /// <summary>Helper class to flag critical exceptions from ones that are  
        /// safe to ignore.</summary>  
        internal static class CriticalException  
        {  
            /// <summary>Gets whether an exception is critical and can not be  
            /// ignored.</summary>  
            /// <param name="ex">The exception to check.</param>  
            /// <returns>True if the exception is critical.</returns>  
            internal static bool IsCriticalException(Exception ex)  
            {  
                if (ex is NullReferenceException  
                    || ex is StackOverflowException  
                    || ex is OutOfMemoryException  
                    || ex is System.Threading.ThreadAbortException)  
                    return true;  
  
                if (ex.InnerException != null)  
                    return IsCriticalException(ex.InnerException);  
  
                return false;  
            }  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-for-the-custom-type-descriptor"></a>Özel tür tanımlayıcısı özel kod ekleme  
 Uygulama `GetCustomProperties` yöntemi tür tanımlayıcısı için `ExampleModel` etki alanı sınıfı.  
  
> [!NOTE]
>  DSL araçları için özel tür tanımlayıcısının oluşturan kodu `ExampleModel` çağrıları `GetCustomProperties`; ancak, DSL araçları yöntemini uygulayan kod oluşturmaz.  
  
 Bu yöntem tanımlama oluşturur izleme özelliği izleme Namespace özelliği tanımlayıcısı. Ayrıca öznitelikler için izleme özelliği sağlayan sağlayan **özellikleri** özelliği doğru bir şekilde görüntülemek için penceresi.  
  
#### <a name="to-modify-the-type-descriptor-for-the-examplemodel-domain-class"></a>Tür tanımlayıcısını ExampleModel alan sınıfına yönelik değiştirmek için  
  
1.  TypeDescriptor.cs dosyaya aşağıdaki kodu ekleyin.  
  
    ```csharp  
    using System;  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Modeling;  
    using Microsoft.VisualStudio.Modeling.Design;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        // To the custom type descriptor for the ExampleElement domain class, add  
        // the GetCustomProperties method.  
        public partial class ExampleElementTypeDescriptor  
        {  
            /// <summary>Returns the property descriptors for the described  
            /// ExampleElement domain class.</summary>  
            /// <remarks>This method adds the tracking property descriptor.  
            /// </remarks>  
            private PropertyDescriptorCollection GetCustomProperties(  
                Attribute[] attributes)  
            {  
                // Get the default property descriptors from the base class  
                PropertyDescriptorCollection propertyDescriptors =  
                    base.GetProperties(attributes);  
  
                // Get a reference to the model element that is being described.  
                ExampleElement source = this.ModelElement as ExampleElement;  
  
                //Add the descriptor for the tracking property.  
                if (source != null)  
                {  
                    DomainPropertyInfo domainProperty =  
                        source.Store.DomainDataDirectory.GetDomainProperty(  
                            ExampleElement.NamespaceDomainPropertyId);  
  
                    DomainPropertyInfo trackingProperty =  
                        source.Store.DomainDataDirectory.GetDomainProperty(  
                            ExampleElement.IsNamespaceTrackingDomainPropertyId);  
  
                    // Define attributes for the tracking property so that the  
                    // Properties window displays the property correctly.  
                    Attribute[] attr = new Attribute[] {  
                        new DisplayNameAttribute("Element Namespace"),  
                        new DescriptionAttribute("The namespace of the element."),  
                        new CategoryAttribute("Tracking Properties"),  
                    };  
  
                    propertyDescriptors.Add(new TrackingPropertyDescriptor(  
                        source, domainProperty, trackingProperty, attr));  
                }  
  
                // Return the property descriptors for this element  
                return propertyDescriptors;  
            }  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-for-the-package"></a>Paket için özel kod ekleme  
 Oluşturulan kodun ExampleElement alan sınıfına yönelik bir tür açıklama sağlayıcısı tanımlar; Ancak, bu tür açıklama sağlayıcısı kullanmak için DSL istemek için kod eklemeniz gerekir.  
  
#### <a name="to-update-the-dsl-package-to-use-your-custom-type-descriptor"></a>Kendi özel tür tanımlayıcısının kullanmak için DSL paketi güncellemek için  
  
1.  Aşağıdaki kodu Package.cs dosyasına ekleyin.  
  
    ```csharp  
    using System.ComponentModel;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        // Override the default Initialize method.  
        internal sealed partial class TrackingPropertyDSLPackage  
        {  
            protected override void Initialize()  
            {  
                // Add the custom type descriptor for the ExampleElement type.  
                TypeDescriptor.AddProvider(  
                    new ExampleElementTypeDescriptionProvider(),  
                    typeof(ExampleElement));  
  
                base.Initialize();  
            }  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-for-the-model"></a>Model için özel kod ekleme  
 Uygulama `GetCustomElementsValue` yöntemi `ExampleModel` etki alanı sınıfı.  
  
> [!NOTE]
>  DSL araçları için oluşturan kodu `ExampleModel` çağrıları `GetCustomElementsValue`; ancak, DSL araçları yöntemini uygulayan kod oluşturmaz.  
  
 Tanımlama `GetCustomElementsValue` yöntemi hesaplanan CustomElements özelliği için mantığı sağlar `ExampleModel`. Bu yöntem sayar `ExampleElement` kullanıcı güncelleştirilmiş bir değeri yok ve bu sayı bütünün modelinde toplam öğe olarak temsil eden bir dize döndürür özelliği izleme bir Namespace sahip alan sınıfları.  
  
 Ayrıca, ekleme bir `OnDefaultNamespaceChanged` yönteme `ExampleModel`ve geçersiz kılma `OnValueChanged` yöntemi `DefaultNamespacePropertyHandler` iç içe sınıf `ExampleModel` çağırmak için `OnDefaultNamespaceChanged`.  
  
 İzleme özelliği, Namespace hesaplamak için, DefaultNamespace özelliği kullanıldığından `ExampleModel` tüm bilgilendirmelisiniz `ExampleElement` değeri, DefaultNamespace değişti alan sınıfları.  
  
#### <a name="to-modify-the-property-handler-for-the-tracked-property"></a>İzlenen bir özellik için özellik işleyicisi değiştirmek için  
  
1.  ExampleModel.cs dosyaya aşağıdaki kodu ekleyin.  
  
    ```csharp  
    using System.Linq;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        public partial class ExampleModel  
        {  
            public string GetCustomElementsValue()  
            {  
                if (this.Elements.Count == 0) return "0/0";  
  
                int number = this.Elements.Count(e => !e.IsNamespaceTracking);  
                return string.Format("{0}/{1}", number, this.Elements.Count);  
            }  
  
            #region Value changed handler for the tracked property  
  
            // When a tracked property changes, it needs to notify all of the properties  
            // that track it.  
  
            /// <summary>Called by the DefaultNamespace property value handler when the  
            /// DefaultNamespace property changes.</summary>  
            /// <param name="oldValue">The previous value of the property.</param>  
            /// <param name="newValue">The new value of the property.</param>  
            protected virtual void OnDefaultNamespaceChanged(  
                string oldValue, string newValue)  
            {  
                // Use the helper class to notify all of the elements in the model  
                // that the default namespace has changed.  
                TrackingHelper.UpdateTrackingCollectionProperty(  
                    this.Store,  
                    this.Elements,  
                    ExampleElement.NamespaceDomainPropertyId,  
                    ExampleElement.IsNamespaceTrackingDomainPropertyId);  
            }  
  
            // Update the change handler for the DefaultNamespace property.  
            internal sealed partial class DefaultNamespacePropertyHandler  
            {  
                /// <summary>Called when the DefaultNamespace property changes.</summary>  
                /// <param name="element">The model element that has the property that  
                /// changed.</param>  
                /// <param name="oldValue">The previous value of the property.</param>  
                /// <param name="newValue">The new value of the property.</param>  
                protected override void OnValueChanged(  
                    ExampleModel element, string oldValue, string newValue)  
                {  
                    base.OnValueChanged(element, oldValue, newValue);  
  
                    if (!element.Store.InUndoRedoOrRollback)  
                    {  
                        element.OnDefaultNamespaceChanged(oldValue, newValue);  
                    }  
                }  
            }  
  
            #endregion  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-for-the-tracking-property"></a>İzleme özelliği için özel kod ekleme  
 Ekleme bir `CalculateNamespace` yönteme `ExampleElement` etki alanı sınıfı.  
  
 Bu yöntem tanımlamak, hesaplanan CustomElements özelliği için mantığı sağlar `ExampleModel`. Bu yöntem sayar `ExampleElement` izleme güncelleştirilmiş olan özellik bir Namespace olan etki alanı sınıfları tarafından kullanıcı durumunu ve bu sayı bütünün modelinde toplam öğe olarak temsil eden bir dize döndürür.  
  
 Ayrıca, depolama için ve almak ve Namespace özel depolama özelliğini ayarlamak için yöntemleri ekleyin `ExampleElement` etki alanı sınıfı.  
  
> [!NOTE]
>  DSL araçları için oluşturan kodu `ExampleModel` get çağrıları ve ayarlamanıza yöntemleri; ancak, DSL araçları yöntemlerini uygulayan kod oluşturmaz.  
  
#### <a name="to-add-the-method-for-the-custom-type-descriptor"></a>Özel tür tanımlayıcısının yöntemi eklemek için  
  
1.  NamespaceTrackingProperty.cs dosyaya aşağıdaki kodu ekleyin.  
  
    ```csharp  
    using System;  
    using Microsoft.VisualStudio.Modeling;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        // To the domain class that has the tracking property, add the caluclation  
        // for when the property is tracking.  
        public partial class ExampleElement  
        {  
            /// <summary>Calculates the actual value of the property when it is  
            /// tracking.</summary>  
            /// <returns>The value of the tracking property when it is  
            /// tracking.</returns>  
            /// <remarks>Making this method virtual allows child classes to modify  
            /// the calculation. This method does not need to perform validation, as  
            /// its caller handles validation prior to calling this method.  
            /// <para>In this case, the tracking value depends on the default namespace  
            /// property of the parent model.</para></remarks>  
            protected virtual string CalculateNamespace()  
            {  
                return this.ExampleModel.DefaultNamespace;  
            }  
  
            #region Tracking property implementation  
  
            // Implement the Namespace domain property of the ExampleElement domain class,  
            // and update the IsNamespaceTracking domain property value handler.  
  
            /// <summary>Storage for the Namespace property.</summary>  
            private string namespaceStorage;  
  
            /// <summary>Gets the value of the Namespace property.</summary>  
            /// <returns>The value of the Namespace property.</returns>  
            private string GetNamespaceValue()  
            {  
                // Only retrieve the tracked value if the store is not in the  
                // middle of a serialization transaction.  
                bool loading = this.Store.TransactionManager.InTransaction  
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;  
  
                if (!loading && this.IsNamespaceTracking)  
                {  
                    try  
                    {  
                        return this.CalculateNamespace();  
                    }  
                    catch (NullReferenceException)  
                    {  
                        return default(string);  
                    }  
                    catch (Exception e)  
                    {  
                        if (CriticalException.IsCriticalException(e))  
                        {  
                            throw;  
                        }  
                        else  
                        {  
                            return default(string);  
                        }  
                    }  
                }  
  
                return namespaceStorage;  
            }  
  
            /// <summary>Sets the value of the Namespace property.</summary>  
            /// <param name="value">The new value for the property.</param>  
            private void SetNamespaceValue(string value)  
            {  
                namespaceStorage = value;  
  
                // Only update the state of the tracking property if the store is  
                // not in the middle of a serialization transaction.  
                bool loading = this.Store.TransactionManager.InTransaction  
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;  
  
                if (!this.Store.InUndoRedoOrRollback && !loading)  
                {  
                    this.IsNamespaceTracking = false;  
                }  
            }  
  
            // Update the default behavior of the ExampleElement.IsNamespaceTracking  
            // domain property value handler.  
            internal sealed partial class IsNamespaceTrackingPropertyHandler  
            {  
                /// <summary>Called after the IsNamespaceTracking property changes.  
                /// </summary>  
                /// <param name="element">The model element that has the property  
                /// that changed.</param>  
                /// <param name="oldValue">The previous value of the property.  
                /// </param>  
                /// <param name="newValue">The new value of the property.</param>  
                protected override void OnValueChanged(  
                    ExampleElement element, Boolean oldValue, Boolean newValue)  
                {  
                    base.OnValueChanged(element, oldValue, newValue);  
                    if (!element.Store.InUndoRedoOrRollback && newValue)  
                    {  
                        DomainPropertyInfo propInfo =  
                            element.Store.DomainDataDirectory.GetDomainProperty(  
                                ExampleElement.NamespaceDomainPropertyId);  
                        propInfo.NotifyValueChange(element);  
                    }  
                }  
  
                /// <summary>Performs the reset operation for the IsNamespaceTracking  
                /// property for a model element.</summary>  
                /// <param name="element">The model element that has the property  
                /// to reset.</param>  
                internal void ResetValue(ExampleElement element)  
                {  
                    object calculatedValue = null;  
  
                    try  
                    {  
                        calculatedValue = element.CalculateNamespace();  
                    }  
                    catch (NullReferenceException)  
                    {  
                    }  
                    catch (System.Exception e)  
                    {  
                        if (CriticalException.IsCriticalException(e))  
                        {  
                            throw;  
                        }  
                    }  
  
                    if ((calculatedValue != null  
                        && object.Equals(element.Namespace, calculatedValue)))  
                    {  
                        element.isNamespaceTrackingPropertyStorage = true;  
                    }  
                }  
  
                /// <summary>Method to set IsNamespaceTracking to false so that this  
                /// instance of this tracking property is not storage-based.  
                /// </summary>  
                /// <param name="element">The element on which to reset the property  
                /// value.</param>  
                internal void PreResetValue(ExampleElement element)  
                {  
                    // Force the IsNamespaceTracking property to false so that the value  
                    // of the Namespace property is retrieved from storage.  
                    element.isNamespaceTrackingPropertyStorage = false;  
                }  
            }  
  
            #endregion  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-to-support-serialization"></a>Serileştirme desteklemek için özel kod ekleme  
 XML serileştirme için özel yükleme sonrası davranışı desteklemek için kod ekleyin.  
  
> [!NOTE]
>  DSL araçları çağrıları oluşturmak, kod `OnPostLoadModel` ve `OnPostLoadModelAndDiagram` yöntemleri; ancak, DSL araçları bu yöntemleri uygulayan kod oluşturmaz.  
  
#### <a name="to-add-code-to-support-the-custom-post-load-behavior"></a>Özel yükleme sonrası davranışı desteklemek üzere kod eklemek için  
  
1.  Serialization.cs dosyaya aşağıdaki kodu ekleyin.  
  
    ```csharp  
    using System;  
    using System.Diagnostics;  
    using Microsoft.VisualStudio.Modeling;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        #region Helper classes for maintaining state while the store is serializing.  
  
        public abstract partial class TrackingPropertyDSLSerializationHelperBase  
        {  
            /// <summary>Reset the tracking state properties to their natural values  
            /// based on comparing storage with calculation.</summary>  
            /// <param name="store">The store that contains this model.</param>  
            internal static void ResetTrackingProperties(Store store)  
            {  
                // Two passes required - one to set all elements to storage-based  
                // then another to set some back to being tracking.  
                foreach (ModelElement element in store.ElementDirectory.AllElements)  
                {  
                    ExampleElement myElementInstance = element as ExampleElement;  
                    if (myElementInstance != null)  
                    {  
                        myElementInstance.PreResetIsTrackingProperties();  
                        continue;  
                    }  
                }  
                foreach (ModelElement element in store.ElementDirectory.AllElements)  
                {  
                    ExampleElement myElementInstance = element as ExampleElement;  
                    if (myElementInstance != null)  
                    {  
                        myElementInstance.ResetIsTrackingProperties();  
                        continue;  
                    }  
                }  
            }  
        }  
  
        // Add the pre-reset and reset methods for the model element.  
        public partial class ExampleElement  
        {  
            /// <summary>Calls the pre-reset method on the associated property value  
            /// handler for each tracking property of this model element.</summary>  
            internal virtual void PreResetIsTrackingProperties()  
            {  
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.PreResetValue(this);  
            }  
  
            /// <summary>Calls the reset method on the associated property value  
            /// handler for each tracking property of this model element.</summary>  
            internal virtual void ResetIsTrackingProperties()  
            {  
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.ResetValue(this);  
            }  
        }  
  
        #endregion  
  
        #region Custom serialization code  
  
        // To the serialization helper for the TrackingPropertyDSL class, add post  
        // load handlers to bind the tracking property to the serialization process.  
        // These handlers manage the tracking states and property values when the  
        // model is serialized and deserialized.  
        public partial class TrackingPropertyDSLSerializationHelperBase  
        {  
            /// <summary>Customize model loading.</summary>  
            /// <param name="serializationResult">The serialization result from the  
            /// load operation.</param>  
            /// <param name="partition">The partition in which the new  
            /// instance was created.</param>  
            /// <param name="fileName">The name of the file from which the  
            /// instance was deserialized.</param>  
            /// <param name="modelRoot">The root of the file that was loaded.  
            /// </param>  
            private void OnPostLoadModel(  
                SerializationResult serializationResult,  
                Partition partition,  
                string fileName,  
                ExampleModel modelRoot)  
            {  
            }  
  
            /// <summary>Customize model and diagram loading.</summary>  
            /// <param name="serializationResult">Stores serialization result from  
            /// the load operation.</param>  
            /// <param name="modelPartition">Partition in which the new  
            /// instance will be created.</param>  
            /// <param name="modelFileName">Name of the file from which the  
            /// instance will be deserialized.</param>  
            /// <param name="diagramPartition">Partition in which the new  
            /// diagram instance will be created.</param>  
            /// <param name="diagramFileName">Name of the file from which the  
            /// diagram instance will be deserialized.</param>  
            /// <param name="modelRoot">The root of the file that was loaded.</param>  
            /// <param name="diagram">The diagram matching the modelRoot.</param>  
            private void OnPostLoadModelAndDiagram(  
                SerializationResult serializationResult,  
                Partition modelPartition,  
                string modelFileName,  
                Partition diagramPartition,  
                string diagramFileName,  
                ExampleModel modelRoot,  
                TrackingPropertyDSLDiagram diagram)  
            {  
                Debug.Assert(modelPartition != null);  
                Debug.Assert(modelPartition.Store != null);  
  
                // Tracking properties need to be set up according to whether the  
                // serialization matches the calculated values.  
                TrackingPropertyDSLSerializationHelperBase.ResetTrackingProperties(  
                    modelPartition.Store);  
            }  
        }  
  
        #endregion  
    }  
    ```  
  
## <a name="testing-the-language"></a>Dil test etme  
 Sonraki adım yeni bir örneğini DSL Tasarımcısı oluşturmak ve çalıştırmaktır [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] böylece izleme özelliği doğru şekilde çalışıp çalışmadığını doğrulayabilirsiniz.  
  
#### <a name="to-exercise-the-language"></a>Dili kullanmak için  
  
1.  Üzerinde **derleme** menüsünde tıklatın **çözümü yeniden derle**.  
  
2.  Üzerinde **hata ayıklama** menüsünü tıklatın **hata ayıklamayı Başlat**.  
  
     Deneysel yapısını [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] açılır **hata ayıklama** boş test dosyasını içeren çözüm.  
  
3.  İçinde **Çözüm Gezgini**Test.trackingPropertyDsl tasarımcıda açmak için dosyaya çift tıklayın ve tasarım yüzeyine'ye tıklayın.  
  
     Dikkat **özellikleri** penceresinde diyagramın **varsayılan Namespace** özelliği **DefaultNamespace**ve **özelöğeler** özelliği **0/0**.  
  
4.  Sürükleme bir **ExampleElement** öğesinden **araç kutusu** diyagramı yüzeyine bırakın.  
  
5.  İçinde **özellikleri** pencere öğesi, select için **öğesi Namespace** özelliği ve değerini **DefaultNamespace** için  **OtherNamespace**.  
  
     Dikkat değerini **öğesi Namespace** artık kalın olarak gösterilir.  
  
6.  İçinde **özellikleri** penceresinde sağ **öğesi Namespace**ve ardından **sıfırlama**.  
  
     Özelliğinin değeri olarak değiştirilir **DefaultNamespace**, ve değer normal bir yazı tipinde gösterilir.  
  
     Sağ **öğesi Namespace** yeniden. **Sıfırlama** komutu artık devre dışı özelliği şu anda, izleme durumunda olduğundan.  
  
7.  Başka bir sürükleyin **ExampleElement** gelen **araç kutusu** diyagramı yüzeyine bırakın ve değişiklik kendi **öğesi Namespace** için **OtherNamespace**.  
  
8.  Tasarım yüzeyine tıklayın.  
  
     İçinde **özellikleri** penceresinde diyagramın değerini **özel öğeleri** artık **1/2**.  
  
9. Değişiklik **varsayılan Namespace** diyagramdan için **DefaultNamespace** için **NewNamespace**.  
  
     **Namespace** ilk öğesi parçalarının **varsayılan Namespace** özelliği, oysa **Namespace** ikinci öğe -güncelkullanıcıkendideğerinikorur. **OtherNamespace**.  
  
10. Çözüm kaydedin ve ardından Deneysel derleme kapatın.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Birden fazla izleme özelliğini kullanın veya birden çok DSL içinde izleme özellikleri uygulayan planlıyorsanız, her izleme özelliği desteklemek için ortak kod üretmek için bir metin şablonu oluşturabilirsiniz. Metin şablonları hakkında daha fazla bilgi için bkz. [kod oluşturma ve T4 metin şablonları](../modeling/code-generation-and-t4-text-templates.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Modeling.Design.TrackingPropertyDescriptor>   
 <xref:Microsoft.VisualStudio.Modeling.Design.ElementTypeDescriptor>   
 [Bir etki alanına özgü dil tanımlama](../modeling/how-to-define-a-domain-specific-language.md)   
 [Nasıl yapılır: bir etki alanına özgü dil çözümü oluşturma](../modeling/how-to-create-a-domain-specific-language-solution.md)   
 [İzlenecek yol: etki alanına özgü dil tanımını özelleştirme](../misc/walkthrough-customizing-the-domain-specific-language-definition.md)



