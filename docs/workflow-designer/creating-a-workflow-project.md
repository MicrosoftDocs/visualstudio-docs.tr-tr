---
title: Workflow Foundation projesi oluşturma
ms.date: 06/25/2018
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- Workflow Designer, creating a workflow project
- creating a workflow project
ms.assetid: 235a125e-ebe7-4a98-bf77-86c8558728fb
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4a4f8ed1effbc459bd2a17e3433738c1b461513b
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755660"
---
# <a name="workflow-project-templates"></a>İş akışı proje şablonları

Visual Studio Proje şablonları kullanarak iş akışları, Windows Communication Foundation (WCF) iş akışı Hizmetleri, özel etkinlikler ve özel etkinlik tasarımcıları oluşturabilirsiniz. Bu makalede, Visual Studio Proje şablonları ile kitaplıkları ve uygulamaları oluşturmayı açıklar.

## <a name="create-a-workflow-project"></a>Bir iş akışı projesi oluşturma

Visual Studio dört farklı iş akışı proje şablonları sağlar:

- İş akışı konsol uygulaması

- WCF iş akışı hizmeti uygulaması

- Etkinlik kitaplığı

- Etkinlik Tasarımcısı kitaplığı

Bu şablonlar erişmek için ilk yükleme **Windows Workflow Foundation** Visual Studio 2017'in bileşeni. Ayrıntılı yönergeler için bkz: [Windows Workflow Foundation yüklemek](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. Yükledikten sonra **Windows Workflow Foundation** bileşeni, açık **yeni proje** seçerek iletişim **dosya** > **yeni**  >  **Proje**.

1. Sol bölmede seçin **Visual C#** > **iş akışı** kategorisi (veya **Visual Basic** > **iş akışı**Visual Basic tercih ederseniz).

1. Orta bölmede, bir proje şablonu gibi seçin **iş akışı konsol uygulaması**.

1. İçinde **adı** kutusuna, projenizin tanınmasını kolaylaştırmak için açıklayıcı bir ad girin.

1. İçinde **konumu** kutusunda, istediğiniz projeyi kaydedin veya seçmek dizini girin **Gözat** gitmek için.

1. İçinde **çözüm** kutusunda, yeni bir çözüm için bir ad girin. Seçin **Tamam** uygulaması oluşturmak için.

   > [!NOTE]
   > Varolan bir çözüme yeni bir proje eklemek istiyorsanız, bu çözümü Visual Studio'da açın, çözüme sağ **Çözüm Gezgini**seçip **Ekle** > **yeni Proje** açmak için **yeni proje** iletişim kutusu.

## <a name="workflow-console-app"></a>İş akışı konsol uygulaması

Seçerseniz **iş akışı konsol uygulaması** şablonu, Visual Studio iş akışı tanımı XAML'de oluşturur. İş Akışı Tasarımcısı açılır ve oluşturduğunuz iş akışı için tuvale görüntüler. Bir iş akışı oluşturmak için etkinlikler veya diğer iş akışı öğeleri sürükleyin **araç** tasarım yüzeyine.

## <a name="wcf-workflow-service-app"></a>WCF iş akışı hizmeti uygulaması

Seçerseniz **WCF iş akışı hizmeti uygulaması** şablon, Visual Studio, hizmet tanımı XAML olarak oluşturur. Tasarım görünümü ile iş akışı Tasarımcısı'nı açar bir <xref:System.Activities.Statements.Sequence> içeren bir dizi etkinlik <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> etkinlikler.

## <a name="activity-library"></a>Etkinlik kitaplığı

Seçerseniz **etkinlik Kitaplığı** şablon, Visual Studio, XAML içinde bir etkinlik tanımı oluşturur. İş Akışı Tasarımcısı açar ve özel etkinliklerinizi tuvale görüntüler. Bir etkinlikten sürükleyin **araç** özel etkinlik eklemek için tasarım yüzeyine.

> [!NOTE]
> Yalnızca bir alt etkinlik özel etkinliklerinizi gövdesinde izin verilen. Ancak, bu alt etkinlik bileşik bir etkinlik gibi olabilir bir <xref:System.Activities.Statements.Sequence> etkinlik veya <xref:System.Activities.Statements.Flowchart> etkinlik.

## <a name="activity-designer-library"></a>Etkinlik Tasarımcısı kitaplığı

Seçerseniz **etkinlik Tasarımcısı Kitaplığı** şablonu, Visual Studio XAML ve arka plan kodu uygulama dosyasında bir etkinlik Tasarımcısı tanımı oluşturur. İş Akışı Tasarımcısı açılır ve tuvale, etkinlik Tasarımcısı için görüntüler. Sürükleme Windows Presentation Foundation (WPF) denetimleri **araç** özel etkinlik Tasarımcısı'nda kullanmak için tasarım yüzeyine.

Özel Etkinlik Tasarımcısı uygulamak nasıl bir örnek için bkz: [nasıl yapılır: Özel Etkinlik Tasarımcısı oluşturma](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer).

> [!NOTE]
> Özel Etkinlik tasarımcıları, varsayılan .NET Framework etkinlikler ve özel etkinlikler için kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Tasarımcısı'nı kullanın](../workflow-designer/using-the-workflow-designer.md)
- [İş akışları (.NET Framework) tasarlayın](/dotnet/framework/windows-workflow-foundation/designing-workflows)