---
title: VS kabuğuna VSPackage dosya konumunu belirtme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 63948a464a43284f3b9205d185e4b0a4e39155e4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49856242"
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>VS Kabuğuna VSPackage Dosya Konumunu Belirtme
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage'ı yüklemek için DLL derlemeyi bulabilir olması gerekir. Bunun çeşitli yollarla aşağıdaki tabloda açıklandığı gibi bulabilirsiniz.  


| Yöntem | Açıklama |
| - | - |
| Kod temeli kayıt defteri anahtarı kullanın. | Kod temeli anahtar yönlendirmek için kullanılabilir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] herhangi bir tam dosya yolundan VSPackage derlemesi yüklenemiyor. Anahtarın değeri, DLL dosyasının yolu olmalıdır. Bu sahip için en iyi yoludur [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , paket derlemesi yüklenemiyor. Bu teknik bazen "CodeBase/özel yükleme dizini teknik." adlandırılır Kayıt sırasında kod tabanının değeri kayıt öznitelik sınıfları bir örneği üzerinden geçirilir <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> türü. |
| DLL içine yerleştirin **PrivateAssemblies** dizin. | Derlemede yerleştirin **PrivateAssemblies** alt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dizin. Derlemeleri bulunan **PrivateAssemblies** otomatik olarak algılanır ancak görünmez **Add References** iletişim kutusu. Arasındaki fark **PrivateAssemblies** ve **Publicassembly'ler** derlemelere olan içinde **Publicassembly'ler** listelenen **başvuruları ekleme**  iletişim kutusu. "CodeBase/özel yükleme dizini" teknik kullanmayı seçtiğiniz sonra içine yüklemelisiniz **PrivateAssemblies** dizin. |
| Tanımlayıcı adlı bütünleştirilmiş kod ve derleme kayıt defteri anahtarını kullanın. | Derleme anahtar açıkça yönlendirmek için kullanılabilir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage derleme adında güçlü yüklenemedi. Anahtarın değeri, derlemenin tanımlayıcı adı olmalıdır. |
| DLL içine yerleştirin **Publicassembly'ler** dizin. | Son olarak, derlemeyi ayrıca içine yerleştirilebilir **Publicassembly'ler** alt. Derlemeleri bulunan **Publicassembly'ler** otomatik olarak algılanır ve ayrıca görünür **Add References** iletişim kutusunda [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].<br /><br /> VSPackage derlemeler yalnızca yerleştirilmelidir **Publicassembly'ler** bunlar içeriyorsa, dizin yönetilen bileşenlerin diğer VSPackage geliştiriciler tarafından kullanılabilmeleri için tasarlanmıştır. Çoğu derleme, bu ölçütü karşılamıyor. |

> [!NOTE]
>  Tanımlayıcı adlı, imzalı derlemeler tüm bağımlı bütünleştirilmiş kodlarınızı için kullanın. Bu derlemeler de dizininizin veya genel derleme önbelleği (GAC) yüklenmesi gerekir. Bu, zayıf adı bağlaması olarak bilinen aynı temel dosya adı olan derlemeler çakışıyor karşı korur.