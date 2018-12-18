---
title: Bağımlılık diyagramlarına özel mimari doğrulaması ekleme
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, adding custom validation
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: e9343ed8fdb1f3993fcd5c2f70595fd4bdd92dcd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49875456"
---
# <a name="add-custom-architecture-validation-to-dependency-diagrams"></a>Bağımlılık diyagramlarına özel mimari doğrulaması ekleme

Visual Studio'da kaynak kodunu bir bağımlılık diyagramındaki bağımlılıklar için uygun olduğunu doğrulayabilir kullanıcılar kaynak kod projesinde katman modeline karşı doğrulayabilir. Standart doğrulama algoritmasını yoktur ancak kendi doğrulama uzantılarınızı tanımlayabilirsiniz.

Kullanıcı seçtiğinde **Mimariyi Doğrula** standart doğrulama yöntemi çağrılır, yüklenmiş herhangi bir doğrulama uzantısı tarafından izlenen bir bağımlılık diyagramında komutu.

> [!NOTE]
> Bir bağımlılık diyagramda, çözümün diğer bölümlerinde program koduyla diyagramı karşılaştırmak için doğrulama ana amacı budur.

İçine bir Visual Studio Tümleştirme Uzantısı (diğer Visual Studio kullanıcılarına dağıtabilirsiniz, VSIX), katman doğrulama uzantınızı paketleyebilirsiniz. Doğrulayıcı bir VSIX kendisi tarafından yerleştirebilir veya onu diğer uzantılarla aynı VSIX içinde birleştirebilirsiniz. Doğrulayıcının kodunu yazmanız kendi Visual Studio projesi, diğer uzantılarla aynı proje içinde değil.

> [!WARNING]
> Doğrulama projesi oluşturduktan sonra kopyalama [örnek kod](#example) sonunda, bu konuda ve kendi gereksinimleriniz doğrultusunda, düzenleyin.

## <a name="requirements"></a>Gereksinimler

Bkz: [gereksinimleri](../modeling/extend-layer-diagrams.md#prereqs).

## <a name="defining-a-layer-validator-in-a-new-vsix"></a>Yeni VSIX'da bir katman Doğrulayıcı tanımlama

Bir doğrulayıcı oluşturmanın en hızlı yolu, proje şablonu kullanmaktır. Bu seçenek, kodu ve VSIX bildirimini aynı projeye yerleştirir.

### <a name="to-define-an-extension-by-using-a-project-template"></a>Bir proje şablonunu kullanarak bir uzantısı tanımlamak için

1. Kullanarak yeni çözümde bir proje oluşturma **yeni proje** komutunu **dosya** menüsü.

2. İçinde **yeni proje** iletişim kutusunun **modelleme projeleri**seçin **katman Tasarımcı doğrulama uzantısı**.

    Şablon, küçük bir örnek içeren bir proje oluşturur.

   > [!WARNING]
   > Şablonun düzgün çalışmasını sağlamak için:
   >
   > - Çağrılarını düzenleyin `LogValidationError` isteğe bağlı bağımsız değişkenlerini kaldırmak için `errorSourceNodes` ve `errorTargetNodes`.
   > - Özel özellikleri kullanırsanız, belirtilen güncelleştirmesini [bağımlılık diyagramlarına özel özellikler ekleme](../modeling/add-custom-properties-to-layer-diagrams.md).

3. Doğrulamanızı tanımlamak için kodu düzenleyin. Daha fazla bilgi için [doğrulamayı programlama](#programming).

4. Uzantıyı test etmek için bkz: [katman hatalarını ayıklamayı doğrulama](#debugging).

   > [!NOTE]
   > Yönteminiz yalnızca belirli durumlarda çağrılır ve kesme noktaları otomatik olarak çalışmaz. Daha fazla bilgi için [katman hatalarını ayıklamayı doğrulama](#debugging).

5. Visual Studio'nun veya başka bir bilgisayara ana örneğindeki uzantıyı yüklemek için bulma *.vsix* dosyası *bin* dizin. Yüklemek istediğiniz bilgisayara kopyalayın ve ardından çift tıklayın. Kaldırmak için seçin **Uzantılar ve güncelleştirmeler** üzerinde **Araçları** menüsü.

## <a name="adding-a-layer-validator-to-a-separate-vsix"></a>Ayrı bir VSIX'e katman Doğrulayıcı ekleme

Katman doğrulayıcılarının, komutların ve diğer uzantıların bulunduğu bir VSIX oluşturmak istiyorsanız, VSIX tanımlamak için bir proje ve işleyiciler için ayrı projeler oluşturmanızı öneririz.

### <a name="to-add-layer-validation-to-a-separate-vsix"></a>Ayrı bir VSIX'e katman doğrulaması eklemek için

1.  Yeni veya mevcut bir Visual Studio çözümünde bir sınıf kitaplığı projesi oluşturun. İçinde **yeni proje** iletişim kutusu, tıklayın **Visual C#** ve ardından **sınıf kitaplığı**. Bu proje, katman doğrulama sınıfını içerir.

2.  Çözümünüzde bir VSIX projesi oluşturun veya tanımlayın. Adlı bir dosyaya bir VSIX projesi içeren **source.extension.vsixmanifest**. VSIX projesi eklemeniz gerekiyorsa, şu adımları izleyin:

    1.  İçinde **yeni proje** iletişim kutusunda **Visual C#**, **genişletilebilirlik**, **VSIX projesi**.

    2.  İçinde **Çözüm Gezgini**, VSIX projesinin kısayol menüsünde **başlangıç projesi olarak ayarla**.

3.  İçinde **source.extension.vsixmanifest**altında **varlıklar**, katman doğrulama projesini MEF Bileşeni ekleyin:

    1.  Seçin **yeni**.

    2.  İçinde **yeni varlık Ekle** iletişim kutusu, ayarla:

         **Type** = **Microsoft.VisualStudio.MefComponent**

         **Kaynak** = **mevcut çözümde bir proje**

         **Proje** = *Doğrulayıcı projenizi*

4.  Bu katman doğrulaması olarak da eklemelisiniz:

    1.  Seçin **yeni**.

    2.  İçinde **yeni varlık Ekle** iletişim kutusu, ayarla:

         **Tür** = **Microsoft.VisualStudio.ArchitectureTools.Layer.Validator**. Bu açılır listedeki seçeneklerden birini değildir. Bunu klavyeden girmeniz gerekir.

         **Kaynak** = **mevcut çözümde bir proje**

         **Proje** = *Doğrulayıcı projenizi*

5.  Katman doğrulama projesine dön ve aşağıdaki proje başvurularını ekleyin:

    |**Başvuru**|**Bunu yapmak sağlar**|
    |-|-|
    |Microsoft.VisualStudio.GraphModel.dll|Mimari grafiğini oku|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema.dll|Kod DOM katmanlar ile ilişkili okuyun|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Katman modelini okuyun|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility|Okuma ve şekilleri ve diyagramları güncelleştirin.|
    |System.ComponentModel.Composition|Yönetilen Genişletilebilirlik Çerçevesi (MEF) kullanarak doğrulama bileşenini tanımla|
    |Microsoft.VisualStudio.Modeling.Sdk.[version]|Modelleme uzantılarını tanımla|

6.  Bu konunun sonundaki örnek kod, doğrulama kodunu içeren Doğrulayıcı kitaplık projesinin sınıf dosyasına kopyalayın. Daha fazla bilgi için [doğrulamayı programlama](#programming).

7.  Uzantıyı test etmek için bkz: [katman hatalarını ayıklamayı doğrulama](#debugging).

    > [!NOTE]
    > Yönteminiz yalnızca belirli durumlarda çağrılır ve kesme noktaları otomatik olarak çalışmaz. Daha fazla bilgi için [katman hatalarını ayıklamayı doğrulama](#debugging).

8.  VSIX ana örneğine Visual Studio'nun veya başka bir bilgisayara yüklemek için bulma **.vsix** dosyası **bin** VSIX projesinin dizin. VSIX'i yüklemek istediğiniz bilgisayara kopyalayın. Windows Gezgini'ndeki VSIX dosyasına çift tıklayın.

     Kaldırmak için kullanın **Uzantılar ve güncelleştirmeler** üzerinde **Araçları** menüsü.

##  <a name="programming"></a> Programlama doğrulaması

Katman doğrulama uzantısı tanımlamak için aşağıdaki özelliklere sahip bir sınıf tanımlayın:

- Bildirimin genel biçimi aşağıdaki gibidir:

  ```csharp
  using System.ComponentModel.Composition;
  using Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema;
  using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
  using Microsoft.VisualStudio.GraphModel;
  ...
   [Export(typeof(IValidateArchitectureExtension))]
    public partial class Validator1Extension :
                    IValidateArchitectureExtension
    {
      public void ValidateArchitecture(Graph graph)
      {
         GraphSchema schema = graph.DocumentSchema;
        ...
    } }
  ```

- Bir hata bulduğunuzda, bunu kullanarak bildirebilirsiniz `LogValidationError()`.

  > [!WARNING]
  > İsteğe bağlı parametreleri kullanmayın `LogValidationError`.

Kullanıcı ne zaman çağırır **Mimariyi Doğrula** menü komutunu, katman çalışma zamanı sistemi olmaktadır katmanları ve onların yapılarını bir grafik oluşturur. Grafik dört bölümden oluşur:

- Grafik içerisinde düğümler ve bağlantılar olarak gösterilir Visual Studio çözümünün katman modelleri.

- Kod, proje öğeleri ve çözümde tanımlanan ve düğümler ve bağlantılar analiz süreci tarafından bağımlılıkları temsil eden olarak temsil edilen diğer yapıtlar.

- Katman düğümlerinden kod yapı düğümlerine bağlantılar.

- Doğrulayıcı tarafından bulunan hataları temsil eden düğümler.

Grafik oluşturulduğunda standart doğrulama yöntemi çağrılır. Bu tamamlandığında, yüklenen uzantı doğrulama yöntemleri belirtilmemiş sırayla çağrılır. Graf geçirilir `ValidateArchitecture` yöntemi grafiği tarar ve bulduğu tüm hataları bildirin.

> [!NOTE]
> Bu etki alanına özgü dillerde kullanılabilecek doğrulama işlemi ile aynı değildir.

Doğrulama yöntemlerinin katman modelini ya da Doğrulanmakta olan kodu değiştirmemesi gerekir.

Grafik modeli tanımlanan <xref:Microsoft.VisualStudio.GraphModel>. Başlıca sınıflardır <xref:Microsoft.VisualStudio.GraphModel.GraphNode> ve <xref:Microsoft.VisualStudio.GraphModel.GraphLink>.

Her düğüm ve her bağlantı, öğe veya temsil ettiği ilişki türünü belirten bir veya daha fazla kategoriye sahiptir. Tipik bir grafiğin düğümleri aşağıdaki kategorileri içerir:

- Dsl.LayerModel

- Dsl.Layer

- Dsl.Reference

- CodeSchema_Type

- CodeSchema_Namespace

- CodeSchema_Type

- CodeSchema_Method

- CodeSchema_Field

- CodeSchema_Property

Öğeleri kodda katmanlardan bağlantılar "Temsil" Bu kategoriye atanmış.

##  <a name="debugging"></a> Hata ayıklama doğrulama

Katman doğrulama uzantınıza hata ayıklamak için CTRL + F5 tuşlarına basın. Visual Studio deneysel örneği açılır. Bu örnekte, bir katman modeli oluşturun veya açın. Bu model, kodu ile ilişkilendirilmiş olmalıdır ve en az bir bağımlılığı olmalıdır.

### <a name="test-with-a-solution-that-contains-dependencies"></a>Bağımlılıklar içeren bir çözümü test etme

Aşağıdaki özellikler olmadıkça doğrulama yürütülmez:

- Bağımlılık diyagram üzerinde en az bir bağımlılık bağlantısı yoktur.

- Model kod öğeleri ile ilişkili Katmanlar vardır.

Doğrulama uzantınızı test etmek için Visual Studio'nun deneysel örneği ilk başlattığınızda bu özelliklere sahip bir çözüm oluşturun veya açın.

### <a name="run-clean-solution-before-validate-architecture"></a>Mimariyi önce temiz çözümü çalıştırma

Doğrulama kodunuzu güncellediğinizde kullanın **çözümü Temizle** komutunu **derleme** doğrulama komutunu test etmeden önce Deneysel çözümde menüsünde. Bu, doğrulama sonuçları önbelleğe alındığı için gereklidir. Test bağımlılık diyagramı veya buna ait kodu doğrulamadıysanız doğrulama yöntemleri yürütülmez.

### <a name="launch-the-debugger-explicitly"></a>Hata ayıklayıcıyı açık olarak Başlat

Doğrulama, ayrı bir işlemde çalıştırır. Bu nedenle, doğrulama yönteminizdeki kesme noktaları tetiklenmez. Doğrulama başladığında işleme hata ayıklayıcı açıkça eklemeniz gerekir.

Hata ayıklayıcıyı doğrulama işlemine iliştirmek için bir çağrı ekleyin. `System.Diagnostics.Debugger.Launch()` doğrulama yönteminizin başlangıcında. Hata ayıklama iletişim kutusu göründüğünde, Visual Studio ana örneğini seçin.

Alternatif olarak, bir çağrı ekleyebilirsiniz `System.Windows.Forms.MessageBox.Show()`. İleti kutusu göründüğünde, Visual Studio ve ana örneğine gidin **hata ayıklama** menüsünü tıklatın **iliştirme**. Adındaki işlemi seçin **Graphcmd.exe**.

CTRL + F5 tuşlarına basarak deneysel örneği her zaman başlatın (**hata ayıklama olmadan Başlat**).

### <a name="deploying-a-validation-extension"></a>Geçerlilik uzatmayı dağıtma

Doğrulama uzantınızı, uygun bir sürüm, Visual Studio'nun yüklü olduğu bir bilgisayara yüklemek için hedef bilgisayarda VSIX dosyasını açın.

##  <a name="example"></a> Örnek kod

```csharp
using System;
using System.ComponentModel.Composition;
using System.Globalization;
using System.Linq;
using System.Text.RegularExpressions;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
using Microsoft.VisualStudio.GraphModel;

namespace Validator3
{
    [Export(typeof(IValidateArchitectureExtension))]
    public partial class Validator3Extension : IValidateArchitectureExtension
    {
        /// <summary>
        /// Validate the architecture
        /// </summary>
        /// <param name="graph">The graph</param>
        public void ValidateArchitecture(Graph graph)
        {
            if (graph == null) throw new ArgumentNullException("graph");

            // Uncomment the line below to debug this extension during validation
            // System.Windows.Forms.MessageBox.Show("Attach 2 to GraphCmd.exe with process id " + System.Diagnostics.Process.GetCurrentProcess().Id);

            // Get all layers on the diagram
            foreach (GraphNode layer in graph.Nodes.GetByCategory("Dsl.Layer"))
            {
                System.Threading.Thread.Sleep(100);
                // Get the required regex property from the layer node
                string regexPattern = "^[a-zA-Z]+$"; //layer[customPropertyCategory] as string;
                if (!string.IsNullOrEmpty(regexPattern))
                {
                    Regex regEx = new Regex(regexPattern);

                    // Get all referenced types in this layer including those from nested layers so each
                    // type is validated against all containing layer constraints.
                    foreach (GraphNode containedType in layer.FindDescendants().Where(node => node.HasCategory("CodeSchema_Type")))
                    {
                        // Check the type name against the required regex
                        CodeGraphNodeIdBuilder builder = new CodeGraphNodeIdBuilder(containedType.Id, graph);
                        string typeName = builder.Type.Name;
                        if (!regEx.IsMatch(typeName))
                        {
                            // Log an error
                            string message = string.Format(CultureInfo.CurrentCulture, Resources.InvalidTypeNameMessage, typeName);
                            this.LogValidationError(graph, typeName + "TypeNameError", message, GraphErrorLevel.Error, layer);
                        }
                    }
                }

            }

        }
    }
}
```

## <a name="see-also"></a>Ayrıca Bkz.

- [Bağımlılık diyagramlarını genişletme](../modeling/extend-layer-diagrams.md)
