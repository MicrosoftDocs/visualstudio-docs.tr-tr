---
title: Visual Studio sürümlerini yan yana yükleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
ms.assetid: 4d00f240-4910-4699-aaf3-cda6461f0c29
caps.latest.revision: 48
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: be7559fb9bc6a2e028638ae18209a91cde955e7f
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53056645"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Visual Studio sürümlerini yan yana yükleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio'nun bu sürümü zaten daha önceki bir sürümün yüklü olduğu bir bilgisayara yükleyebilirsiniz. Bir yükleme hatasıyla karşılaşırsanız, kullanabileceğiniz [günlük toplama aracı](http://go.microsoft.com/fwlink/?LinkId=262077) , sorunları kendiniz çözmek üzere hatalar hakkında bilgi toplamak için.

> [!NOTE]
> Yüklemenizi öneririz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bunlar yayımlanan sırada sürümleri. Örneğin, Visual Studio 2015'i yüklemeden önce Visual Studio 2013 yükleyin.

 Sürümleri yan yana yüklemeden önce aşağıdaki koşulları gözden geçirin:

-   İçinde oluşturulmuş bir çözümü açmak için Visual Studio 2015 kullanıyorsanız [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)], daha sonra açın ve Visual Studio 2015'e özgü herhangi bir özellik uygulamadığınız sürece çözümü yeniden eski sürümü değiştirin.

-   İçinde oluşturulmuş bir çözümü açmak için Visual Studio 2015 kullanmaya çalışırsanız [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] veya önceki bir sürümü projelerinizi ve dosyalarınızı Visual Studio 2015 ile uyumlu olacak şekilde değiştirmeniz gerekebilir. Daha fazla bilgi için [bağlantı noktası, geçirme ve yükseltme Visual Studio projeleri](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects?view=vs-2015) sayfası.

-   Bir sürümünü kaldırırsanız [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] birden fazla sürümü yüklü olan bir bilgisayarda dosya ilişkilendirmeleri [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tüm sürümler için kaldırılır. Kullanarak bu dosya ilişkilerini yeniden eşleyebilirsiniz **dosya ilişkilerini geri yükle** düğmesini **ortam**, **genel** sayfasının [seçenekleri](../ide/reference/general-environment-options-dialog-box.md) iletişim kutusu.

-   Tüm uzantıları uyumlu olmadığından visual Studio uzantıları otomatik olarak yükseltmez. Uzantılar'dan yeniden yüklemeniz gerekir [Visual Studio Market](http://go.microsoft.com/fwlink/?LinkId=178891) veya yazılım yayımcısından.

## <a name="net-framework-versions-and-side-by-side-installations"></a>.NET framework sürümleri ve yan yana yüklemeler

-   Visual Basic, Visual C#, görsel ve F# projelerde kullan **hedef Framework'ü** seçeneğini **Proje Tasarımcısı** bir projenin hangi .NET Framework sürümünü kullandığını belirtmek için. Bir C++ projesi için .vcxproj dosyasını değiştirerek hedef Framework'ü el ile değiştirebilirsiniz. Daha fazla bilgi için [sürüm uyumluluğu](http://msdn.microsoft.com/library/2f25e522-456a-48c3-8a53-e5f39275649f).

     Bir proje oluşturduğunuzda, projenin hangi .NET Framework sürümünü hedefleyeceğini belirtebilirsiniz **.NET Framework** listesinde **yeni proje** iletişim kutusu.

     Dile özgü bilgiler için aşağıdaki tabloda ilgili konuya bakın.

    |Dil|Konu|
    |--------------|-----------|
    |[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]|[Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)|
    |Visual C#|[Uygulama Sayfası, Proje Tasarımcısı (C#)](../ide/reference/application-page-project-designer-csharp.md)|
    |Visual F#|[Projeleri Yapılandırma](http://msdn.microsoft.com/library/a1489abb-6294-4f8f-b71f-2cb126393526)|
    |C++|[Nasıl Yapılır: Hedef Framework ve Platform Araç Kümesini Değiştirme](http://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe)|
    |[!INCLUDE[jsprjscript](../includes/jsprjscript-md.md)]|[Ortak dil çalışma zamanının önceki bir sürümünde JScript uygulaması çalıştırma](http://msdn.microsoft.com/en-us/bbea51b5-ac03-4e6c-b9a6-f487ef63eda5)|

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio'yu yükleyin](../install/install-visual-studio-2015.md)
- [Taşıma, geçirme ve Visual Studio projelerini yükseltme](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects?view=vs-2015)
- [C/C++ Yalıtılmış Uygulamaları ve Yan Yana Derlemeleri Oluşturma](http://msdn.microsoft.com/library/9465904e-76f7-48bd-bb3f-c55d8f1699b6)
- [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)