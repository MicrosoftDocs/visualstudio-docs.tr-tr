---
title: .NET Framework 4 veya .NET Framework 4.5 için geçirdiğiniz Office projelerini çalıştırmak için gereken değişiklikler
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 78a46fbffdbf849ab9f9584b72c520d5aa1d3624
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50670799"
---
# <a name="required-changes-to-run-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>.NET Framework 4 veya .NET Framework 4.5 için geçirdiğiniz Office projelerini çalıştırmak için gereken değişiklikler
  Bir Office projesi hedef Framework'ü değiştirilirse [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya daha önceki .NET Framework sürümünden çözüm geliştirme bilgisayarında ve son kullanıcı bilgisayarlarında çalışabildiğinden emin olmak için aşağıdaki görevleri gerçekleştirmeniz gerekir:  
  
- Kaldırma <xref:System.Security.SecurityTransparentAttribute> Visual Studio 2008'den yükseltilmiş ise projesi.  
  
- Gerçekleştirmek bir **temiz** çalıştırın veya geliştirme bilgisayarında projede hata ayıklamak için Visual Studio'da komutu.  
  
- .NET Framework projesi için önkoşul güncelleştirin.  
  
- Hedef Çerçeve değiştirilmeden önce ClickOnce kullanarak, daha önce dağıttıysanız, son kullanıcılar ayrıca çözüm yeniden yüklemeniz gerekir.  
  
  Bu görevlerin her biri hakkında daha fazla bilgi için aşağıdaki karşılık gelen bölümlere bakın.  
  
## <a name="remove-the-securitytransparent-attribute-from-projects-that-you-upgrade-from-visual-studio-2008"></a>Visual Studio 2008'den yükseltme projeleri SecurityTransparent özniteliğini kaldırın  
 Visual Studio 2008 ve hedef Framework'ü Office projesini yükseltirseniz, projeyi daha sonra değişikliklerini [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya daha sonra kaldırmalısınız <xref:System.Security.SecurityTransparentAttribute> proje. Visual Studio otomatik olarak bu özniteliği sizin için kaldırmaz. Bu öznitelik kaldırmazsanız, projeyi derlerken bir hata iletisi alırsınız.  
  
 Visual Studio yükseltilmiş projenin hedef çerçevesi değiştirebilirsiniz koşullar hakkında daha fazla bilgi için [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], bkz: [yükseltme ve Office çözümlerini geçirme](../vsto/upgrading-and-migrating-office-solutions.md).  
  
#### <a name="to-remove-the-securitytransparentattribute"></a>SecurityTransparentAttribute kaldırmak için  
  
1.  Projeyi Visual Studio'da Aç açın **Çözüm Gezgini**.  
  
2.  Altında **özellikleri** düğümü (C#) veya **Projem** (Visual Basic) düğümünü AssemblyInfo kod dosyası Kod Düzenleyicisi'nde açmak için çift tıklayın.  
  
    > [!NOTE]  
    >  Visual Basic projelerinde tıklamanız **tüm dosyaları göster** düğmesine **Çözüm Gezgini** AssemblyInfo kod dosyasını görmek için.  
  
3.  Bulun <xref:System.Security.SecurityTransparentAttribute> ve dosyanın kaldırmak veya yorum çıkarın.  
  
    ```vb  
    <Assembly: SecurityTransparent()>  
    ```  
  
    ```csharp  
    [assembly: SecurityTransparent()]  
    ```  
  
## <a name="perform-the-clean-command-to-debug-or-run-a-project-on-the-development-computer"></a>Hata ayıklama veya proje geliştirme bilgisayarında çalıştırma için temiz komutu gerçekleştirin  
 Bir Office projesi için projenin hedef çerçeve değiştirilmeden önce oluşturulduysa [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya daha sonra gerçekleştirmeniz gereken bir **temiz** komut ve hedef Framework'ü değiştirildikten sonra projeyi yeniden derleyin. Varsa işlemleri yapma bir **temiz** komutunu alırsınız bir <xref:System.Runtime.InteropServices.COMException> çalıştığınızda hata ayıklama veya yeniden hedeflenen projeyi çalıştırın.  
  
 Hakkında daha fazla bilgi için **temiz** komutu, bkz: [yapı Office çözümleri](../vsto/building-office-solutions.md).  
  
## <a name="update-the-prerequisites-for-deployment"></a>Güncelleştirme dağıtımı için Önkoşullar  
 Bir Office projesine hedeflediğinizde [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya daha sonra aynı zamanda ilgili .NET Framework önkoşul olarak güncelleştirmeniz gerekir **önkoşulları** iletişim kutusu. Aksi takdirde ClickOnce dağıtımı veya InstallShield Limited Edition projesi olup olmadığını denetler ve .NET Framework'ün önceki bir sürümü yükler.  
  
 Dağıtımı için Önkoşullar son kullanıcı bilgisayarlarında güncelleştirme hakkında daha fazla bilgi için bkz. [nasıl yapılır: son kullanıcı bilgisayarlarında Office çözümlerinin çalışması için Önkoşulları Yükleme](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
## <a name="reinstall-solutions-on-end-user-computers"></a>Çözümleri son kullanıcı bilgisayarlarında yeniden yükleyin.  
 .NET Framework 3. 5'i hedefleyen bir Office çözümünü dağıtmak için ClickOnce'ı kullanma ve ardından projeyi yeniden hedefle [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ya da son kullanıcılar daha sonra gerekir ve bu çözümün kaldırılması yeniden yayınladıktan sonra çözümü yeniden yükleyin. Yeniden hedeflenen çözümü yeniden yayımlamanız ve çözümün son kullanıcı bilgisayarlarında güncelleştirilir, son kullanıcıların alacak bir <xref:System.Runtime.InteropServices.COMException> çalıştırdıklarında da güncelleştirilen çözümü.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümlerini .NET Framework 4 veya sonraki sürümlere geçirme](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)  
  
  