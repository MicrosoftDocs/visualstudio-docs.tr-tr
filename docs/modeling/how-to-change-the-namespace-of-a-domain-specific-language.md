---
title: 'Nasıl yapılır: etki alanına özgü bir dilin ad alanını değiştirme'
ms.date: 10/31/2018
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, namespace
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 47e13e8399cba7762ff7443e4fc4cbf3a89375a6
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "50966836"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Nasıl yapılır: etki alanına özgü bir dilin ad alanını değiştirme

Etki alanına özgü bir dilin ad alanını değiştirebilirsiniz. Değişiklik yapmak **DSL Gezgini**, Dsl paket proje özelliklerinde ve derleme bilgileri.

## <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Etki alanına özgü bir dilin ad alanını değiştirmek için

1. İçinde **DSL Gezgini**seçin **Dsl** düğümü.

2. İçinde **özellikleri** penceresinde değişiklik **Namespace** özelliği.

3. Çözüm kaydedin ve şablonlarını Dönüştür.

4. Üzerinde **proje** menüsünde seçin **Dsl özellikleri**.

   Projeniz için Özellikler görünür.

5. Seçin **uygulama** sekmesi.

6. Değişiklik **varsayılan ad alanı** özelliğini yeni ad alanı adı.

7. Derlemenin adı değiştirmek istiyorsanız, değişiklik **bütünleştirilmiş kodun ad özelliği.**

8. Derleme adı değişmişse DslPackage\Package.tt açın ve bu satırı güncelleştirin:

   `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. Herhangi bir özel kod yazdığınız, kod dosyalarında ad alanını ve sınıf başvuruları değiştirdiğinizden emin olun.

10. Visual Studio deneysel örneği sıfırlayın.

    1. Silme **\Users\\**_{adınız}_**\AppData\Local\Microsoft\VisualStudio\\\*Exp**.

    2. Windows üzerinde **Başlat** menüsünde seçin **tüm programlar** > **Microsoft Visual Studio 2010 SDK** > **Araçları**  >  **Deneysel örneğini sıfırlama**.

11. Üzerinde **derleme** menüsünde seçin **çözümü yeniden derle**.

## <a name="see-also"></a>Ayrıca bkz.

[Etki alanına özgü dil araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)