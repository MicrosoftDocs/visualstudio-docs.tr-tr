---
title: T4 Metin Şablonu Yönergeleri
description: T4 test şablonu yönergelerini ve bunların metin şablonu dönüştürme altyapısına nasıl yönergeler sağlay olduklarını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, import directive
- text templates, include directive
- text templates, assembly directive
- text templates, output directive
- text templates, directives
- text templates, template directive
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0d9b7ca189ced11eea57e175a06b81161090070b
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388743"
---
# <a name="t4-text-template-directives"></a>T4 Metin Şablonu Yönergeleri

Yönergeler metin şablonu dönüştürme motoru için yönergeler sağlar.

Yönergelerin sözdizimi aşağıdaki gibidir:

```
<#@ DirectiveName [AttributeName = "AttributeValue"] ... #>
```

Tüm öznitelik değerleri çift tırnak işaretleri arasına alınmalıdır. Değerin kendisi tırnak işaretleri içeriyorsa, bunlardan \ karakteriyle kaçılmalıdır.

Yönergeler genellikle şablon dosyasında ya da eklenen dosyadaki ilk öğelerdir. Bunları bir kod bloğuna veya bir sınıf `<#...#>` özellik bloğuna sonra içine yerleyemebilirsiniz. `<#+...#>`

[T4 Şablon Yönergesi](../modeling/t4-template-directive.md)

```
<#@ template [language="VB"] [hostspecific="true|TrueFromBase"] [debug="true"] [inherits="templateBaseClass"] [culture="code"] [compilerOptions="options"] [visibility="internal"] [linePragmas="false"] #>
```

[T4 Parametre Yönergesi](../modeling/t4-parameter-directive.md)

```
<#@ parameter type="Full.TypeName" name="ParameterName" #>
```

[T4 Çıkış Yönergesi](../modeling/t4-output-directive.md)

```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

[T4 Derleme Yönergesi](../modeling/t4-assembly-directive.md)

```
<#@ assembly name="[assembly strong name|assembly file name]" #>
```

[T4 İçe Aktarma Yönergesi](../modeling/t4-import-directive.md)

```
<#@ import namespace="namespace" #>
```

[T4 Include Yönergesi](../modeling/t4-include-directive.md)

```
<#@ include file="filePath" #>
```

[T4 CleanUpBehavior yönergesi](../modeling/t4-cleanupbehavior-directive.md)

```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

Ayrıca, kendi yönergelerinizi oluşturabilirsiniz. Daha fazla bilgi için [bkz. Özel T4 Metin Şablonu Yönerge İşlemcileri Oluşturma.](../modeling/creating-custom-t4-text-template-directive-processors.md) Görselleştirme ve Modelleme SDK'sını etki alanına özgü dil (DSL) oluşturmak için kullanıyorsanız, bir yönerge işlemcisi, DSL'nin bir parçası olarak oluşturulur.
