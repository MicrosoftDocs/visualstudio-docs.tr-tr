---
title: Metin Şablonlarının Güvenliği
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 71052a0d4120a74269f2aa05412230284271e574
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31947527"
---
# <a name="security-of-text-templates"></a>Metin Şablonlarının Güvenliği
Metin şablonları aşağıdaki güvenlik sorunları vardır:

-   Metin şablonları rastgele kod eklemelerin etkilenir.

-   Konak bir yönerge işlemcisi bulmak için kullandığı mekanizması güvenli değilse, kötü amaçlı bir yönerge işlemcisi çalıştırabilir.

## <a name="arbitrary-code"></a>Rastgele kod
 Şablon yazarken içinde herhangi bir kod koyabilirsiniz \<## > etiketler. Bu, bir metin şablonu içinde yürütülmesi rastgele bir kodu sağlar.

 Güvenilir kaynaklardan gelen şablonları elde emin olun. Son Kullanıcılar güvenilir kaynaklardan gelen şablonları çalıştırmamayı uygulamanızın uyar emin olun.

## <a name="malicious-directive-processor"></a>Kötü amaçlı yönerge işlemcisi
 Metin şablonu altyapısı bir dönüştürme ana bilgisayar ve bir veya daha fazla yönerge işlemcileri bir çıktı dosyası şablonu metne dönüştürecek ile etkileşim kurar. Daha fazla bilgi için bkz: [metin şablonu dönüştürme süreci](../modeling/the-text-template-transformation-process.md).

 Konak bir yönerge işlemcisi bulmak için kullandığı mekanizması güvenli değilse, kötü amaçlı bir yönerge işlemcisi çalıştıran riskini çalışır. Kötü amaçlı yönerge işlemcisi çalıştırmak, kod sağlayabilir `FullTrust` şablon çalıştırdığınızda modu. Özel metin şablonu dönüştürme konağı oluşturursanız, örneğin yönerge işlemcileri bulmaya altyapısı için kayıt defteri güvenli bir mekanizma kullanmanız gerekir.