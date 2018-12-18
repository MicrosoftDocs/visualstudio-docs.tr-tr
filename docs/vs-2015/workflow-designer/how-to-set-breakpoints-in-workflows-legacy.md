---
title: 'Nasıl yapılır: kesme noktası ayarlama (eski) iş akışlarında | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- breakpoints, setting in workflows
- debugging, setting breakpoints in workflows
- debugging workflows, setting breakpoints
- workflows, setting breakpoints
ms.assetid: 78e0be39-3e99-487c-bfef-19db0daf6f42
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 158592ccef331c541bf27494856cfa1314b21f88
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49252557"
---
# <a name="how-to-set-breakpoints-in-workflows-legacy"></a>Nasıl yapılır: (eski) akışlarında kesme noktası ayarlama
Kesme noktaları ayarlama hakkında bilgi için bu konuda açıklanmaktadır [!INCLUDE[wf](../includes/wf-md.md)] uygulamaları oluşturmak eski kullanarak [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Eski kullanın [!INCLUDE[wfd2](../includes/wfd2-md.md)] olduğunda, [!INCLUDE[wf2](../includes/wf2-md.md)] uygulamanın gerekir ya da hedeflemek [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] veya [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Eski kullandığınızda [!INCLUDE[wfd2](../includes/wfd2-md.md)] içinde [!INCLUDE[vs2010](../includes/vs2010-md.md)] oluşturmak için bir [!INCLUDE[wf2](../includes/wf2-md.md)] uygulama ayarlayabileceğiniz kesme noktaları C# ve Visual Basic kodu Visual Studio'da yaptığınız gibi. Beklendiği gibi iş akışı yürütme ayarladığınız her bir kesme noktasında durur.  
  
 Bir kesme noktası üç durumu vardır: *bekleyen*, *bağlı*, ve *hata*. Bir kesme noktası ayarlarsanız, bekleyen ve boş kırmızı bir simge ile temsil edilir. Çalışma zamanı iş akışı türü yüklendiğinde bağlı olur ve düz kırmızı bir simge ile temsil edilir. Yanlış bir biçimde kesme noktası için geçersiz bir etkinlik adı olarak belirtirseniz, hata penceresinde görünür. Kesme noktası hala kesme noktası penceresine eklenir, ancak küçük "x" ile işaretlenir.  
  
 Aşağıdaki yollarla bir etkinlik iş akışı tasarım yüzeyinde kesme noktaları ayarlayabilirsiniz:  
  
-   Etkinliğe sağ tıklayın ve seçin **kesme noktası \ kesme noktası Ekle**.  
  
-   Etkinliği seçin ve F9 tuşuna basın.  
  
-   Seçin **yeni kesme noktası** gelen **hata ayıklama** menüsü.  
  
     Hata ayıklayıcı bir kesme noktasında durduğunda, hata ayıklama sırasında yeni bir kesme noktası ayarlamak için bu seçeneği'ni de kullanabilirsiniz.  
  
    > [!NOTE]
    >  Çağrılan iş akışlarında kesme noktaları ayarlama desteklenmiyor.  
  
### <a name="to-set-a-breakpoint-using-the-new-breakpoint-option-on-the-debug-menu"></a>Hata ayıklama menüsünden Yeni kesme noktası seçeneğini kullanarak bir kesme noktası ayarlamak için  
  
1.  Üzerinde **hata ayıklama** menüsünde **yeni kesme noktası**.  
  
2.  Tıklayın **sonu işlevi**.  
  
     **Yeni kesme noktası** iletişim kutusu açılır.  
  
3.  Bir etkinlik adını **işlevi** bu söz dizimini kullanarak metin kutusu: `QualifiedActivityId[:[FullClassName][:InstanceId]]`.  
  
    > [!NOTE]
    >  Etkinlik adı yerine isteğe bağlı olarak, **işlevi** metin kutusunda, iş akışı aktivitesi mutlak yolunu belirterek bir kesme noktası ayarlayabilirsiniz. Örneğin, adında bir iş akışı çözümü olduğunu varsayalım **WorkflowConsoleApplication1** ve bir iş akışında adlı çözüm **Workflow1** adlı bir etkinlik kullanan **Delay1**. Etkinlik adı kullanabileceğiniz **Delay1** veya yol olarak belirtmek **Delay1:WorkflowConsoleApplication1.Workflow1** veya **Delay1:WorkflowConsoleApplication1.Workflow1: { 6614886A-608E-412B-BF98-99FF1559DDDF}**.  
  
4.  Seçin **kullanım IntelliSense** işlev adını doğrulamak için onay kutusunu işaretleyin.  
  
     Bu onay kutusu seçili değilse, hiçbir kesme noktası adı doğrulama gerçekleştirilir.  
  
5.  Seçin **iş akışı** gelen **dil** listesi.  
  
6.  **Tamam**'ı tıklatın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eski iş akışlarında hata ayıklama](../workflow-designer/debugging-legacy-workflows.md)   
 [Windows Workflow Foundation için Visual Studio Hata Ayıklayıcısını Çağırma (Eski)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)