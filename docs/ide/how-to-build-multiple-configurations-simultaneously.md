---
title: 'Nasıl yapılır: aynı anda birden fazla yapılandırma derleme'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3e3e5fb1eea1d8bf821bf55b50ccfc1db488249b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49910608"
---
# <a name="how-to-build-multiple-configurations-simultaneously"></a>Nasıl yapılır: aynı anda birden fazla yapılandırma derleme

Birden çok proje veya bile tüm yapı yapılandırmalarına aynı anda birçok türü kullanarak oluşturabilirsiniz **Toplu derleme** iletişim kutusu. Ancak, aynı anda birden çok oluşturma yapılandırmasında projeleri aşağıdaki türde oluşturulamıyor:

1. [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] JavaScript kullanarak Windows için oluşturulmuş uygulamalar.

2. Tüm Visual Basic projeleri.

   Derleme yapılandırmaları hakkında daha fazla bilgi için bkz. [anlayın derleme yapılandırmaları](../ide/understanding-build-configurations.md).

## <a name="to-build-a-project-in-multiple-build-configurations"></a>Birden çok oluşturma yapılandırmasında bir proje oluşturmak için

1. Menü çubuğunda, **derleme** > **Toplu derleme**.

2. İçinde **derleme** onay kutularını bir projeyi derlemek istediğiniz yapılandırmaları için sütun seçin.

    > [!TIP]
    > Çözüm yapı yapılandırması oluşturun veya düzenlemek için seçin **derleme** > **Configuration Manager** açmak için menü çubuğunda **Configuration Manager** iletişim kutusu. Bir çözüm için bir derleme yapılandırması düzenledikten sonra seçin **yeniden** düğmesine **Toplu derleme** derleme yapılandırmaları Çözümdeki projeler için tüm güncelleştirmek için iletişim kutusu.

3. Seçin **derleme** veya **yeniden** belirttiğiniz yapılandırmaları olan bir projeyi derlemek için düğmeler.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: yapılandırmaları oluşturma ve düzenleme](../ide/how-to-create-and-edit-configurations.md)
- [Derleme yapılandırmalarını anlama](../ide/understanding-build-configurations.md)
- [Paralel olarak birden çok proje derleme](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)