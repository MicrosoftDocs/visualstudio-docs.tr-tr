---
title: Birim testi projesi oluşturma
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: c217b2956f5bff2f8aa5f44b88033f7f74580d3c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059054"
---
# <a name="create-a-unit-test-project"></a>Birim testi projesi oluşturma

Birim testleri, test altındaki kod yapısına genellikle yansıtır. Örneğin, her kod projesini ürün için birim testi projesi oluşturulması. Ayrı bir çözümde de olabilir veya üretim kodu aynı çözümde test projesini olabilir. Test projeleri bir çözümde birden çok birim olabilir.

> [!NOTE]
> Yerel kod için birim konumunu testleri ve test Proje yapısı bu konuda açıklanan yapısı farklı olabilir. Daha fazla bilgi için [C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md).

## <a name="to-create-a-unit-test-project"></a>Birim testi projesi oluşturmak için:

1.  Üzerinde **dosya** menüsünde seçin **yeni** seçip **proje** (klavye **Ctrl**+**Shift** + **N**).

2.  İçinde **yeni proje** iletişim kutusunda **yüklü** düğümü, test projeniz için kullanın ve ardından istediğiniz dili seçin **Test**.

3.  Microsoft birim testi çerçevelerini birini kullanmak üzere, **Birim Test projesi** proje şablonları listesinden. Aksi takdirde, kullanmak istediğiniz test çerçevesi biriminin proje şablonu seçin. Bizim örneğimizde, hesapları projeyi test etmek için projeyi garip gelse **AccountsTests**.

4.  Birim test projenizde, test edilen kod bir başvuru ekleyin.  Aynı çözümdeki bir kod projesine başvuru oluşturmak nasıl aşağıda verilmiştir:

    1.  Projede seçin **Çözüm Gezgini**.

    2.  Üzerinde **proje** menüsünde seçin **Başvuru Ekle**.

    3.  İçinde **başvuru Yöneticisi** açık iletişim kutusunu **çözüm** düğüm ve **projeleri**. Kod projesi adını denetleyin ve iletişim kutusunu kapatın.

5.  Test etmek istediğiniz kod başka bir konumda olup olmadığını, [bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md) başvurular ekleme hakkında daha fazla bilgi için.

## <a name="next-steps"></a>Sonraki adımlar

 Aşağıdaki bölümlerden birine bakın:

**Birim testleri yazma**

- [Birim testi kod](../test/unit-test-your-code.md)

- [C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md)

- [MSTest framework birim testleri kullanın](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

**Birim testlerini çalıştırma**

- [Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md)