---
title: 'Nasıl yapılır: projeleri hedef birden çok platform için yapılandırma'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], targeting platforms
- platforms, changing target platforms
ms.assetid: affa2392-7aed-45ac-9ffa-1d8e0496d590
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 308858941d03f6341cf3d22af074be45d790e16b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49930225"
---
# <a name="how-to-configure-projects-to-target-multiple-platforms"></a>Nasıl yapılır: projeleri hedef birden çok platform için yapılandırma

Visual Studio aynı anda birçok farklı CPU mimarileri veya platformlarını hedeflemek bir çözüm için bir yol sağlar. Ayarlamak için bu özellikleri aracılığıyla erişilen **Configuration Manager** iletişim kutusu.

## <a name="target-a-platform"></a>Hedef platform

**Configuration Manager** iletişim kutusunda, oluşturmak ve çözüm ve proje düzeyinde yapılandırmalar ve platformlar izin verir. Her bir çözüm düzeyinde yapılandırmaları ve hedefleri bileşimi benzersiz bir hedefleyen arasında kolayca, örneğin, bir sürüm yapılandırması geçiş olanak tanıyan ilişkili özellikler kümesini olabilir bir [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)] platform, yayın yapılandırması x x86 hedefleyen platform ve bir x86 hedefleyen bir hata ayıklama yapılandırması platformu.

1.  Üzerinde **derleme** menüsünde tıklatın **Configuration Manager**.

2.  İçinde **etkin çözüm platformu kutusu**, çözümünüze hedef istediğiniz ya da seçin platformu seçin  **\<yeni >** yeni platformu oluşturmak için. Visual Studio, uygulamanızın etkin platform olarak ayarlandığından platformunu hedeflemeniz derleme **Configuration Manager** iletişim kutusu.

## <a name="remove-a-platform"></a>Bir platform Kaldır

Gerek bir platform olduğunu fark ederseniz kullanarak kaldırabilirsiniz **Configuration Manager** iletişim kutusu. Bu, yapılandırma ve hedef birleşimi için yapılandırdığınız tüm çözüm ve proje ayarlarını kaldırır.

1.  Üzerinde **derleme** menüsünde tıklatın **Configuration Manager**.

2.  İçinde **etkin çözüm platformu kutusu**seçin  **\<Düzenle >**. **Çözüm platformları Düzenle** iletişim kutusu açılır.

3.  Kaldırın ve istediğiniz platform tıklayın **Kaldır**.

## <a name="target-multiple-platforms-with-one-solution"></a>Bir Çözümle birden fazla platformu hedefleyin

Ayarlarını yapılandırma ve platform ayarları birleşimi göre değişebileceği için birden çok platformu hedefleyen bir çözümünü ayarlayabilirsiniz.

### <a name="to-target-multiple-platforms"></a>Birden çok platformu hedefleyecek şekilde

1.  Kullanım **Configuration Manager** en az iki hedef platformlara çözümü eklemek için.

2.  Gelen hedeflemek istediğiniz platformu seçin **etkin çözüm platformu** listesi.

3.  Çözümü oluşturun.

### <a name="to-build-multiple-solution-configurations-at-once"></a>Aynı anda birden çok çözüm yapılandırmaları oluşturmak için

1. Kullanım **Configuration Manager** en az iki hedef platformlara çözümü eklemek için.

2. Kullanım **Toplu derleme** penceresi aynı anda çeşitli çözüm yapılandırmalar da oluşturabilirsiniz.

   Örneğin, ayarlamak için bir çözüm düzeyinde platforma sahip mümkündür [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)], ve aynı platform hedefleme, çözüm içinde proje yok. Çözümünüz içinde her farklı platformları hedefleyen birden çok proje mümkündür. Bunlardan biri varsa, Karışıklığı önlemek için açıklayıcı bir ad ile yeni bir yapılandırma oluşturmak önerilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: yapılandırmaları oluşturma ve düzenleme](../ide/how-to-create-and-edit-configurations.md)
- [Derleme yapılandırmalarını anlama](../ide/understanding-build-configurations.md)
- [Derleme ve temizleme projeleri ve Visual Studio çözümleri](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
