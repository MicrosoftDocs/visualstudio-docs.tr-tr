---
title: "İzlenecek yol: Visual Basic'de Görselleştirici yazma | Microsoft Docs"
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
ms.assetid: c93bf5a1-3e5e-422f-894e-bd72c9bc1b57
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 549e1ce240808a3947b2780f5c96485439e44ecc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51794907"
---
# <a name="walkthrough-writing-a-visualizer-in-visual-basic"></a>İzlenecek Yol: Visual Basic'de Görselleştirici Yazma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu kılavuz kullanılarak basit Görselleştirici yazma işlemi gösterilmektedir [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]. Bu izlenecek yolda oluşturacağınız Görselleştirici, bir Windows Forms ileti kutusunu kullanarak bir dizenin içeriklerini görüntüler. Bu basit dize Görselleştirici nasıl görselleştiriciler diğer veri türleri için daha uygun projelerinize oluşturacağınızı göstermek için basit bir örnektir.  
  
> [!NOTE]
>  İletişim kutuları ve menü komutları gördüğünüz açıklanana Yardım'da, etkin ayarlarınıza ve sürüm bağlı olarak farklı olabilir. Ayarlarınızı değiştirmek için Git **Araçları** menüsünü seçip **içeri ve dışarı aktarma** . Daha fazla bilgi için [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Görselleştirici kod, hata ayıklayıcı tarafından okunacak DLL'de yerleştirilmelidir. İlk adım, DLL için bir sınıf kitaplığı projesi oluşturmaktır.  
  
## <a name="create-and-prepare-a-class-library-project"></a>Oluşturma ve bir sınıf kitaplığı projesi hazırlama  
  
#### <a name="to-create-a-class-library-project"></a>Bir sınıf kitaplığı projesi oluşturmak için  
  
1. Üzerinde **dosya** menüsünde seçin **yeni** tıklatıp **yeni proje**.  
  
2. İçinde **yeni proje** iletişim kutusunun **proje türü**s, tıklayın **Visual Basic**.  
  
3. İçinde **şablonları** kutusunun **sınıf kitaplığı**.  
  
4. İçinde **adı** gibi sınıf kitaplığı için uygun bir ad yazın **MyFirstVisualizer**.  
  
5. **Tamam**'ı tıklatın.  
  
   Sınıf kitaplığı oluşturduktan sonra tanımlanan sınıflara var. kullanabilmesi için Microsoft.VisualStudio.DebuggerVisualizers.DLL, bir başvuru eklemeniz gerekir. İlk olarak, ancak, projenize anlamlı bir ad verin.  
  
#### <a name="to-rename-class1vb-and-add-microsoftvisualstudiodebuggervisualizers"></a>Class1.vb yeniden adlandırıp Microsoft.VisualStudio.DebuggerVisualizers Ekle  
  
1.  İçinde **Çözüm Gezgini**, sağ **Class1.vb**ve kısayol menüsünde **Yeniden Adlandır**.  
  
2.  Ad Class1.vb DebuggerSide.vb gibi anlamlı değiştirin.  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sınıf bildirimi içinde DebuggerSide.vb yeni dosya adı ile eşleşecek şekilde otomatik olarak değiştirir.  
  
3.  İçinde **Çözüm Gezgini**, sağ **My ilk Görselleştirici**ve kısayol menüsünde **Başvuru Ekle**.  
  
4.  İçinde **Başvuru Ekle** iletişim kutusundaki **.NET** sekmesinde, Microsoft.VisualStudio.DebuggerVisualizers.DLL tıklayın.  
  
5.  **Tamam**'ı tıklatın.  
  
6.  Aşağıdaki deyime DebuggerSide.vb içinde ekleyin `Imports` ifadeleri:  
  
    ```  
    Imports Microsoft.VisualStudio.DebuggerVisualizers  
    ```  
  
## <a name="add-the-debugger-side-code"></a>Hata ayıklayıcı tarafı kodu ekleyin  
 Artık, hata ayıklayıcı tarafından çalışan kod oluşturmaya hazırsınız. Görselleştirmek istediğiniz bilgileri görüntülemek için hata ayıklayıcısı içinde çalıştırılan kod budur. İlk olarak, bildirimini değiştirmek zorunda `DebuggerSide` taban sınıfından devralan nesnesini `DialogDebuggerVisualizer`.  
  
#### <a name="to-inherit-from-dialogdebuggervisualizer"></a>DialogDebuggerVisualizer devralacak şekilde  
  
1. Aşağıdaki kod satırını DebuggerSide.vb içinde gidin:  
  
   ```  
   Public Class DebuggerSide  
   ```  
  
2. Kod şuna benzer şekilde düzenleyin:  
  
   ```  
   Public Class DebuggerSide  
   Inherits DialogDebuggerVisualizer  
   ```  
  
   `DialogDebuggerVisualizer` soyut bir yöntemi, `Show`, geçersiz kılmanız gerekir.  
  
#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>DialogDebuggerVisualizer.Show yöntemi geçersiz kılmak için  
  
- İçinde `public class DebuggerSide`, aşağıdaki yöntemi ekleyin:  
  
  ```  
  Protected Overrides Sub Show(ByVal windowService As Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService, ByVal objectProvider As Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider)  
  
      End Sub  
  ```  
  
  `Show` Yöntemi gerçekten görselleştiricisi iletişim kutusu veya diğer kullanıcı arabirimi oluşturur ve hata ayıklayıcı'dan görselleştiriciye geçirildi bilgilerini görüntüler kodunu içerir. İletişim kutusu oluşturur ve bilgi görüntüleyen bir kod eklemeniz gerekir. Bu kılavuzda, bir Windows Forms ileti kutusunu kullanarak bunu. İlk olarak, bir başvuru ekleyin ve `Imports` bildirimi <xref:System.Windows.Forms>.  
  
#### <a name="to-add-systemwindowsforms"></a>System.Windows.Forms eklemek için  
  
1.  İçinde **Çözüm Gezgini**, sağ **başvuruları**ve kısayol menüsünde **Başvuru Ekle**.  
  
2.  İçinde **Başvuru Ekle** iletişim kutusundaki **.NET** sekmesinde **System.Windows.Forms**.  
  
3.  **Tamam**'ı tıklatın.  
  
4.  Aşağıdaki deyime DebuggerSide.cs içinde ekleyin `Imports` ifadeleri:  
  
    ```  
    Imports System.Windows.Forms  
    ```  
  
## <a name="create-your-visualizers-user-interface"></a>Visualizer'ın kullanıcı arabirimi oluşturma  
 Şimdi oluşturun ve kullanıcı arabirimi için Görselleştirici göstermek için bazı kod ekleyeceksiniz. Bu, ilk Görselleştirici olduğu için kullanıcı arabirimi basit tutmak ve bir ileti kutusunu kullanın.  
  
#### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>İletişim kutusunda görselleştiricisi çıkışının görüntülenmesi için  
  
1.  İçinde `Show` yöntemini aşağıdaki kod satırını ekleyin:  
  
    ```  
    MessageBox.Show(objectProvider.GetObject().ToString())  
    ```  
  
     Bu kod örneği, hata işleme içermez. Hata işleme gerçek Görselleştirici veya herhangi bir uygulama türünü içermelidir.  
  
2.  Üzerinde **derleme** menüsünde tıklatın **derleme MyFirstVisualizer**. Proje başarıyla oluşturması gerekir. Devam etmeden önce derleme hataları düzeltin.  
  
## <a name="add-the-necessary-attribute"></a>Gerekli öznitelik Ekle  
 Hata ayıklayıcı tarafı kodun sonuna olmasıdır. Var olan bir adım daha ancak: görselleştiriciyi hata ayıklanan yan hangi sınıfları koleksiyonu belirten özniteliği oluşur.  
  
#### <a name="to-add-the-debugee-side-code"></a>Debugee tarafı kod eklemek için  
  
1.  DebuggerSide.vb için aşağıdaki kodu özniteliği ekleyin `Imports` deyimleri önce `namespace MyFirstVisualizer`:  
  
    ```  
    <Assembly: System.Diagnostics.DebuggerVisualizer(GetType(MyFirstVisualizer.DebuggerSide), GetType(VisualizerObjectSource), Target:=GetType(System.String), Description:="My First Visualizer")>  
    ```  
  
2.  Üzerinde **derleme** menüsünde tıklatın **derleme MyFirstVisualizer**. Proje başarıyla oluşturması gerekir. Devam etmeden önce derleme hataları düzeltin.  
  
## <a name="create-a-test-harness"></a>Bir Test bandı oluşturma  
 Bu noktada, ilk Görselleştirici tamamlandı. Doğru adımları izlediyseniz, görselleştiricisi oluşturun ve içine yüklemek [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Görselleştirici içine yüklemeden önce [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ancak doğru şekilde çalıştığından emin olmak için sınamalısınız. Görselleştirici içine yüklemeden çalıştırmak için test bandı şimdi oluşturacak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
#### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Görselleştirici göstermek için bir test yöntemi eklemek için  
  
1. Sınıfına aşağıdaki yöntemi ekleyin `public DebuggerSide`:  
  
   ```  
   Shared Public Sub TestShowVisualizer(ByVal objectToVisualize As Object)  
       Dim visualizerHost As New VisualizerDevelopmentHost(objectToVisualize, GetType(DebuggerSide))  
   visualizerHost.ShowVisualizer()  
   End Sub  
   ```  
  
2. Üzerinde **derleme** menüsünde tıklatın **derleme MyFirstVisualizer**. Proje başarıyla oluşturması gerekir. Devam etmeden önce derleme hataları düzeltin.  
  
   Ardından, DLL, Görselleştirici çağırmak için bir yürütülebilir proje oluşturmanız gerekir. Kolaylık olması için bir konsol uygulama projesi kullanın.  
  
#### <a name="to-add-a-console-application-project-to-the-solution"></a>Bir konsol uygulaması projesi çözüme eklemek için  
  
1. Üzerinde **dosya** menüsünü tıklatın **Ekle**ve ardından **yeni proje**.  
  
2. İçinde **Yeni Proje Ekle** iletişim kutusundaki **şablonları** kutusunun **konsol uygulaması**.  
  
3. İçinde **adı** gibi konsol uygulaması için anlamlı bir ad yazın **MyTestConsole**.  
  
4. **Tamam**'ı tıklatın.  
  
   Artık gerekli MyTestConsole MyFirstVisualizer çağırabilmek başvuran eklemeniz gerekir.  
  
#### <a name="to-add-necessary-references-to-mytestconsole"></a>MyTestConsole gerekli başvuruları eklemek için  
  
1.  İçinde **Çözüm Gezgini**, sağ **MyTestConsole**ve kısayol menüsünde **Başvuru Ekle**.  
  
2.  İçinde **Başvuru Ekle** iletişim kutusundaki **.NET** sekmesinde, Microsoft.VisualStudio.DebuggerVisualizers tıklayın.  
  
3.  **Tamam**'ı tıklatın.  
  
4.  Sağ **MyTestConsole**ve ardından **Başvuru Ekle** yeniden.  
  
5.  İçinde **Başvuru Ekle** iletişim kutusu, tıklayın **projeleri** sekmesini ve ardından MyFirstVisualizer seçin.  
  
6.  **Tamam**'ı tıklatın.  
  
## <a name="finish-your-test-harness-and-test-your-visualizer"></a>Son Test Bandınız ve, Görselleştiriciyi test etme  
 Şimdi, test bandı tamamlamak için kod ekleyeceksiniz.  
  
#### <a name="to-add-code-to-mytestconsole"></a>Kod için MyTestConsole eklemek için  
  
1. İçinde **Çözüm Gezgini**, sağ **Program.vb**ve kısayol menüsünde **Yeniden Adlandır**.  
  
2. Uygun, Module1.vb adından gibi Düzen **TestConsole.vb**.  
  
    Dikkat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sınıf bildirimi içinde TestConsole.vb yeni dosya adı ile eşleşecek şekilde otomatik olarak değiştirir.  
  
3. TestConsole içinde. vb, aşağıdaki `Imports` deyimi:  
  
   ```  
   Imports MyFirstVisualizer  
   ```  
  
4. Yönteminde `Main`, aşağıdaki kodu ekleyin:  
  
   ```  
   Dim myString As String = "Hello, World"  
   DebuggerSide.TestShowVisualizer(myString)  
   ```  
  
   Şimdi, ilk görselleştiriciyi sınamak hazır olursunuz.  
  
#### <a name="to-test-the-visualizer"></a>Görselleştiriciyi sınamak için  
  
1. İçinde **Çözüm Gezgini**, sağ **MyTestConsole**ve kısayol menüsünde **başlangıç projesi olarak ayarla**.  
  
2. Üzerinde **hata ayıklama** menüsünde tıklatın **Başlat**.  
  
    Konsol uygulamasını başlatır. Görselleştirici görünür ve "Hello, World." dizesini görüntüler  
  
   Tebrikler. Yalnızca yerleşik ve test, ilk Görselleştirici.  
  
   Görselleştiricisindeki kullanmak istiyorsanız [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yüklemek zorunda yalnızca, test bandı çağırmak yerine,. Daha fazla bilgi için [nasıl yapılır: Görselleştiriciyi yükleme](../debugger/how-to-install-a-visualizer.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görselleştirici mimarisi](../debugger/visualizer-architecture.md)   
 [Nasıl yapılır: Görselleştiriciyi yükleme](../debugger/how-to-install-a-visualizer.md)   
 [Özel Görselleştirici Oluşturma](../debugger/create-custom-visualizers-of-data.md)



