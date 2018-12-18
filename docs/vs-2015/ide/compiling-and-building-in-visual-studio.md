---
title: Derleme ve oluşturma
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ae06d11e1bdd193ebda5223c7c638c3132984147
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53052656"
---
# <a name="compiling-and-building-in-visual-studio"></a>Derleme ve Visual Studio'da oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio, uygulamalar ve derlemeler ve yürütülebilir programlar sık aralıklarla geliştirme döngüsü sırasında oluşturmak için kullanabilirsiniz. Kodunuzu genellikle oluşturarak, derleme zamanı hataları, sözdizimi yanlış yazılmış anahtar sözcükleri ve tür uyumsuzluklarına gibi daha önce belirleyebilirsiniz. Ayrıca, algılamak ve sık oluşturma ve kod hata ayıklama sürümlerini çalıştıran mantık hataları ve anlamsal hataları gibi çalışma zamanı hataları düzeltin.

 Tam olarak geliştirilen ve yeterince bir proje veya çözüm hata ayıklama bileşenleri derleme derleyebilirsiniz. Varsayılan olarak, bir yayın yapısı en iyi duruma getirilmiş ve hata ayıklama sürümünden daha küçük ve daha hızlı çalışır olacak şekilde tasarlanır. Daha fazla bilgi için [izlenecek yol: uygulama oluşturma](../ide/walkthrough-building-an-application.md).

## <a name="choosing-a-build-method"></a>Oluşturma yöntemi seçme
 Bir komut isteminde IDE içindeki varsayılan derleme Seçenekleri'ni kullanarak veya Team Foundation Yapısı'nı kullanarak bir uygulama oluşturabilirsiniz. Temel teknoloji bu seçeneklerin her birinin kullanın MSBuild ve her bir yaklaşıma, aşağıdaki tabloda gösterildiği gibi belirli avantajlar vardır.

|Derleme yöntemi|Yararları|Daha fazla bilgi için|
|------------------|--------------|--------------------------|
|IDE kullanma|-Daha kolay oluşturabilirsiniz ve Çalıştır'ı hemen oluşturur.<br />-C++ ve C# projeleri için birden çok işlemcili yapılar çalıştırabilirsiniz.<br />-Derleme Sistemi bazı yönlerini özelleştirebilirsiniz.|[Visual Studio'da Projeler ve Çözümler Oluşturma ve Temizleme](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)|
|MSBuild komut satırını çalıştıran|Visual Studio yüklemeden-projeleri oluşturabilirsiniz.<br />-Tüm proje türleri için birden çok işlemcili yapılar çalıştırabilirsiniz.<br />-Derleme sisteminin çoğu alanları özelleştirebilirsiniz.|[MSBuild](../msbuild/msbuild.md)|
|Team Foundation Yapısı kullanarak|-Yapı işleminizi otomatik hale getirebilirsiniz. Örneğin, gecelik bir veya daha fazla proje veya kodu iade her zaman oluşturabilirsiniz. Ayrıca, paylaşılan derleme sunucuları yerine geliştirme bilgisayarınızda projeleri oluşturabilirsiniz.<br />-Hızlı bir şekilde, çalıştırmak istediğiniz testleri derlemek istediğiniz kodu ve diğer ortak seçenekleri belirtebilirsiniz.<br />-Yapı iş akışını değiştirin ve ayrıntılı bir şekilde özelleştirilmiş görevleri gerçekleştirmek için yapı etkinlikleri gerektiği gibi oluşturun.|[Uygulamayı oluşturun](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)|

## <a name="building-from-the-ide"></a>IDE içinden derleme
 Bir proje oluşturduğunuzda, varsayılan derleme yapılandırmaları için tanımlanan ve çözüm yapı yapılandırması için yapılar için bağlam sağlamak için atanır. Çözüm içindeki projeleri nasıl oluşturulan ve dağıtılan çözüm yapılandırmaları tanımlar. Proje yapılandırmaları bir platform için benzersizdir ve yapı türü (örneğin, sürüm Win32) proje özellikleri kümesidir. Bu varsayılan yapılandırmalar düzenleyebilir ve kendi yapılandırmaları oluşturabilirsiniz. Daha fazla bilgi için bkz [Proje Tasarımcısı giriş](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7) ve [NIB nasıl yapılır: Proje özelliklerini değiştirmek ve yapılandırma ayarlarını](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67).

 IDE içinde aşağıdaki ek görevleri gerçekleştirebilirsiniz:

-   [Derleme çıktı dizinini değiştirme](../ide/how-to-change-the-build-output-directory.md).

-   [Doğru şekilde derlenmesi için başka bir proje çıkışı bağımlı olan projeler tanımlamak](../ide/how-to-create-and-remove-project-dependencies.md).

-   [Derleme günlüğü veya çıkış penceresine derlemelerin dahil bilgi miktarını değiştirmek](../ide/how-to-view-save-and-configure-build-log-files.md).

-   [Visual C#, Visual C++ veya Visual Basic için belirli bir derleyici uyarılarını Gizle](../ide/how-to-suppress-compiler-warnings.md).

-   [Özel belirleme konumunun derleme öncesi ve sonrası eylemleri bir derleme için derleme](../ide/specifying-custom-build-events-in-visual-studio.md).

-   Paralel yapılar kullanarak yapı performansını artırmakta. Daha fazla bilgi için [yapı paralel olarak birden çok proje](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md) veya blog gönderisinde [ayarlama C++ derleme paralellik](http://blogs.msdn.com/b/msbuild/archive/2010/03/08/tuning-c-build-parallelism-in-vs2010.aspx).

## <a name="see-also"></a>Ayrıca Bkz.
 [İzlenecek yol: bir uygulama oluşturma](../ide/walkthrough-building-an-application.md) [anlama derleme yapılandırmaları](../ide/understanding-build-configurations.md) [derleme platformlarını anlama](../ide/understanding-build-platforms.md) [(derleme) Web sitesi projeleriderleme](http://msdn.microsoft.com/library/a9cbb88c-8fff-4c67-848b-98fbfd823193) [Nasıl yapılır: Proje bağımlılıklarını oluşturma ve kaldırma](../ide/how-to-create-and-remove-project-dependencies.md)
