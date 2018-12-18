---
title: Veritabanları ve veri katmanı uygulamaları oluşturma ve yönetme
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing change, databases
- database features of Visual Studio, managing change
- databases, managing change
- managing change, database servers
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
caps.latest.revision: 40
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 90ed31f442a1ca30c34554549e1d186cb2c320ee
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53061248"
---
# <a name="creating-and-managing-databases-and-data-tier-applications-in-visual-studio"></a>Veritabanlarını ve Visual Studio'daki veri katmanı uygulamaları oluşturma ve yönetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


ÖNEMLİ]
>  ' In önceki sürümlerinde bulunan veritabanı projeleri [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] artık sağlanan [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)] araçları. Daha fazla bilgi için [SQL Server Geliştirici Araçları](http://go.microsoft.com/fwlink/?LinkId=228126).

 Veritabanı projeleri yeni veritabanları oluşturmak için kullanabileceğiniz yeni veri katmanı uygulamaları (Dac'ler) ve var olan veritabanlarını ve veri katmanı uygulamaları güncelleştirmek için. Hem veritabanı projeleri hem de DAC projeleri çok yönetilen veya yerel kod için bu teknikler uyguladığınız aynı şekilde, veritabanı geliştirme çalışmalarınızda kullanmanız için sürüm denetimi ve proje yönetimi teknikleri uygulanmasını sağlar. Geliştirme ekibiniz oluşturarak veritabanları ve veritabanı sunucuları için değişiklikleri yönetmenize yardımcı olabilir bir *DAC proje*, *veritabanı projesi*, veya bir *sunucu projesi* ve onu koyma Sürüm denetimi altında. Ekip üyelerinin sonra kontrol edebilirsiniz olun, derleme ve değişiklikleri test etmek için dosyaları bir *yalıtılmış bir geliştirme ortamı*, veya önce onları takım ile paylaşım korumalı alan. Kod kalitesinin sağlanmasına yardımcı olmak için takımınızın tamamlayın ve değişiklikleri üretime dağıtmadan önce tüm değişiklikleri veritabanını belirli bir sürümü için bir hazırlama ortamında test.

 Veri katmanı uygulamaları tarafından desteklenen veritabanı özelliklerin bir listesi için bkz. [veri katmanı uygulamalarında desteklenen özellikleri](http://go.microsoft.com/fwlink/?LinkId=164239) Microsoft web sitesinde. Veri katmanı uygulamaları tarafından desteklenmeyen özellikleri veritabanınızdaki kullanırsanız, veritabanınıza değişiklikleri yönetmek için bunun yerine bir veritabanı projesi kullanmanız gerekir.

## <a name="common-high-level-tasks"></a>Ortak bir üst düzey görevler

|Üst düzey görev|Destekleyici İçerik|
|----------------------|------------------------|
|**Veri katmanı uygulaması geliştirmeye başla:** A DAC ile sunulan yeni bir kavram olan [!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] tanımını içeren bir [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] veritabanını ve destekleyen bir istemci-sunucu veya 3 katmanlı tarafından kullanılan nesneleri örneği uygulama. Bir DAC, tablolar ve görünümler, oturum açma bilgileri gibi örnek varlıkları birlikte gibi nesneleri içerir. Kullanabileceğiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] DAC projesi oluşturmak için bir DAC paket dosyası derleme ve dağıtım örneği için bir veritabanı yöneticisi bu DAC paket dosyası göndermek [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] veritabanı altyapısı.|-   [Veri katmanı uygulamaları oluşturma ve yönetme](http://go.microsoft.com/fwlink/?LinkId=160741) (Microsoft web sitesi)<br />-   [SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=227328)|
|**Yinelemeli veritabanı geliştirme gerçekleştirme:** bir geliştirici veya test edici ise, proje bölümlerini denetleyin ve ardından bunları bir yalıtılmış geliştirme ortamında güncelleştirin. Bu ortam türünü kullanarak, diğer takım üyeleri etkilemeden değişikliklerinizi test edebilirsiniz. Değişiklik tamamlandıktan sonra burada diğer takım üyelerinin yaptığınız değişiklikleri alabilir ve yapı ve bunları bir test sunucusuna dağıtmak geri sürüm denetimine, dosyaları denetleyin.|-   [Sorgu ve metin düzenleyiciler (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) (Microsoft web sitesi)<br />-   [Transact-SQL hata ayıklayıcısını](http://go.microsoft.com/fwlink/?LinkId=227324) (Microsoft web sitesi)|
|**Doğrulama prototip oluşturma, test sonuçları ve değiştirme veritabanı betikleri ve nesneleri:** kullanabileceğiniz [!INCLUDE[tsql](../includes/tsql-md.md)] herhangi biri şu genel görevleri gerçekleştirmek için düzenleyici.|-   [Sorgu ve metin düzenleyiciler (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) (Microsoft web sitesi)|

## <a name="see-also"></a>Ayrıca Bkz.
 [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)
