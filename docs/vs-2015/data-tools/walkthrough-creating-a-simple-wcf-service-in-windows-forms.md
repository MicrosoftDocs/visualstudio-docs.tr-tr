---
title: "İzlenecek yol: Windows Forms'ta basit bir WCF hizmeti oluşturma | Microsoft Docs"
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF, walkthrough [Visual Studio]
- WCF, Visual Studio tools for
- WCF services
- WCF services, walkthrough
ms.assetid: 5fef1a64-27a4-4f10-aa57-29023e28a2d6
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6e73659c2d28cf97a8a7136ed8232cfbc5f0b77c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49247214"
---
# <a name="walkthrough-creating-a-simple-wcf-service-in-windows-forms"></a>İzlenecek yol: Windows Forms'ta basit bir WCF hizmeti oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Bu izlenecek yol basit bir oluşturma işlemini gösterir [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] hizmet, test etmesine ve sonra bir Windows Forms uygulamasından erişebilirsiniz.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="creating-the-service"></a>Hizmeti Oluşturma  
  
#### <a name="to-create-a-wcf-service"></a>Bir WCF hizmeti oluşturmak için  
  
1.  Üzerinde **dosya** menüsünde **yeni** ve ardından **proje**.  
  
2.  İçinde **yeni proje** iletişim kutusunda **Visual Basic** veya **Visual C#** düğüm ve tıklatın **WCF**çizgidir **WCF Hizmet Kitaplığı**. Tıklayın **Tamam** projeyi açmak için.  
  
     ![WCF hizmet kitaplığı projesi](../data-tools/media/wcf1.PNG "wcf1")  
  
    > [!NOTE]
    >  Bu, test ve erişilen bir çalışma hizmet oluşturur. Aşağıdaki iki adımı farklı bir veri türü kullanılacak varsayılan yöntemini nasıl değişiklik yapabileceğiniz gösterir. Gerçek bir uygulamada hizmete kendi işlevlerinizi eklersiniz.  
  
3.  ![Iservice1 dosya](../data-tools/media/wcf2.png "wcf2")  
  
     İçinde **Çözüm Gezgini**Iservice1.vb veya Iservice1.cs öğesine çift tıklayın ve şu satırı bulun:  
  
     [! kod-csharp [WCFWalkthrough #4] (.. /snippets/CSharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1 (2).cs #4)] [! kod-vb [WCFWalkthrough #4] (.. /snippets/VisualBasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1 (2).vb #4)]  
  
     Değişiklik türü için `value` parametresi `String`:  
  
     [!code-csharp[WCFWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#1)]
     [!code-vb[WCFWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#1)]  
  
     Yukarıdaki kodda Not `<OperationContract()>` veya `[OperationContract]` öznitelikleri. Bu öznitelik hizmet tarafından sunulan herhangi bir yöntem için gerekli değildir.  
  
4.  ![Service1 dosya](../data-tools/media/wcf3.png "wcf3")  
  
     İçinde **Çözüm Gezgini**gt;service1.vb veya Service1.cs çift tıklayın ve şu satırı bulun:  
  
     [! kod-csharp [WCFWalkthrough 5] (.. /snippets/CSharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/Service1 (2).cs 5)] [! kod-vb [WCFWalkthrough 5] (.. /snippets/VisualBasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/Service1 (2).vb 5)]  
  
     Değer parametresi türünü değiştir `String`:  
  
     [!code-csharp[WCFWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/service1.cs#2)]
     [!code-vb[WCFWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/service1.vb#2)]  
  
## <a name="testing-the-service"></a>Hizmeti test etme  
  
#### <a name="to-test-a-wcf-service"></a>Bir WCF hizmeti test etmek için  
  
1.  Tuşuna **F5** hizmeti çalıştırmak için. A **WCF Test istemcisi** form görüntülenir ve hizmete yüklenir.  
  
2.  İçinde **WCF Test istemcisi** formunda, çift **GetData()** altındaki yöntemin **Iservice1**. **GetData** sekmesi görüntülenir.  
  
     ![GetData&#40; &#41; yöntemi](../data-tools/media/wcf4.png "wcf4")  
  
3.  İçinde **istek** kutusunda **değer** alan ve tür `Hello`.  
  
     ![Değer alanı](../data-tools/media/wcf5.png "wcf5")  
  
4.  Tıklayın **Invoke** düğmesi. Varsa bir **Güvenlik Uyarısı** iletişim kutusu görüntülenir, tıklayın **Tamam**. Sonuç görüntülenecek **yanıt** kutusu.  
  
     ![Sonucu yanıt kutusundaki](../data-tools/media/wcf6.png "wcf6")  
  
5.  Üzerinde **dosya** menüsünde tıklatın **çıkış** test formu kapatmak için.  
  
## <a name="accessing-the-service"></a>Hizmete erişim  
  
#### <a name="to-reference-a-wcf-service"></a>Bir WCF Hizmeti başvurmak için  
  
1.  Üzerinde **dosya** menüsünde **Ekle** ve ardından **yeni proje**.  
  
2.  İçinde **yeni proje** iletişim kutusunda **Visual Basic** veya **Visual C#** düğümünü seçip alt **Windows**seçip **Windows Forms uygulamalarındaki**. Tıklayın **Tamam** projeyi açmak için.  
  
     ![Windows Forms uygulaması projesi](../data-tools/media/wcf7.png "wcf7")  
  
3.  Sağ **WindowsApplication1** tıklatıp **hizmet Başvurusu Ekle**. **Hizmet Başvurusu Ekle** iletişim kutusu görüntülenir.  
  
4.  İçinde **hizmet Başvurusu Ekle** iletişim kutusu, tıklayın **bulma**.  
  
     ![Hizmet Başvurusu Ekle iletişim kutusu](../data-tools/media/wcf8.png "wcf8")  
  
     **Service1** görüntülenmesi **Hizmetleri** bölmesi.  
  
5.  Tıklayın **Tamam** hizmet başvurusu eklemek için.  
  
#### <a name="to-build-a-client-application"></a>Bir istemci uygulaması oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, çift **Form1.vb** veya **Form1.cs** Windows Form Tasarımcısı zaten açık değilse açın.  
  
2.  Gelen **araç kutusu**, sürükleyin bir `TextBox` denetimi, bir `Label` denetimi ve bir `Button` forma denetim.  
  
     ![Formu için denetimler ekleme](../data-tools/media/wcf9.png "wcf9")  
  
3.  Çift `Button`ve aşağıdaki kodu ekleyin `Click` olay işleyicisi:  
  
     [!code-csharp[WCFWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/form1.cs#3)]
     [!code-vb[WCFWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/form1.vb#3)]  
  
4.  İçinde **Çözüm Gezgini**, sağ **WindowsApplication1** tıklatıp **başlangıç projesi olarak ayarla**.  
  
5.  Tuşuna **F5** projeyi çalıştırın. Bir metin girin ve düğmeye tıklayın. Etiket görüntüler "girdiniz:" ve girdiğiniz metni.  
  
     ![Formun sonucu gösteriliyor](../data-tools/media/wcf10.png "wcf10")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio'da Windows Communication Foundation Hizmetleri ve WCF Veri Hizmetleri](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

