---
title: 'Nasıl yapılır: kodu bir görselde VBA kullanımına sunma C# proje'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual C# [Office development in Visual Studio], exposing code to VBA
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- exposing code to VBA
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f00f668c3eac9a39251d0a4e19f98ed597c373db
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49873493"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-c-project"></a>Nasıl yapılır: kodu bir görselde VBA kullanımına sunma C# proje
  Bir görseldeki kodunu getirebilir C# iki birbiriyle etkileşim kurmak için kod istiyorsanız, Visual Basic Applications (VBA) kodu için proje.  
  
 Görsel C# işlem Visual Basic işleminden farklıdır. Daha fazla bilgi için [nasıl yapılır: Visual Basic projesinde kodu VBA kullanımına sunma](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="expose-code-in-a-visual-c-project"></a>Bir görselde bir kodu ortaya C# proje  
 Bir görselde kodu çağırmak VBA kodunu etkinleştirmek için C# proje kodu COM görünür olacak şekilde değiştirin ve ardından **ReferenceAssemblyFromVbaProject** özelliğini **True** Tasarımcısı'nda.  
  
 Bir görselde bir yöntem çağrısı yapmayı gösteren bir anlatım için C# projesine VBA'dan [izlenecek yol: Visual c VBA'dan Kod Çağırma&#35; proje](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).  
  
### <a name="to-expose-code-in-a-visual-c-project-to-vba"></a>Kod bir görselde göstermek için C# VBA projesi  
  
1. Word belgesi, Excel çalışma kitabı veya makroları destekleyen ve VBA kodu zaten içeren Excel şablon tabanlı bir belge düzeyi projesi oluşturun veya açın.  
  
    Makrolar destekleyen belge dosya biçimleri hakkında daha fazla bilgi için bkz. [birleştirmek VBA ve belge düzeyi özelleştirmeleri](../vsto/combining-vba-and-document-level-customizations.md).  
  
   > [!NOTE]  
   >  Bu özellik Word şablonu projelerinde kullanılamaz.  
  
2. Belgedeki VBA kodu kullanıcı makroları istemeden çalışmaya izin verildiğinden emin olun. Office proje konumunu Word veya Excel için Güven Merkezi ayarlarında güvenilen konumlar listesine ekleyerek çalıştırılacak VBA kodu güvenebilir.  
  
3. Projenizdeki bir genel sınıf VBA için kullanıma sunmak istediğiniz üye eklemek ve yeni üye olarak bildirmek **genel**.  
  
4. Aşağıdaki uygulama <xref:System.Runtime.InteropServices.ComVisibleAttribute> ve <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> öznitelikleri için VBA bırakıyorsunuz sınıf. Bu öznitelikler sınıfı görebilmesi com ancak bir sınıf arabirimi oluşturuluyor.  
  
   ```csharp  
   [System.Runtime.InteropServices.ComVisible(true)]  
   [System.Runtime.InteropServices.ClassInterface(  
       System.Runtime.InteropServices.ClassInterfaceType.None)]  
   ```  
  
5. Geçersiz kılma **GetAutomationObject** gösterme sınıfının bir örneğini dönmek için projenizdeki ana bilgisayar öğesi sınıfının yöntemi:  
  
   - Konak öğesi sınıf VBA bırakıyorsunuz, geçersiz kılma **GetAutomationObject** yönteminin bu sınıfa ait ve sınıfının geçerli örneği döndürür.  
  
     ```csharp  
     protected override object GetAutomationObject()  
     {  
         return this;  
     }  
     ```  
  
   - Bir konak öğesi olmayan bir sınıf bırakıyorsunuz, geçersiz kılma **GetAutomationObject** yöntemi herhangi bir konak öğesi projenizde ve konak öğesi olmayan sınıfının bir örneğini döndürür. Örneğin, aşağıdaki kod adında bir sınıf gösterme varsayar `DocumentUtilities` VBA.  
  
     ```csharp  
     protected override object GetAutomationObject()  
     {  
         return new DocumentUtilities();  
     }  
     ```  
  
     Konak öğeleri hakkında daha fazla bilgi için bkz. [konak öğelerini ve denetimlerine genel bakış için ana bilgisayar](../vsto/host-items-and-host-controls-overview.md).  
  
6. Bir arabirim için VBA bırakıyorsunuz sınıfı Al. İçinde **Arabirimi Ayıkla** iletişim kutusunda, arabirimin bildiriminde dahil etmek istediğiniz genel üyeleri seçin. Daha fazla bilgi için [ayıklama arabirimi yeniden düzenleme](../ide/reference/extract-interface.md).
  
7. Ekleme **genel** arabirim bildirimi için anahtar sözcüğü.  
  
8. Aşağıdakileri ekleyerek arabirime COM görünür yapmak <xref:System.Runtime.InteropServices.ComVisibleAttribute> özniteliği için arabirim.  
  
   ```csharp  
   [System.Runtime.InteropServices.ComVisible(true)]  
   ```  
  
9. Çalışma sayfası (Excel) ve belge (Word) tasarımcıda açmak [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
10. İçinde **özellikleri** penceresinde **ReferenceAssemblyFromVbaProject** özellik ve değere değiştirin **True**.  
  
    > [!NOTE]  
    >  Çalışma kitabı veya belge VBA kodu zaten içermiyor veya belgedeki VBA kodu çalıştırmak için güvenilir değilse, ayarlarken bir hata iletisi alırsınız **ReferenceAssemblyFromVbaProject** özelliğini **True**. Bu durum, Visual Studio, bu durumda belgedeki VBA projesine değiştirilemiyor çünkü.  
  
11. Tıklayın **Tamam** iletisinde görüntülenir. Bu ileti eklerseniz VBA kodunu çalışma kitabına veya belge projeden çalıştırırken gerektiğini hatırlatır [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], projeyi sonraki açışınızda VBA kodu kaybolacak. Klasör projeyi her seferinde üzerine yazılır yapı içinde belge çıkış olmasıdır.  
  
     Bu noktada, Visual Studio Proje bütünleştirilmiş kod içine VBA projesi çağırabilirsiniz şekilde yapılandırır. Visual Studio adlı bir yöntemi de ekler `GetManagedClass` VBA projesine. Bu yöntem her yerden çağırabilirsiniz VBA için kullanıma sunulan sınıfa erişme olanağına VBA projesi.  
  
12. Projeyi oluşturun.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: Visual Studio'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Office çözümleri oluşturma ve tasarlama](../vsto/designing-and-creating-office-solutions.md)   
 [VBA ve belge düzeyi özelleştirmelerini birleştirme](../vsto/combining-vba-and-document-level-customizations.md)   
 [İzlenecek yol: Visual c VBA'dan Kod Çağırma&#35; proje](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)   
 [Nasıl yapılır: Visual Basic projesinde kodu VBA kullanımına sunma](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)  
  
  