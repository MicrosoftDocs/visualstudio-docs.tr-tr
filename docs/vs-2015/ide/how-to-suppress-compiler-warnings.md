---
title: 'Nasıl yapılır: Derleyici uyarılarını gizleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 31827b17-f933-413d-b28a-b19f903b64ca
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7cb1bbc637b51ecf75c0b491a5918ceaa147aa8f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49932318"
---
# <a name="how-to-suppress-compiler-warnings"></a>Nasıl yapılır: Derleyici Uyarılarını Gizleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Derleyici uyarılarını içerecek şekilde istemediğiniz bir veya daha fazla tür belirterek bir yapı günlüğüne declutter. Örneğin, bazı gözden geçirmek için bu teknik, ancak Normal, ayrıntılı ya da tanılama günlük derleme ayrıntı ayarladığınızda, otomatik olarak oluşturulan bilgilerin tümünü kullanabilirsiniz. Ayrıntı düzeyi hakkında daha fazla bilgi için bkz. [nasıl yapılır: görünümü, kaydetme ve yapılandırma derleme günlük dosyalarını](../ide/how-to-view-save-and-configure-build-log-files.md).  
  
### <a name="to-suppress-specific-warnings-for-visual-c-or-f"></a>Visual C# veya F # için belirli uyarıları bastırmak için  
  
1.  İçinde **Çözüm Gezgini**, uyarıları bastırmak istediğiniz projeyi seçin.  
  
2.  Menü çubuğunda, **görünümü**, **özellik sayfaları**.  
  
3.  Seçin **derleme** sayfası.  
  
4.  İçinde **uyarıları bastırma** kutusunda gizlemek istediğiniz uyarıların hata kodlarını noktalı virgülle ayırarak belirtin ve ardından çözümü yeniden oluşturun.  
  
### <a name="to-suppress-specific-warnings-for-visual-c"></a>Visual C++ için belirli uyarıları bastırmak için  
  
1.  İçinde **Çözüm Gezgini**, projeyi seçin veya uyarıları bastırmak istediğiniz dosya kaynağı.  
  
2.  Menü çubuğunda, **görünümü**, **özellik sayfaları**.  
  
3.  Seçin **yapılandırma özellikleri** kategorisi seçin **C/C++** kategori seçip **Gelişmiş** sayfası.  
  
4.  Aşağıdaki adımlardan birini uygulayın:  
  
    -   İçinde **belirli uyarıları devre dışı** kutusunda, gizlemek istediğiniz uyarıları hata kodlarının noktalı virgülle ayrılmış belirtin.  
  
    -   İçinde **belirli uyarıları devre dışı** kutusunda **Düzenle** daha fazla seçenek görüntülenecek.  
  
5.  Seçin **Tamam** düğmesini ve ardından çözümü yeniden oluşturun.  
  
## <a name="suppressing-warnings-for-visual-basic"></a>Visual Basic için uyarıları gizleme  
 Belirli bir derleyici uyarılarını Visual Basic projesi için .vbproj dosyasını düzenleyerek gizleyebilirsiniz. Ayrıca [derleme sayfası, Proje Tasarımcısı](../ide/reference/compile-page-project-designer-visual-basic.md) kategoriye göre uyarıları bastırmak için. Daha fazla bilgi için [Visual Basic'teki uyarıları yapılandırma](../ide/configuring-warnings-in-visual-basic.md).  
  
#### <a name="to-suppress-specific-warnings-for-visual-basic"></a>Visual Basic için belirli uyarıları bastırmak için  
  
1. İçinde **Çözüm Gezgini**, uyarıları bastırmak istediğiniz projeyi seçin.  
  
2. Menü çubuğunda, **proje**, **projeyi**.  
  
3. İçinde **Çözüm Gezgini**, proje için kısayol menüsünü açın ve ardından **Düzenle**_ProjectName_**.vbproj**.  
  
    Proje dosyası Kod Düzenleyicisi'nde açılır.  
  
4. Bulun `<NoWarn></NoWarn>` ile oluşturmakta olduğunuza yapı yapılandırma öğesi.  
  
    Aşağıdaki örnekte gösterildiği `<NoWarn></NoWarn>` kalın metin için hata ayıklama derleme yapılandırmasını x x86 öğesinde platformu:  
  
   ```  
   <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">  
       <PlatformTarget>x86</PlatformTarget>  
       <DebugSymbols>true</DebugSymbols>  
       <DebugType>full</DebugType>  
       <Optimize>false</Optimize>  
       <OutputPath>bin\Debug\</OutputPath>  
       <DefineDebug>true</DefineDebug>  
       <DefineTrace>true</DefineTrace>  
       <ErrorReport>prompt</ErrorReport>  
       <NoWarn></NoWarn>  
       <WarningLevel>1</WarningLevel>  
     </PropertyGroup>  
   ```  
  
5. Bir veya daha fazla uyarı numaralarını değeri olarak Ekle `<NoWarn>` öğesi. Birden çok uyarı numaralarını belirtirseniz, aşağıdaki örnekte gösterildiği gibi bir virgül ile ayırın.  
  
   ```  
   <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">  
       <PlatformTarget>x86</PlatformTarget>  
       <DebugSymbols>true</DebugSymbols>  
       <DebugType>full</DebugType>  
       <Optimize>false</Optimize>  
       <OutputPath>bin\Debug\</OutputPath>  
       <DefineDebug>true</DefineDebug>  
       <DefineTrace>true</DefineTrace>  
       <ErrorReport>prompt</ErrorReport>  
       <NoWarn>40059,42024</NoWarn>  
       <WarningLevel>1</WarningLevel>  
     </PropertyGroup>  
   ```  
  
6. .vbproj dosyasındaki değişiklikleri kaydedin.  
  
7. Menü çubuğunda, **proje**, **projeyi**.  
  
8. Menü çubuğunda, **derleme**, **çözümü yeniden derle**.  
  
    **Çıkış** penceresi artık belirtilen uyarıları gösterir.  
  
   Daha fazla bilgi için [/nowarn](http://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: bir uygulama oluşturma](../ide/walkthrough-building-an-application.md)   
 [Nasıl yapılır: görüntüleme, kaydetme ve derleme günlüğü dosyalarını yapılandırma](../ide/how-to-view-save-and-configure-build-log-files.md)   
 [Derleme ve Oluşturma](../ide/compiling-and-building-in-visual-studio.md)



