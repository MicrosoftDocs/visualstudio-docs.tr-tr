---
title: Office çözümlerinde WPF denetimlerini kullanma
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5419a715cbe255b5cfc31a113a00e3525d63d827
ms.sourcegitcommit: 96a6d1f16d06ca28d309d05b6e9fbd52f628cdbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40008209"
---
# <a name="use-wpf-controls-in-office-solutions"></a>Office çözümlerinde WPF denetimlerini kullanma

Visual Studio'da Office geliştirme araçlarını kullanarak oluşturulan çözümleri, doğrudan Windows Forms denetimleri ile çalışmak için tasarlanmış olmasına rağmen WPF denetimleri de çözümlerinizde kullanabilirsiniz. Windows Presentation Foundation (WPF) Windows Forms'a kullanıcı arabirimleri tasarlama için alternatiftir. WPF, UI, medya ve belgeler birleştirmek için yeni teknikler sağlamak için Extensible Application Markup Language (XAML) adlı bir biçimlendirme dili kullanır. Daha fazla bilgi için [WPF genel bakış](../designers/introduction-to-wpf.md).

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

Office çözümünü Windows Forms denetimlerinde barındıran herhangi bir kullanıcı Arabirimi öğesi, WPF denetimleri de barındırabilir. Bunlar, aşağıdaki öğeleri içerir:

-   Belgeleri ve belge düzeyi özelleştirmelerdeki çalışma.

-   Belge düzeyi özelleştirmelerdeki Eylemler bölmesi.

-   VSTO eklentileri özel görev bölmeleri.

-   VSTO eklentileri için Outlook form bölgeleri.

## <a name="add-wpf-controls-to-office-projects-at-design-time"></a>WPF denetimleri Office projelerini tasarım zamanında ekleyin.

Office çözümlerinde UI öğelerine doğrudan WPF denetimleri ekleyemezsiniz. Bunun yerine ekleme bir **kullanıcı denetimi (WPF)** öğesi projenize ekleyin ve WPF denetimleri için tasarım yüzeyi olarak kullanın. Ardından, bir kullanıcı Arabirimi öğesi, projenizdeki WPF kullanıcı denetimi ekleyin.

### <a name="to-add-wpf-controls-to-an-actions-pane-custom-task-pane-or-form-region"></a>Eylemler bölmesinde, özel görev bölmesi veya form bölgesi WPF denetimleri eklemek için

1.  Özel görev bölmesi, Eylemler bölmesi ve form bölgesini eklemek istediğiniz bir projeyi açın.

2.  Ekleme bir **kullanıcı denetimi (WPF)** projenize öğesi.

3.  Gelen **araç kutusu**, WPF denetimlerinin WPF kullanıcı denetimi tasarım yüzeyine ekleyin.

     WPF kullanıcı denetimi Tasarımcısı açıkken, varsayılan olarak **araç kutusu** sadece WPF denetimleri içerir.

4.  Projeyi oluşturun.

5.  Eylemler bölmesinde, form bölgesi ya da özel görev bölmesi projenize ekleyin:

    -   Form bölgeleri için ekleme bir **Outlook Form bölgesi** projeye öğe. Daha fazla bilgi için [nasıl yapılır: bir Outlook eklenti projesine form bölgesi ekleme](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

    -   Eylemler bölmeleri için ekleme bir **Eylemler bölmesi denetimi** veya **kullanıcı denetimi** projeye öğe. Daha fazla bilgi için bkz [nasıl yapılır: Eylemler bölmesi ekleme Word belgelerine veya Excel çalışma kitapları](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md) ve [nasıl yapılır: Word belgelerine Eylemler bölmesi ekleme veya Excel çalışma kitapları](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).

    -   Özel görev bölmeleri için ekleme bir **kullanıcı denetimi** projeye öğe. Daha fazla bilgi için [nasıl yapılır: uygulamaya özel görev bölmesi ekleme](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

6.  Gelen *ProjectName* **WPF kullanıcı denetimleri** sekmesinde **araç kutusu**, Eylemler bölmesinde, form bölgesi veya özel görev bölmesi için tasarımcı WPF kullanıcı denetimi sürükleyin.

     Visual Studio otomatik olarak oluşturur bir <xref:System.Windows.Forms.Integration.ElementHost> UI öğesi üzerinde WPF kullanıcı denetimi barındıran bir nesne.

7.  Projeyi yeniden derleyin.

#### <a name="to-add-wpf-controls-to-a-document-or-worksheet-in-a-document-level-project"></a>Belge veya çalışma bir belge düzeyi projede WPF denetimleri eklemek için

1.  Word veya Excel için belge düzeyi projesi açın.

2.  Ekleme bir **kullanıcı denetimi (WPF)** projenize öğesi.

3.  Gelen **araç kutusu**, WPF denetimlerinin WPF kullanıcı denetimi tasarım yüzeyine ekleyin.

4.  Projeyi oluşturun.

5.  Ekleme bir **kullanıcı denetimi** projeye öğe (diğer bir deyişle, bir Windows Forms kullanıcı denetimi).

6.  Windows Forms kullanıcı denetimi Tasarımcısı'nı açın.

7.  Gelen *ProjectName* **WPF kullanıcı denetimleri** sekmesinde **araç kutusu**, WPF kullanıcı denetimi tasarımcıya sürükleyin.

     Visual Studio otomatik olarak oluşturur bir <xref:System.Windows.Forms.Integration.ElementHost> WPF kullanıcı denetimi Windows Forms kullanıcı denetimi barındıran bir nesne.

8.  Windows Forms kullanıcı denetimi belge veya çalışma kitabındaki programlı olarak ekleyen bir kod yazın. Daha fazla bilgi için [Office belgelerine çalışma zamanında denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).

    > [!NOTE]
    > Windows Forms kullanıcı denetimi, belge veya çalışma sayfasını tasarımcıda sürükleyemezsiniz.

9. Projeyi yeniden derleyin.

## <a name="host-wpf-controls-by-using-the-elementhost-class"></a>ElementHost sınıfı kullanarak konak WPF denetimleri

Visual Studio yardımcı Windows Forms denetimleri, Office çözümlerinde kullanın, ancak benzer özellikler WPF denetimleri için sağlamaz sağlar. Örneğin, Windows Forms denetimleri belgelere ve çalışma kitaplarına tasarım zamanında denetimlerden sürükleyerek ekleyebileceğiniz **araç kutusu**, veya yardımcı yöntemler kullanarak çalışma zamanında. Ancak, bu araçlar, WPF denetimleri için kullanılamaz.

WPF denetimlerini kullanma <xref:System.Windows.Forms.Integration.ElementHost> sınıf olarak bir Windows Forms Denetim veya form ve WPF denetimleri arasında tümleştirme katmanı. Visual Studio çözümünüze tasarım zamanında WPF denetimleri eklediğinizde otomatik olarak oluşturduğu bir <xref:System.Windows.Forms.Integration.ElementHost> nesnesi.

## <a name="wpf-resources"></a>WPF kaynakları

Daha fazla mimari hakkında bilgi ve Windows Forms denetimleri ve forms, WPF denetimleri barındırma için tasarım konuları için aşağıdaki konulara bakın:

-   [Windows Forms ve WPF birlikte çalışabilirlik giriş mimarisi](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture)

-   [Windows Forms ve WPF özelliğini eşleme](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-property-mapping)

-   [WPF ve Windows Forms birlikte çalışması](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)

-   [Windows Forms denetimleri ve eşdeğer WPF denetimleri](/dotnet/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls)

Windows Forms denetimleri ve Visual Studio formlarında tasarım zamanında WPF denetimleri ekleme hakkında daha fazla bilgi için aşağıdaki konulara bakın:

-   [İzlenecek yol: yeni bir WPF içeriği Windows formlarında tasarım zamanında oluşturma](/dotnet/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time)

-   [İzlenecek yol: Tasarım zamanında WPF içeriği Windows Forms'ta düzenleme](/dotnet/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time)

-   [İzlenecek yol: Stil WPF içeriği](/dotnet/framework/winforms/advanced/walkthrough-styling-wpf-content)

## <a name="see-also"></a>Ayrıca bkz.

- [Office kullanıcı arabirimini özelleştirme](../vsto/office-ui-customization.md)
- [Windows Forms denetimlerine Office belgeleri genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)
- [Özel görev bölmeleri](../vsto/custom-task-panes.md)
- [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)
- [Nasıl yapılır: Word belgelerine Eylemler bölmesi ekleme veya Excel çalışma kitapları](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Nasıl yapılır: uygulamaya özel görev bölmesi ekleme](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Nasıl yapılır: bir Outlook eklenti projesine form bölgesi ekleme](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
