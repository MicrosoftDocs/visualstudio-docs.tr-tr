---
title: Office çözümleri oluşturma ve tasarlama
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], creating
- Office development in Visual Studio, creating solutions
- solutions [Office development in Visual Studio], creating
- Office project types in Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 05cf317823d4f5853d960109bd97da77ea8a927d
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671254"
---
# <a name="design-and-create-office-solutions"></a>Office çözümleri oluşturma ve tasarlama
  Visual Studio, birkaç farklı türde Office çözümleri oluşturmak için kullanabileceğiniz proje şablonları sağlar. Belgelerinin bu bölümü, proje şablonlarını açıklar ve Office projeleri oluşturma hakkında yönergeler sağlar. Projenizi oluşturduktan sonra kodun ve kullanıcı arabirimi özelleştirmelerinin gerçekleştirme hakkında daha fazla bilgi için bkz. [geliştirme Office çözümleri](../vsto/developing-office-solutions.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
> [!NOTE]  
>  Office deneyiminiz boyunca genişleten çözümleri geliştirme yapmakla mı ilgileniyorsunuz [birden çok platform](https://dev.office.com/add-in-availability)? Yeni kontrol [Office eklentilerini modeli](https://dev.office.com/docs/add-ins/overview/office-add-ins). Office eklentileri, VSTO eklentileri ve çözümleri için karşılaştırma küçük ayak izine sahip ve neredeyse tüm web teknolojisi, HTML5, JavaScript, CSS3 ve XML gibi programlama kullanarak oluşturabilirsiniz.  
  
## <a name="create-office-projects"></a>Office projeleri oluşturma  
 Başlamadan önce gereksinimlerinizi belirlemek ve türüne en uygun çözümü bulmak gerekir. Örneğin Office çözümünüzü uygulama kullanılır, her seferinde bir VSTO eklentisi en iyi sığar gereksinimlerinizi çalıştırmanız gerekir. Kod bir tek belge ile tümleşiktir, belge düzeyinde özelleştirme oluşturun. Bu proje türleri, Visual Studio Proje şablonları kullanılabilir. Visual Studio ile birlikte gelen Office proje şablonları hakkında daha fazla bilgi için bkz. [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md). Office projeleri oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio'da oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Office projelerinde özellikler ve Visual Studio'da proje türlerinde farklı proje öğeleri var. Örneğin, bir belge düzeyi projesi oluşturduğunuzda, belge veya çalışma kitabı, projenizdeki açılabilir ve Visual Studio içinde düzenlenebilir. Daha fazla bilgi için [Visual Studio ortamında Office projeleri](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="choose-a-net-framework-version"></a>Bir .NET Framework sürümünü seçin  
 Gereksinimlerinize en uygun proje türü seçtikten sonra hangi geliştirme sürecinizde kullanmak için .NET Framework sürümünü seçebilirsiniz. Office projelerinde aşağıdaki .NET Framework sürümlerini hedef:  
  
- [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]  
  
- [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]  
  
- [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
  
  Projeniz için seçtiğiniz .NET Framework sürümü, çözümünüzün çalışması için son kullanıcı bilgisayarlarında gereklidir. Örneğin, projenizin hedeflediği [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] son kullanıcı bilgisayarlarında gereklidir. Son kullanıcı bilgisayarlarında yüklü .NET Framework 3.5, yalnızca bu örnekte, çözümünüzü çalışmaz.  
  
  .NET Framework 3.5 hedefleyen bir VSTO eklenti projesinde geçirirseniz, Visual Studio projeniz için hedef Framework'ü değişiklikleri [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya üzeri yüklü olan Office sürümüne bağlı olarak.  
  
  Ancak, hedef Framework'ü Visual Studio değiştirdikten sonra belirli özellikleri kullanıyorsa, kodu projenizdeki bazı değiştirmeniz gerekebilir. Hedef Framework'ü değiştirme hakkında daha fazla bilgi için bkz. [nasıl yapılır: .NET Framework sürümü hedefleme](../ide/how-to-target-a-version-of-the-dotnet-framework.md). Projenizde yapmak ihtiyaç duyabilirsiniz değişiklikler hakkında daha fazla bilgi için bkz. [geçirme Office çözümlerini .NET Framework 4 veya sonraki bir sürüme](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).  
  
  Visual Studio projeniz için hedef .NET Framework değiştirir ve çözümünüzü dağıtmak için ClickOnce'ı kullanıyorsanız, aynı zamanda ilgili .NET Framework sürümünü seçtiğinizden emin **önkoşulları** iletişim kutusu. Projeniz için hedef Framework'ü değiştirdiğinizde, bu seçenek otomatik olarak değiştirmez. Daha fazla bilgi için [nasıl yapılır: son kullanıcı bilgisayarlarında Office çözümlerinin çalışması için Önkoşulları Yükleme](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
> [!NOTE]  
>  .NET Framework 3.5 veya Office projelerinde kullanarak oluşturduğunuz önceki hedefleyemez [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]. Kullanarak oluşturduğunuz office projeleri [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] sürümünde ilk yapılan özellikleri gerektirir [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]  
  
### <a name="understand-when-the-office-pias-are-required-on-end-user-computers"></a>Son kullanıcı bilgisayarlarında Office PIA'ların gerektiğinde anlama  
 Varsayılan olarak, Office birincil birlikte çalışma derlemeleri (PIA), son kullanıcı bilgisayarlarında yüklü olması gerekmez **birlikte çalışma türlerini katıştır** özelliği projedeki her Office PIA başvurusu **True**, Varsayılan değer olan. Projeyi oluşturduğunuzda bu senaryoda, çözümünüz tarafından kullanılan PIA türler için tür bilgileri çözüm derlemesine eklenir. Çalışma zamanında, Office uygulamasının COM tabanlı nesne modeline çağrı yapmak yerine PIA'ların gömülü tür bilgileri kullanılır. PIA'ların türlerinden çözümünüze nasıl katıştırılmış hakkında daha fazla bilgi için bkz. [tür eşdeğerliği ve katıştırılmış birlikte çalışma türleri](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types).  
  
 Varsa **birlikte çalışma türlerini katıştır** özelliği projedeki her Office PIA başvurusu **False**, Office PIA'ların yüklenmeli ve her bir son kullanıcı bilgisayarında genel derleme önbelleğinde kayıtlı, Çözüm çalıştırır. Çoğu durumda, varsayılan Office PIA'ların yüklü, ancak PIA çözümünüz için bir önkoşul olarak yeniden dağıtılabilir'i de içerebilir. Daha fazla bilgi için [Office çözüm dağıtım önkoşullarını](https://msdn.microsoft.com/9f672809-43a3-40a1-9057-397ce3b5126e).  
  
### <a name="understand-the-client-profile"></a>İstemci profili anlama  
 .NET Framework istemci profili, tam .NET Framework'ün bir alt kümesidir. .NET Framework istemci profili .NET Framework yalnızca istemci özelliklerini kullanmanız gerekir ve Office çözümünüz için en hızlı olası dağıtım deneyimi sağlamak istiyorsanız hedefleyebilirsiniz. Daha fazla bilgi için [.NET Framework istemci profili](/dotnet/framework/deployment/client-profile).  
  
 Hedefleyen bir Office projesi oluşturduğunuzda, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] varsayılan olarak hedeflenir. Tam için geliştirmek istiyorsanız [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], projeyi oluşturduktan sonra bu seçenek ayarlamanız gerekir. Daha fazla bilgi için [nasıl yapılır: .NET Framework sürümü hedefleme](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
## <a name="create-solutions-for-the-64-bit-edition-of-microsoft-office"></a>Çözümleri Microsoft Office'in 64 bit sürümü için oluşturma  
 Microsoft Office, 64-bit ve 32-bit sürümlerinde kullanılabilir. Her iki sürümde de çalıştırabilirsiniz Office çözümleri oluşturmak için projeniz için platform hedefi ayarı ayarlanmalıdır **herhangi bir CPU**. Office projeleri için varsayılan değer budur. Daha fazla bilgi için [yapı Office çözümleri](../vsto/building-office-solutions.md).  
  
 Ayrı 64-bit ve 32-bit sürümleri vardır [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Microsoft Office'in 64-bit ve 32-bit sürümleri tarafından kullanılır. Daha fazla bilgi için [Office çalışma zamanına genel bakış için Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## <a name="assemblies-in-office-solutions"></a>Office çözümlerinde derlemeler  
 Visual Studio'da Office geliştirme araçlarını kullanarak bir Office projesi oluşturduğunuzda, yazdığınız kod sonunda bütünleştirilmiş kod içine derlenmiş. Derleme, paylaşılan bir sunucu veya istemci bilgisayarda bir dizine dağıtılır.  
  
 Office çözümlerindeki derlemelerin bir Office uygulaması tarafından yüklenir. Derleme yüklendikten sonra derleme içindeki kod bir kullanıcı bir menü öğesini tıkladığında uygulamada, örneğin, başlatılan olaylara yanıt verebilir. Derlemedeki kod uygulamasını otomatikleştirmek ve genişletmek için nesne modeli ayrıca çağırabilir ve sınıflarda birini kullanabilirsiniz [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)]. Daha fazla bilgi için [belge düzeyi özelleştirmeler mimarisi](../vsto/architecture-of-document-level-customizations.md) ve [mimarisi, VSTO eklentileri](../vsto/architecture-of-vsto-add-ins.md).  
  
 Office çözümleri, derlemeyi tanımlamak üzere dağıtım bildirimleri ve uygulama bildirimleri kullanın. Uygulama bulmak, bağlantı ve doğru derleme çalıştırın böylece bildirimleri derlemenin adı, sürümü ve konum hakkında bilgiler içerir. Daha fazla bilgi için [uygulama ve dağıtım bildirimlerini Office çözümlerinde](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
 Belge düzeyi projeler derleme yanı sıra bir belge ekleyin. Belge uygulama ön ucu görev yapar ve tüm kullanıcı etkileşimi gerçekleştiği. Her bir belgeyi yalnızca bir ana proje derlemesi ile ilişkili olabilir; Ancak, birden çok belge aynı derlemeye işaret edebilir.  
  
 Belge düzeyi projelere derlemelerde belgeye gömülü değildir. Bunun yerine, başka bir yerde saklanır ve belgenin uygulama bildirimi tarafından tanımlanır.  
  
## <a name="security-considerations-for-assemblies"></a>Derlemeler için güvenlik konuları  
 Bir bilgisayarda çalıştırmak bir Office çözümü için çözüm tarafından kullanılan derlemeler çalıştırmak için güvenilir olması gerekir. Güvenlik hakkında daha fazla bilgi için bkz: [güvenli Office çözümleri](../vsto/securing-office-solutions.md).  
  
 Varsayılan olarak, çözüm derlemesini ve projenizin çıkış klasöründe bulunan başvurulan derlemeler projeyi oluşturduğunuzda, geliştirme bilgisayarınızda çalıştırmanıza güvenilirdir. Daha fazla bilgi için [yapı Office çözümleri](../vsto/building-office-solutions.md).  
  
 Güvenlik nedenleriyle, paylaşılan bir konumda yerel bilgisayarınızda projeleri oluşturmak en iyi yerine geliştirme. Daha fazla bilgi için [Office çözümlerinin işbirlikçi geliştirmesi](../vsto/collaborative-development-of-office-solutions.md).  
  
## <a name="referenced-assemblies"></a>Başvurulan derlemeler  
 Derleme proje başvuruları listelenen diğer derlemelere başvurabilir. Ancak, bir belge düzeyi projesi derleme başka bir belge düzeyi projesi derleme başvuramaz.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md)   
 [Nasıl yapılır: Visual Studio'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Visual Studio ortamında Office projeleri](../vsto/office-projects-in-the-visual-studio-environment.md)   
 [Office projelerinde Özellikler](../vsto/properties-in-office-projects.md)   
 [Çözümleri Microsoft Office'in farklı sürümlerinde çalıştırma](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)   
 [Nasıl yapılır: birincil birlikte çalışma derlemeleriyle hedef Office uygulamaları](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Office çözümlerinde uygulama ve dağıtım bildirimleri](../vsto/application-and-deployment-manifests-in-office-solutions.md)   
 [Nasıl yapılır: bir Office çözümü için yapılandırma bilgilerini ayarlama](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md)   
 [Visual Studio içinde Office işlevselliğini kullanma](../vsto/using-office-functionality-inside-of-visual-studio.md)   
 [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)   
 [Office programlarındaki ortak görevler](../vsto/common-tasks-in-office-programming.md)   
 [Office çözümleri geliştirme](../vsto/developing-office-solutions.md)   
 [Visual Studio'da Office çözümleri mimarisi](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  