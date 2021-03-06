---
title: VS Shell 'e VSPackage dosya konumunu belirtme | Microsoft Docs
description: Visual Studio 'nun VSPackage 'ı yüklemek için derleme DLL 'sini bulması için nasıl mümkün olabileceğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: efec1ac3f7ccb3884265f3740108aaef261e9378
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064091"
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>VS Kabuğuna VSPackage Dosya Konumunu Belirtme
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage 'ı yüklemek için derleme DLL dosyasını bulabilmelidir. Aşağıdaki tabloda açıklandığı gibi çeşitli yollarla konumunu bulabilirsiniz.

| Yöntem | Açıklama |
| - | - |
| CodeBase kayıt defteri anahtarını kullanın. | CodeBase anahtarı, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] herhangi bir tam dosya yolundan VSPackage derlemesini yüklemek için doğrudan kullanılabilir. Anahtarın değeri DLL 'nin dosya yolu olmalıdır. Bu, paket derlemenizi yüklemek için en iyi yoldur [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Bu teknik bazen "CodeBase/Private yükleme dizini tekniği" olarak adlandırılır. Kayıt sırasında, kod temelinin değeri, kayıt öznitelik sınıflarına tür örneği aracılığıyla geçirilir <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> . |
| DLL 'yi **PrivateAssemblies** dizinine yerleştirin. | Derlemeyi, dizinin **PrivateAssemblies** alt dizinine yerleştirin [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . **PrivateAssemblies** içinde bulunan derlemeler otomatik olarak algılanır, ancak **Başvuru Ekle** iletişim kutusunda görünmez. **PrivateAssemblies** ve **PublicAssemblies** arasındaki fark, **PublicAssemblies** içindeki derlemelerin **Başvuru Ekle** iletişim kutusunda numaralandırılmanızdır. "CodeBase/Private yükleme dizini" tekniğinin kullanılmasını tercih ediyorsanız, **PrivateAssemblies** dizinine yüklemeniz gerekir. |
| Tanımlayıcı adlı bütünleştirilmiş kod ve derleme kayıt defteri anahtarını kullanın. | Derleme anahtarı, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kesin bir adlandırılmış VSPackage derlemesini yüklemeye açıkça doğrudan yönlendirmek için kullanılabilir. Anahtarın değeri derlemenin tanımlayıcı adı olmalıdır. |
| DLL 'yi **PublicAssemblies** dizinine yerleştirin. | Son olarak, derleme ayrıca **PublicAssemblies** alt dizinine yerleştirilebilecek. **PublicAssemblies** içinde bulunan derlemeler otomatik olarak algılanır ve ' de **Başvuru Ekle** iletişim kutusunda da görünür [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .<br /><br /> VSPackage derlemeleri yalnızca, diğer VSPackage geliştiricileri tarafından yeniden kullanılması amaçlanan yönetilen bileşenleri içeriyorsa **PublicAssemblies** dizinine yerleştirilmelidir. Derlemelerin çoğunluğu bu ölçütü karşılamıyor. |

> [!NOTE]
> Tüm bağımlı derlemeleriniz için tanımlayıcı adlandırılmış ve imzalı derlemeler kullanın. Bu derlemelerin de kendi dizininizde veya genel derleme önbelleğinde (GAC) yüklü olması gerekir. Bu, zayıf ad bağlama olarak bilinen, aynı temel dosya adına sahip Derlemelerle çakışmalara karşı koruma sağlar.
