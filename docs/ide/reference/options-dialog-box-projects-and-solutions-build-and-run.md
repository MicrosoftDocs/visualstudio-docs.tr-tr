---
title: Seçenekler İletişim Kutusu, Projeler ve Çözümler, Derleme ve Çalıştırma
ms.date: 07/14/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.Build_and_Run
helpviewer_keywords:
- builds [Visual Studio], setting up
- run actions
- debugger, run options
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1b2d047201214e3a7cd4c14c61baa041840decd8
ms.sourcegitcommit: 1abb9cf4c3ccb90e3481ea8079272c98aad12875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/26/2018
ms.locfileid: "50143326"
---
# <a name="options-dialog-box-projects-and-solutions-build-and-run"></a>Seçenekler İletişim Kutusu, Projeler ve Çözümler, Derleme ve Çalıştırma

Bu iletişim kutusunda, Visual C++ en yüksek sayısını belirtebilirsiniz veya C# aynı anda oluşturabilirsiniz projeleri, belirli bir varsayılan derleme davranışları ve bazı günlük ayarlarını oluşturun. Bu seçeneklere erişmek için seçin **Araçlar > Seçenekler** genişletin **projeler ve çözümler**seçip **derleme ve çalıştırma**.

**derleme en fazla paralel proje sayısı**

Visual C++ en fazla sayısını belirtir ve C# projeleri aynı anda oluşturabilirsiniz. Derleme işlemi iyileştirmek için en fazla paralel proje yapılandırma sayısını bilgisayarınızın CPU sayısını otomatik olarak ayarlanır. En fazla 32'dir.

**Başlangıç projelerini ve bağımlılıkları sadece çalıştırıldığında Derle**

F5 anahtar, select kullandığınızda, yalnızca başlangıç projesi ve bağımlılıklarını yapılar **hata ayıklama > Başlat** menü komutu ya da geçerli komutları **derleme** menüsü. Açık tüm projelerinizi ve bağımlılıklarınızı derleme vardır.

**Çalıştırmada, projelerin güncel olduğunda**

*Uygulandığı [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] yalnızca projeleri.*

F5 tuşuna basarak bir proje çalıştırırken veya **hata ayıklama > Başlat** komut, varsayılan ayar **oluşturmak komut istemi** bir proje yapılandırması güncel değil, bir ileti görüntüler. Seçin **her zaman derleme** her çalıştırıldığında, projeyi oluşturmak için. Seçin **asla derleme** bir projeyi çalıştırdığınızda, tüm otomatik derlemeler bastırmak için.

**Alıştırmada, ne zaman derleme veya dağıtım hataları oluşuyor**

*Uygulandığı [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] yalnızca projeleri.*

F5 tuşuna basarak bir proje çalıştırırken veya **hata ayıklama > Başlat** komut, varsayılan ayar **başlatmak komut istemi** bir proje, derleme başarısız olsa bile çalıştırılması gereken bir ileti görüntüler. Seçin **başlatma eski sürümü** çalışan kodu ve kaynak kodu uyuşmazlıklarını sonuçlanabilir son iyi derlemeden otomatik olarak başlatılacak. Seçin **başlatma** iletiyi bastırmak için.

**Yeni çözümleri şu anda seçili projeyi başlangıç projesi olarak kullanın.**

Bu seçenek ayarlandığında, yeni çözümleri şu anda seçili projeyi başlangıç projesi olarak kullanın.

**MSBuild proje oluşturması çıkış ayrıntısı**

Ne kadar bilgi görünür belirler **çıkış** derleme için penceresi.

**MSBuild proje derleme günlük dosyası ayrıntısı**

*Uygulandığı [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] yalnızca projeleri.*

Şu konumdadır derleme günlüğü dosyası için ne kadar bilgi yazılacağını belirler \\... \\ *ProjectName*\Debug\\*ProjectName*. günlük.

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme ve Oluşturma](../../ide/compiling-and-building-in-visual-studio.md)
- [Seçenekler iletişim kutusu, projeler ve çözümler](projects-and-solutions-options-dialog-box.md)
- [Seçenekler İletişim Kutusu, Projeler ve Çözümler, Web Projeleri](options-dialog-box-projects-and-solutions-web-projects.md)