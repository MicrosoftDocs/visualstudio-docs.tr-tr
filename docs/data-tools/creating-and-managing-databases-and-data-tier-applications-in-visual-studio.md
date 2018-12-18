---
title: Veritabanı projeleri ve DAC projeleri
ms.date: 11/21/2018
ms.topic: conceptual
helpviewer_keywords:
- databases, managing change
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d8671c46cf2e88ab5d5797dd7a009ff29b953c4e
ms.sourcegitcommit: c9a01c599ce19a5845605b3b28c0229fd0abb93f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2018
ms.locfileid: "52281738"
---
# <a name="database-projects-and-data-tier-applications"></a>Veritabanı projeleri ve veri katmanı uygulamaları

Veritabanı projeleri yeni veritabanları oluşturmak için kullanabileceğiniz yeni veri katmanı uygulamaları (Dac'ler) ve var olan veritabanlarını ve veri katmanı uygulamaları güncelleştirmek için. Hem veritabanı projeleri hem de DAC projeleri çok yönetilen veya yerel kod için bu teknikler uyguladığınız aynı şekilde, veritabanı geliştirme çalışmalarınızda kullanmanız için sürüm denetimi ve proje yönetimi teknikleri uygulanmasını sağlar. DAC proje, veritabanı projesi veya bir sunucu projesi oluşturma ve sürüm denetimi altında koyarak veritabanları ve veritabanı sunucuları değişiklikleri yönetme geliştirme ekibinize yardımcı olabilir. Ekip üyelerinin olun, derleme ve değişiklikleri bir yalıtılmış bir geliştirme ortamı veya korumalı alan, takım paylaşmadan önce test dosyaları kontrol edebilirsiniz. Kod kalitesinin sağlanmasına yardımcı olmak için takımınızın tamamlayın ve değişiklikleri üretime dağıtmadan önce tüm değişiklikleri veritabanını belirli bir sürümü için bir hazırlama ortamında test.

Veri katmanı uygulamaları tarafından desteklenen veritabanı özelliklerin bir listesi için bkz. [DAC desteklemek için SQL Server nesne](/sql/relational-databases/data-tier-applications/dac-support-for-sql-server-objects-and-versions). Veri katmanı uygulamaları tarafından desteklenmeyen özellikleri veritabanınızdaki kullanırsanız, veritabanınıza değişiklikleri yönetmek için bunun yerine bir veritabanı projesi kullanmanız gerekir.

## <a name="common-high-level-tasks"></a>Ortak bir üst düzey görevler

| Üst düzey görev | Destekleyici İçerik |
| - | - |
| **Veri katmanı uygulaması geliştirmeye başla:** kavramı bir veri katmanı uygulaması (DAC), SQL Server 2008 ile kullanılmaya başlandı. Bir DAC, bir SQL Server veritabanı ve bir istemci-sunucu veya 3 katmanlı uygulama tarafından kullanılan destekleyici örneği nesneler için bir tanım içeriyor. Bir DAC, tablolar ve görünümler, oturum açma bilgileri gibi örnek varlıkları birlikte gibi nesneleri içerir. DAC proje oluşturma, derleme DAC paket dosyası ve SQL Server veritabanı altyapısı örneğine dağıtım için bir veritabanı yöneticisi DAC paket dosyası göndermek için Visual Studio kullanabilirsiniz. | - [Veri katmanı uygulamaları](/sql/relational-databases/data-tier-applications/data-tier-applications)<br />- [SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms) |
| **Yinelemeli veritabanı geliştirme gerçekleştirme:** geliştiriciler, proje bölümlerini kontrol edin ve bunları bir yalıtılmış geliştirme ortamında güncelleştirin. Bu ortam türünü kullanarak, diğer takım üyeleri etkilemeden değişikliklerinizi test edebilirsiniz. Değişiklik tamamlandıktan sonra burada diğer takım üyelerinin yaptığınız değişiklikleri alabilir ve yapı ve bunları bir test sunucusuna dağıtmak geri sürüm denetimine, dosyaları denetleyin. | - [Çevrimdışı veritabanı proje odaklı geliştirme (SQL Server veri araçları)](/sql/ssdt/project-oriented-offline-database-development)<br />- [Transact-SQL hata ayıklayıcı (SQL Server Management Studio)](/sql/ssms/scripting/transact-sql-debugger) |
| **Doğrulama prototip oluşturma, test sonuçları ve değiştirme veritabanı betikleri ve nesneleri:** herhangi biri şu genel görevleri gerçekleştirmek için Transact-SQL Düzenleyicisi'ni kullanabilirsiniz. | - [Sorgu ve metin düzenleyiciler (SQL Server Management Studio)](/sql/ssms/scripting/query-and-text-editors-sql-server-management-studio) |

## <a name="see-also"></a>Ayrıca bkz.

- [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)