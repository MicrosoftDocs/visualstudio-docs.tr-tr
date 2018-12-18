---
title: 'Nasıl yapılır: Visual Basic projesinde kodu VBA kullanımına sunma'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- Visual Basic [Office development in Visual Studio], exposing code to VBA
- exposing code to VBA
- host items [Office development in Visual Studio], exposing code to VBA
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7e4bc9f4227c11f8e34838a2785b27da62a0a6b8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49839654"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-basic-project"></a>Nasıl yapılır: Visual Basic projesinde kodu VBA kullanımına sunma
  Kodda getirebilir bir [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] iki birbiriyle etkileşim kurmak için kod istiyorsanız, Visual Basic Applications (VBA) kodu için proje.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Visual Basic işlemidir görsel farklı C# işlem. Daha fazla bilgi için [nasıl yapılır: kodu Visual c VBA kullanımına sunma&#35; proje](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md).  
  
 Kodda diğer sınıflar için farklı bir ana bilgisayar öğesi sınıf kodunu işlemdir:  
  
- [Bir ana bilgisayar öğesi sınıftaki kod kullanıma sunma](#HostItemCode)  
  
- [Bir konak öğesi sınıfında yer almayan bir kodu ortaya](#NonHostItem)  
  
  ![video bağlantısı](../vsto/media/playvideo.gif "video bağlantı") ilgili video gösterimi için bkz. [nasıl ı: çağrı VSTO kod VBA'dan?](http://go.microsoft.com/fwlink/?LinkId=136757).  
  
##  <a name="HostItemCode"></a> Bir ana bilgisayar öğesi sınıftaki kod kullanıma sunma  
 Visual Basic kodunu konak öğesi sınıfının içinde çağırmak VBA kodu etkinleştirmek için **EnableVbaCallers** konak öğesi özelliği **True**.  
  
 Ana bilgisayar öğesi sınıfının bir yöntemi kullanıma sunar ve sonra VBA içinden çağrısı yapmayı gösteren bir kılavuz için bkz. [izlenecek yol: çağrı kodu VBA içinden bir Visual Basic projesinde](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md). Konak öğeleri hakkında daha fazla bilgi için bkz. [konak öğelerini ve denetimlerine genel bakış için ana bilgisayar](../vsto/host-items-and-host-controls-overview.md).  
  
#### <a name="to-expose-code-in-a-host-item-to-vba"></a>Bir konak öğesi VBA kodu göstermek için  
  
1.  Belge düzeyi oluşturun veya açın [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] bir Word belgesi, Excel çalışma kitabı veya makroları destekleyen ve VBA kodu zaten içeren Excel şablon tabanlı bir proje.  
  
     Makrolar destekleyen belge dosya biçimleri hakkında daha fazla bilgi için bkz. [birleştirmek VBA ve belge düzeyi özelleştirmeleri](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Bu özellik Word şablonu projelerinde kullanılamaz.  
  
2.  Belgedeki VBA kodu kullanıcı makroları istemeden çalışmaya izin verildiğinden emin olun. Office proje konumunu Word veya Excel için Güven Merkezi ayarlarında güvenilen konumlar listesine ekleyerek çalıştırılacak VBA kodu güvenebilir.  
  
3.  Özelliği, yöntemi veya projenizdeki ana bilgisayar öğesi sınıflarının biri VBA kullanıma sunmak istediğiniz olayı ekleyin ve yeni üye olarak bildirmek **genel**. Sınıfın adı, uygulamaya bağlıdır:  
  
    -   Proje konak öğesi sınıfı bir sözcükteki adlı `ThisDocument` varsayılan olarak.  
  
    -   Bir Excel projesinde ana bilgisayar öğesi sınıflar adlandırılan `ThisWorkbook`, `Sheet1`, `Sheet2`, ve `Sheet3` varsayılan olarak.  
  
4.  Ayarlama **EnableVbaCallers** konak öğesi özelliği **True**. Bu özellik kullanılabilir **özellikleri** konak öğesi tasarımcıda açtığınızda penceresi.  
  
     Bu özellik ayarlandıktan sonra Visual Studio otomatik olarak ayarlar **ReferenceAssemblyFromVbaProject** özelliğini **True**.  
  
    > [!NOTE]  
    >  Çalışma kitabı veya belge VBA kodu zaten içermiyor veya belgedeki VBA kodu çalıştırmak için güvenilir değilse, ayarlarken bir hata iletisi alırsınız **EnableVbaCallers** özelliğini **True**. Bu durum, Visual Studio, bu durumda belgedeki VBA projesine değiştirilemiyor çünkü.  
  
5.  Tıklayın **Tamam** iletisinde görüntülenir. Bu ileti, çalışma kitabı veya belgeye eklediğiniz VBA kodu projeden çalıştığını hatırlatır [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], proje oluşturduğunuzda başlatıldığında VBA kodu kaybolacak. Projeyi her derlediğinizde derleme çıktısı klasörü belgede yazılır olmasıdır.  
  
     Bu noktada, Visual Studio Proje bütünleştirilmiş kod içine VBA projesi çağırabilirsiniz şekilde yapılandırır. Visual Studio ayrıca adlı bir özellik ekler `CallVSTOAssembly` için `ThisDocument`, `ThisWorkbook`, `Sheet1`, `Sheet2`, veya `Sheet3` VBA projesinde modülü. Genel üyelerinin VBA için kullanıma sunulan sınıfı erişmek için bu özelliği kullanabilirsiniz.  
  
6.  Projeyi oluşturun.  
  
##  <a name="NonHostItem"></a> Bir konak öğesi sınıfında yer almayan bir kodu ortaya  
 Bir konak öğesi sınıfında yer almayan Visual Basic kodu çağırmak VBA kodu etkinleştirmek için kodu VBA için görünür olacak şekilde değiştirin.  
  
### <a name="to-expose-code-that-is-not-in-a-host-item-class-to-vba"></a>Ana bilgisayar öğesi sınıf VBA olmayan kodu göstermek için  
  
1.  Belge düzeyi oluşturun veya açın [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] bir Word belgesi, Excel çalışma kitabı veya makroları destekleyen ve VBA kodu zaten içeren Excel şablon tabanlı bir proje.  
  
     Makrolar destekleyen belge dosya biçimleri hakkında daha fazla bilgi için bkz. [birleştirmek VBA ve belge düzeyi özelleştirmeleri](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Bu özellik Word şablonu projelerinde kullanılamaz.  
  
2.  Belgedeki VBA kodu kullanıcı makroları istemeden çalışmaya izin verildiğinden emin olun. Office proje konumunu Word veya Excel için Güven Merkezi ayarlarında güvenilen konumlar listesine ekleyerek çalıştırılacak VBA kodu güvenebilir.  
  
3.  Projenizdeki bir genel sınıf VBA için kullanıma sunmak istediğiniz üye eklemek ve yeni üye olarak bildirmek **genel**.  
  
4.  Aşağıdaki uygulama <xref:System.Runtime.InteropServices.ComVisibleAttribute> ve <xref:Microsoft.VisualBasic.ComClassAttribute> öznitelikleri için VBA bırakıyorsunuz sınıf. Bu öznitelikler sınıf VBA görünür yapın.  
  
    ```vb  
    <Microsoft.VisualBasic.ComClass()> _  
    <System.Runtime.InteropServices.ComVisibleAttribute(True)> _  
    ```  
  
5.  Geçersiz kılma **GetAutomationObject** gösterme sınıfının bir örneğini dönmek için projenizdeki ana bilgisayar öğesi sınıfının yöntemi. Aşağıdaki kod örneğinde adlı bir sınıf gösterme varsayar `DocumentUtilities` VBA.  
  
    ```vb  
    Protected Overrides Function GetAutomationObject() As Object  
        Return New DocumentUtilities()  
    End Function  
    ```  
  
6.  Belge (Word) veya çalışma sayfası (Excel) Tasarımcısı'nda açın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
7.  İçinde **özellikleri** penceresinde **ReferenceAssemblyFromVbaProject** özellik ve değere değiştirin **True**.  
  
    > [!NOTE]  
    >  Çalışma kitabı veya belge VBA kodu zaten içermiyor veya belgedeki VBA kodu çalıştırmak için güvenilir değilse, ayarlarken bir hata iletisi alırsınız **ReferenceAssemblyFromVbaProject** özelliğini **True** . Bu durum, Visual Studio, bu durumda belgedeki VBA projesine değiştirilemiyor çünkü.  
  
8.  Tıklayın **Tamam** iletisinde görüntülenir. Bu ileti, çalışma kitabı veya belgeye eklediğiniz VBA kodu projeden çalıştığını hatırlatır [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], proje oluşturduğunuzda başlatıldığında VBA kodu kaybolacak. Projeyi her derlediğinizde derleme çıktısı klasörü belgede yazılır olmasıdır.  
  
     Bu noktada, Visual Studio Proje bütünleştirilmiş kod içine VBA projesi çağırabilirsiniz şekilde yapılandırır. Visual Studio adlı bir yöntemi de ekler `GetManagedClass` VBA projesine. Bu yöntem her yerden çağırabilirsiniz VBA için kullanıma sunulan sınıfa erişme olanağına VBA projesi.  
  
9. Projeyi oluşturun.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: Visual Studio'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Office çözümleri oluşturma ve tasarlama](../vsto/designing-and-creating-office-solutions.md)   
 [VBA ve belge düzeyi özelleştirmelerini birleştirme](../vsto/combining-vba-and-document-level-customizations.md)   
 [İzlenecek yol: kod Visual Basic projesinde VBA'dan çağırın](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)   
 [Nasıl yapılır: kodu Visual c VBA kullanımına sunma&#35; proje](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)  
  
  