---
title: Hangi&#39;'teki Visual Studio 2017 SDK'sı | Microsoft Docs
ms.custom: ''
ms.date: 10/31/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6f2a003bc19764aa07262552d3f0cc41316835b6
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39566914"
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>Hangi&#39;'teki Visual Studio 2017 SDK'sı

Visual Studio SDK'sı için Visual Studio 2017 aşağıdaki yeni ve güncelleştirilmiş özelliklere sahiptir.

## <a name="vsix-v3-format"></a>VSIX v3 biçimi

Visual Studio 2017'in yeni hafif yüklemeyi desteklemek için VSIX uzantısı bildirim biçimi (VSIX v3) 3. sürümüne güncelleştirildi.

Yeni biçim desteği vardır:

* Açıkça algılanabilir ve tarafından Vsıxınstaller yüklü önkoşulları bildirme.
* Uzantı yüklemesi derlemelerini Ngen.
* Genel uzantı kök dışında varlıklar yükleniyor.

Bu değişiklikler hakkında bilgi edinmek için aşağıdaki konulara bakın:

* [Genişletilebilirlik 2017 için değişiklikler](breaking-changes-2017.md)
* [VSIX v3’te Ngen desteği](ngen-support.md)
* [Uzantılar klasörünün dışına yükleme](set-install-root.md)
* [Visual Studio 2017 genişletilebilirliği için sık sorulan sorular](faq-2017.md)

## <a name="migrate-extensibility-project-to-visual-studio-2017"></a>Genişletilebilirlik projesi Visual Studio 2017'ye geçirme

Genişletilebilirlik projelerinizi ve kendi VSIX bildirimlerini Visual Studio 2017'ye güncelleştirme hakkında bilgi edinmek için bkz: [nasıl yapılır: genişletilebilirlik projelerini Visual Studio 2017'ye geçirme](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

## <a name="custom-project-and-item-templates"></a>Özel proje ve öğe şablonları

Visual Studio 2017'den itibaren özel Proje ve öğe şablonları için tarama artık gerçekleştirilir. Bunun yerine, uzantı yükleme konumu olarak bu şablonları tanımlamak, şablon bildirim dosyalarını sağlamanız gerekir. VSIX uzantılarınızı güncelleştirmek için Visual Studio 2017'yi kullanabilirsiniz. Uzantınızı bir MSI kullanarak dağıtırsanız, şablon bildirim dosyalarını el ile oluşturmanız gerekir. Daha fazla bilgi için [Visual Studio 2017 için özel Proje ve öğe şablonlarını yükseltme](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Şablon bildirim şeması belgelenen [Visual Studio şablon bildirim şeması başvurusu](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="updated-extension-performance-guidelines"></a>Güncelleştirilmiş uzantısı performans yönergeleri

Yeni bir [nasıl yapılır: uzantı performansını tanılama](how-to-diagnose-extension-performance.md) altında makalesi [yönetme VSPackages](managing-vspackages.md) algılamak ve Visual Studio uzantısı etkisini analiz etme göstermek için başlangıç ve çözüm yükleme süreleri.
