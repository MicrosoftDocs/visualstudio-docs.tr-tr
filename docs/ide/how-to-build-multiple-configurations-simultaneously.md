---
title: 'Nasıl yapılır: birden çok yapılandırma oluşturma'
ms.date: 05/13/2020
ms.technology: vs-ide-compile
ms.topic: how-to
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7820d56bcb266e8361f36cb5350475f31445800
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85284768"
---
# <a name="how-to-build-multiple-configurations-in-a-single-build-request"></a>Nasıl yapılır: tek bir yapı isteğinde birden çok yapılandırma oluşturma

**Batch derlemesi** iletişim kutusunu kullanarak, tek bir IDE eylemiyle birden çok veya daha fazla proje türü oluşturabilirsiniz. Ancak, aynı anda birden çok yapı yapılandırmasında aşağıdaki proje türlerini derleyebilirsiniz:

1. [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] JavaScript kullanarak Windows için oluşturulmuş uygulamalar.

2. Tüm Visual Basic projeleri.

3. CMake projeleri.

Bir çözüm bu iki proje türünün herhangi bir projesini içeriyorsa, **Toplu derleme** bu çözüm için kullanılamaz. Bu durumda, komut **Build** menüsünde görünmez.

   Derleme konfigürasyonları hakkında daha fazla bilgi için bkz. [derleme yapılandırmasını anlama](../ide/understanding-build-configurations.md).

## <a name="to-build-a-project-in-multiple-build-configurations"></a>Birden çok yapı yapılandırmasında bir proje oluşturmak için

1. Menü çubuğunda, **Build**  >  **Toplu derleme**oluştur ' u seçin. Ya da, **Ctrl** + arama kutusunu açmak için CTRL**Q** tuşlarına basın ve arama yapın `Batch Build` .

2. **Build** sütununda, bir proje derlemek istediğiniz yapılandırmaların onay kutularını seçin.

    > [!TIP]
    > Bir çözüme yönelik derleme yapılandırması düzenlemek veya oluşturmak için, menü çubuğunda **Configuration Manager oluştur**' u seçerek  >  **Configuration Manager** **Configuration Manager** iletişim kutusunu açın. Bir çözüm için yapı yapılandırmasını düzenledikten sonra, çözümdeki projelerin tüm derleme yapılandırmalarını güncelleştirmek için **Batch derlemesi** Iletişim kutusundaki **yeniden oluştur** düğmesini seçin.

3. Projeyi belirttiğiniz yapılandırmalara göre derlemek için **Derle** veya **yeniden oluştur** düğmelerini seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: yapılandırma oluşturma ve düzenleme](../ide/how-to-create-and-edit-configurations.md)
- [Derleme yapılandırmalarını anlama](../ide/understanding-build-configurations.md)
- [Paralel olarak birden çok proje oluşturun](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)