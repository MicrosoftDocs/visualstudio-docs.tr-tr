---
title: "İzlenecek yol: Görselleştiriciyi C# ' de yazma | Microsoft Docs"
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: 53467461-8e0f-45ee-9bc4-374bbaeaf00f
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e265810e30423064e27b1650f57fb054743341ce
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817340"
---
# <a name="walkthrough-writing-a-visualizer-in-c"></a>İzlenecek Yol: C# ile Görselleştirici Yazma #
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu kılavuz, C# kullanarak basit Görselleştirici yazma işlemi gösterilmektedir. Bu izlenecek yolda oluşturacağınız Görselleştirici, bir Windows forms ileti kutusunu kullanarak bir dizenin içeriklerini görüntüler. Bu basit dize Görselleştirici kendisi özellikle kullanışlı değildir, ancak diğer veri türleri için daha faydalı görselleştiriciler oluşturmak için izlemeniz gereken temel adımlarda gösterilir.  
  
> [!NOTE]
>  İletişim kutuları ve menü komutları gördüğünüz açıklanana Yardım'da, etkin ayarlarınıza ve sürüm bağlı olarak farklı olabilir. Ayarlarınızı değiştirmek için Git **Araçları** menüsünü seçip **içeri ve dışarı aktarma ayarları**. Daha fazla bilgi için [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Görselleştirici kod bir DLL'de hata ayıklayıcı tarafından okunacak yerleştirilmelidir. Bu nedenle, ilk adım bir sınıf kitaplığı projesi DLL için oluşturmaktır.  
  
#### <a name="to-create-a-class-library-project"></a>Bir sınıf kitaplığı projesi oluşturmak için  
  
1. Üzerinde **dosya** menüsünde seçin **yeni** ve ardından **yeni proje**.  
  
2. İçinde **yeni proje** iletişim kutusunun **proje türü**s, select **Visual C#**.  
  
3. İçinde **şablonları** kutusunda **sınıf kitaplığı**.  
  
4. İçinde **adı** MyFirstVisualizer gibi bir sınıf kitaplığı için uygun bir ad yazın.  
  
5. **Tamam**'ı tıklatın.  
  
   Sınıf kitaplığı oluşturduktan sonra tanımlanan sınıflara var. kullanabilmesi için Microsoft.VisualStudio.DebuggerVisualizers.DLL bir başvuru eklemeniz gerekir. Ancak, başvuru eklemeden önce böylece sahip oldukları anlamlı adlar bazı sınıfları yeniden adlandırmanız gerekir.  
  
#### <a name="to-rename-class1cs-and-add-microsoftvisualstudiodebuggervisualizers"></a>Class1.cs yeniden adlandırıp Microsoft.VisualStudio.DebuggerVisualizers Ekle  
  
1. İçinde **Çözüm Gezgini**Class1.cs sağ tıklatın ve seçin **Yeniden Adlandır** kısayol menüsünde.  
  
2. Ad Class1.cs DebuggerSide.cs gibi anlamlı değiştirin.  
  
   > [!NOTE]
   >  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sınıf bildirimi içinde DebuggerSide.cs yeni dosya adı ile eşleşecek şekilde otomatik olarak değiştirir.  
  
3. İçinde **Çözüm Gezgini**, sağ **başvuruları** ve **Başvuru Ekle** kısayol menüsünde.  
  
4. İçinde **Başvuru Ekle** iletişim kutusundaki **.NET** sekmesinde, Microsoft.VisualStudio.DebuggerVisualizers.DLL seçin.  
  
5. **Tamam**'ı tıklatın.  
  
6. Aşağıdaki deyime DebuggerSide.cs içinde ekleyin `using` ifadeleri:  
  
   ```  
   using Microsoft.VisualStudio.DebuggerVisualizers;  
   ```  
  
   Hata ayıklayıcı tarafından çalışan kod oluşturmaya hazırsınız. Görselleştirmek istediğiniz bilgileri görüntülemek için hata ayıklayıcısı içinde çalıştırılan kod budur. İlk olarak, bildirimini değiştirmek zorunda `DebuggerSide` taban sınıfından devralan şekilde nesne `DialogDebuggerVisualizer`.  
  
#### <a name="to-inherit-from-dialogdebuggervisualizer"></a>DialogDebuggerVisualizer devralacak şekilde  
  
1. Aşağıdaki kod satırını DebuggerSide.cs içinde gidin:  
  
   ```  
   public class DebuggerSide  
   ```  
  
2. Kodla değiştirin:  
  
   ```  
   public class DebuggerSide : DialogDebuggerVisualizer  
   ```  
  
   `DialogDebuggerVisualizer` soyut bir yöntemi vardır (`Show`), geçersiz kılmanız gerekir.  
  
#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>DialogDebuggerVisualizer.Show yöntemi geçersiz kılmak için  
  
- İçinde `public class DebuggerSide`, aşağıdaki **yöntemi:**  
  
  ```  
  override protected void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)  
  {  
  }  
  ```  
  
  `Show` Yöntemi gerçekten görselleştiricisi iletişim kutusu veya diğer kullanıcı arabirimi oluşturur ve hata ayıklayıcı'dan görselleştiriciye geçirildi bilgilerini görüntüler kodunu içerir. İletişim kutusu oluşturur ve bilgi görüntüleyen bir kod eklemeniz gerekir. Bu kılavuzda, bir Windows forms ileti kutusunu kullanarak bunu. İlk olarak, bir başvuru ekleyin ve `using` System.Windows.Forms bildirimi.  
  
#### <a name="to-add-systemwindowsforms"></a>System.Windows.Forms eklemek için  
  
1. İçinde **Çözüm Gezgini**, sağ **başvuruları** ve **Başvuru Ekle** kısayol menüsünde.  
  
2. İçinde **Başvuru Ekle** iletişim kutusundaki **.NET** sekmesinde, System.Windows.Forms.DLL seçin.  
  
3. **Tamam**'ı tıklatın.  
  
4. Aşağıdaki deyime DebuggerSide.cs içinde ekleyin `using` ifadeleri:  
  
   ```  
   using System.Windows.Forms;  
   ```  
  
   Şimdi, oluşturma ve kullanıcı arabirimi için Görselleştirici göstermek için bazı kod ekleyeceksiniz. Bu, ilk Görselleştirici olduğundan, biz kullanıcı arabirimi basit tutmak ve bir ileti kutusunu kullanın.  
  
#### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>İletişim kutusunda görselleştiricisi çıkışının görüntülenmesi için  
  
1. İçinde `Show` yöntemini aşağıdaki kod satırını ekleyin:  
  
   ```  
   MessageBox.Show(objectProvider.GetObject().ToString());  
   ```  
  
    Bu kod örneği, hata işleme içermez. Hata gerçek Görselleştirici veya başka tür bir uygulama işleme içermesi gerekir.  
  
2. Üzerinde **derleme** menüsünde seçin **derleme MyFirstVisualizer**. Proje başarıyla oluşturması gerekir. Devam etmeden önce derleme hataları düzeltin.  
  
   Hata ayıklayıcı çalışan kod sonu olmasıdır. Ancak bir adım daha yoktur; hata ayıklanan yan hangi sınıfları koleksiyonu belirten özniteliği Görselleştirici oluşur.  
  
#### <a name="to-add-the-debuggee-side-code"></a>Hata ayıklanan tarafın kod eklemek için  
  
1. DebuggerSide.cs için aşağıdaki kodu özniteliği ekleyin `using` deyimleri önce `namespace MyFirstVisualizer`:  
  
   ```  
   [assembly:System.Diagnostics.DebuggerVisualizer(  
   typeof(MyFirstVisualizer.DebuggerSide),  
   typeof(VisualizerObjectSource),  
   Target  = typeof(System.String),  
   Description  = "My First Visualizer")]  
   ```  
  
2. Üzerinde **derleme** menüsünde seçin **derleme MyFirstVisualizer**. Proje başarıyla oluşturması gerekir. Devam etmeden önce derleme hataları düzeltin.  
  
   Bu noktada, ilk Görselleştirici tamamlandı. Doğru adımları izlediyseniz, görselleştiricisi oluşturun ve içine yüklemek [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Görselleştirici içine yüklemeden önce [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ancak doğru şekilde çalıştığından emin olmak için sınamalısınız. Görselleştirici içine yüklemeden çalıştırmak için test bandı şimdi oluşturacak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
#### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Görselleştirici göstermek için bir Test yöntemi eklemek için  
  
1. Sınıfına aşağıdaki yöntemi ekleyin `public DebuggerSide`:  
  
   ```  
   public static void TestShowVisualizer(object objectToVisualize)  
   {  
      VisualizerDevelopmentHost visualizerHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));  
      visualizerHost.ShowVisualizer();  
   }  
   ```  
  
2. Üzerinde **derleme** menüsünde seçin **derleme MyFirstVisualizer**. Proje başarıyla oluşturması gerekir. Devam etmeden önce derleme hataları düzeltin.  
  
   Ardından, DLL, Görselleştirici çağırmak için bir yürütülebilir proje oluşturmanız gerekir. Kolaylık olması için bir konsol uygulama projesini kullanacağız.  
  
#### <a name="to-add-a-console-application-project-to-the-solution"></a>Bir konsol uygulaması projesi çözüme eklemek için  
  
1. Üzerinde **dosya** menüsünde seçin **Ekle** ve ardından **yeni proje**.  
  
2. İçinde **Yeni Proje Ekle** iletişim kutusundaki **şablonları** kutusunda **konsol uygulaması**.  
  
3. İçinde **adı** gibi konsol uygulaması için anlamlı bir ad yazın `MyTestConsole`.  
  
4. **Tamam**'ı tıklatın.  
  
   Artık gerekli MyTestConsole MyFirstVisualizer çağırabilmek başvuran eklemeniz gerekir.  
  
#### <a name="to-add-necessary-references-to-mytestconsole"></a>MyTestConsole gerekli başvuruları eklemek için  
  
1. İçinde **Çözüm Gezgini**, sağ **MyTestConsole** ve **Başvuru Ekle** kısayol menüsünde.  
  
2. İçinde **Başvuru Ekle** iletişim kutusu, **.NET** sekmesinde, Microsoft.VisualStudio.DebuggerVisualizers.DLL seçin.  
  
3. **Tamam**'ı tıklatın.  
  
4. Sağ **MyTestConsole** ve **Başvuru Ekle** yeniden.  
  
5. İçinde **Başvuru Ekle** iletişim kutusu, tıklayın **projeleri** sekmesine ve ardından MyFirstVisualizer tıklayın.  
  
6. **Tamam**'ı tıklatın.  
  
   Şimdi, test bandı tamamlamak için kod ekleyeceksiniz.  
  
#### <a name="to-add-code-to-mytestconsole"></a>Kod için MyTestConsole eklemek için  
  
1. İçinde **Çözüm Gezgini**, Program.cs sağ tıklatın ve seçin **Yeniden Adlandır** kısayol menüsünde.  
  
2. Program.cs adından TestConsole.cs gibi daha anlamlı olacak şekilde düzenleyin.  
  
    **Not** [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sınıf bildirimi içinde TestConsole.cs yeni dosya adı ile eşleşecek şekilde otomatik olarak değiştirir.  
  
3. TestConsole.cs içinde aşağıdaki kodu ekleyin `using` ifadeleri:  
  
   ```  
   using MyFirstVisualizer;  
   ```  
  
4. Yönteminde `Main`, aşağıdaki kodu ekleyin:  
  
   ```  
   String myString = "Hello, World";  
   DebuggerSide.TestShowVisualizer(myString);  
   ```  
  
   Şimdi, ilk görselleştiriciyi sınamak hazır olursunuz.  
  
#### <a name="to-test-the-visualizer"></a>Görselleştiriciyi sınamak için  
  
1. İçinde **Çözüm Gezgini**, sağ **MyTestConsole** ve **başlangıç projesi olarak ayarla** kısayol menüsünde.  
  
2. Üzerinde **hata ayıklama** menüsünde seçin **Başlat**.  
  
    Konsol uygulaması başlatır ve Görselleştirici görünür ve "Hello, World" dizesini görüntüler  
  
   Tebrikler. Yalnızca yerleşik ve test, ilk Görselleştirici.  
  
   Görselleştiricisindeki kullanmak istiyorsanız [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yüklemek zorunda yalnızca, test bandı çağırmak yerine,. Daha fazla bilgi için [nasıl yapılır: Görselleştiriciyi yükleme](../debugger/how-to-install-a-visualizer.md).  
  
## <a name="using-the-visualizer-item-template"></a>Görselleştirici öğe şablonu kullanma  
 Şu ana kadar bu izlenecek yolda Görselleştirici el ile oluşturmak nasıl göstermiştir. Bu öğrenme alıştırma olarak yapıldı. Artık basit Görselleştirici nasıl çalıştığını öğrendiğinize göre oluşturmak için daha kolay bir yolu yoktur: Görselleştirici öğe şablonu kullanarak.  
  
 İlk olarak, yeni bir sınıf kitaplığı projesi oluşturmanız gerekir.  
  
#### <a name="to-create-a-new-class-library"></a>Yeni bir sınıf kitaplığı oluşturmak için  
  
1. Üzerinde **dosya** menüsünde seçin **Ekle** ve ardından **yeni proje**.  
  
2. İçinde **Yeni Proje Ekle** iletişim kutusunun **proje türü**s, select **Visual C#**.  
  
3. İçinde **şablonları** kutusunda **sınıf kitaplığı**.  
  
4. İçinde **adı** MySecondVisualizer gibi bir sınıf kitaplığı için uygun bir ad yazın.  
  
5. **Tamam**'ı tıklatın.  
  
   Şimdi, kendisine görselleştiricisi öğe ekleyebilirsiniz:  
  
#### <a name="to-add-a-visualizer-item"></a>Görselleştirici öğe eklemek için  
  
1. İçinde **Çözüm Gezgini**, MySecondVisualizer sağ tıklayın.  
  
2. Kısayol menüsünde **Ekle** ve ardından **yeni öğe**.  
  
3. İçinde **Yeni Öğe Ekle** iletişim kutusunun **şablonları**, **Visual Studio yüklenmiş şablonlar**seçin **hata ayıklama görselleştiricisi**.  
  
4. İçinde **adı** SecondVisualizer.cs gibi uygun bir ad yazın.  
  
5. **Ekle**'yi tıklatın.  
  
   Tüm İşte bu kadar kolay olmasıdır. Dosyaya SecondVisualizer.cs bakması ve şablon sizin için eklenen kodu görüntüleyin. Devam edin ve kodla denemeler yapın. Temel bilgileri artık bildiğinize göre olsun daha karmaşık ve kullanışlı görselleştiriciler kendi oluşturma.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görselleştirici mimarisi](../debugger/visualizer-architecture.md)   
 [Nasıl yapılır: Görselleştiriciyi yükleme](../debugger/how-to-install-a-visualizer.md)   
 [Özel Görselleştirici Oluşturma](../debugger/create-custom-visualizers-of-data.md)



