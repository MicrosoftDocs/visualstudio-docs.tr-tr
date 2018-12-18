---
title: Azure Araçları'nın geçerli sürümüne projeleri yükseltme | Microsoft Docs
description: Azure Visual Studio projesinde Azure Araçları'nın geçerli sürümüne yükseltmeyi öğrenin
author: ghogen
manager: douge
assetId: 1d64070a-078d-468a-87f4-e6715de6475f
ms.prod: visual-studio-dev15
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/18/2016
ms.author: ghogen
ms.openlocfilehash: 8d8b5ac6beb6cfb7b40f3f09fded3fef365652a4
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51000431"
---
# <a name="how-to-upgrade-projects-to-the-current-version-of-the-azure-tools-for-visual-studio"></a>Projeleri Visual Studio için Azure Araçları'nın güncel sürümüne yükseltme
## <a name="overview"></a>Genel Bakış
Azure Araçları (veya 1.6 yeni bir önceki sürüm)'in geçerli sürümünü yükledikten sonra Azure Araçları kullanılarak oluşturulmuş herhangi bir projeyi 1.6 önce sürüm (Kasım 2011) otomatik olarak yükseltilecek açmadan hemen sonra. Bu araçları 1.6 (Kasım 2011) sürümünü kullanarak projeleri oluşturulan ve hala yüklü sürümü varsa, daha eski bir sürümde bu projeleri açmak ve daha sonra bunları yükseltilmesi gerekip gerekmediğini belirleme.

## <a name="how-your-project-changes-when-you-upgrade-it"></a>Bu yükseltme yaptığınızda, projenizin nasıl değiştiğini
Yükseltmek istediğinizi belirtin veya bir proje otomatik olarak yükseltilir, projeniz belirli bütünleştirilmiş kodların geçerli sürümleri ile çalışacak şekilde değiştirilir ve bu bölümde açıklandığı gibi bazı özellikler de değiştirilir. Projenizi Araçları'nın daha yeni sürümü ile uyumlu olacak şekilde başka değişiklikler gerektiriyorsa, bu değişiklikleri el ile yapmalısınız.

* Web.config dosyası web rolleri ve çalışan rolleri için app.config dosyasında Microsoft.WindowsAzure.Diagnostics.DiagnosticMonitoirTraceListener.dll daha yeni sürümü başvurmak için güncelleştirilmiştir.
* Microsoft.WindowsAzure.StorageClient.dll Microsoft.WindowsAzure.Diagnostics.dll ve Microsoft.WindowsAzure.ServiceRuntime.dll derlemeleri yeni sürümleriyle yükseltilir.
* Azure projesi (.ccproj) dosyasında depolanan yayımlama profillerine taşınmıştır uzantısı .azurePubXml ile ayrı bir dosya içinde **Yayımla** alt.
* Yayımlama profili bazı özellikleri, yeni ve değiştirilmiş özellikler destekleyecek şekilde güncelleştirilir. **AllowUpgrade** değiştirilir **DeploymentReplacementMethod** olduğundan, dağıtılmış bir bulut hizmetinde aynı anda veya artımlı olarak güncelleştirebilirsiniz.
* Özellik **UseIISExpressByDefault** eklenir ve böylece hata ayıklama için kullanılan web sunucusu otomatik olarak Internet Information Services (IIS) IIS Express için değişmez false olarak ayarlayın. IIS Express, araçların daha yeni sürümleri ile oluşturulan projeleri için varsayılan web sunucusu olabilir.
* Azure önbelleği bir veya daha fazla proje rolleri barındırılıyorsa bir proje yükseltildiğinde bazı özellikler hizmet yapılandırma (.cscfg dosyası) ve hizmet tanımı (.csdef dosyası) değiştirilir. Azure önbellek NuGet paketini projeye kullanıyorsa, proje paketi en son sürümüne yükseltilir. Web.config dosyasını açın ve istemci yapılandırması, yükseltme işlemi sırasında düzgün şekilde tutulan doğrulamanız gerekir. Azure önbellek istemci derlemelerine başvurular NuGet paketi kullanmadan dts'e eklediyseniz, bu derlemeler güncelleştirilmez; Ayrıca, yeni sürümleri bu başvuruları el ile güncelleştirmeniz gerekir.

> [!IMPORTANT]
> F # projeleri için böylece bu derlemelerin yeni sürümlerini oldukları Azure derlemelere başvuruları el ile güncelleştirmelisiniz.
> 
> 

### <a name="how-to-upgrade-an-azure-project-to-the-current-release"></a>Bir Azure projesi geçerli sürüme yükseltme
1. Yükseltilen proje için kullanmak istediğiniz Visual Studio yüklemesini içine Azure Araçları'nın geçerli sürümü yükleyin ve ardından yükseltmek istediğiniz projeyi açın. Projeyi Azure Araçları ile oluşturulmuş olsa bile yayın önce 1.6 (Kasım 2011) projeyi otomatik olarak geçerli sürümüne yükseltilir. Projenizi oluşturduysanız ile Kasım 2011 sürüm ve sürümü yüklüdür, bu sürümde projeyi açar.
2. Çözüm Gezgini'nde proje düğümü için kısayol menüsünü açın, **özellikleri**ve ardından **uygulama** görüntülenen iletişim kutusunda sekmesi.
   
    **Uygulama** sekmesi, projeyle ilişkili Araçlar sürümü gösterir. Azure Araçları'nın geçerli sürümü varsa, proje zaten yükseltildi. Hangi sekmesini gösteren daha araçları daha yeni bir sürümünü yüklediyseniz bir **yükseltme** düğmesi görünür.
3. Seçin **yükseltme** Araçları'nın geçerli sürümüne bir projeyi yükseltmesine düğmesi.
4. Projeyi oluşturmak ve ardından API değişikliklerden kaynaklanan hataları çözün. Kodunuz için yeni sürümü değiştirme hakkında daha fazla bilgi için özel API belgelerine bakın.

