---
title: Proje şablonu ve öğe şablonu yüklenirken sorun giderme
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: troubleshooting
helpviewer_keywords:
- templates [Visual Studio], troubleshooting
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 2963bdbd4f788f6321d963bc52001f1875c48a14
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53061875"
---
# <a name="how-to-troubleshoot-templates"></a>Nasıl yapılır: şablonlarda sorun giderme

Geliştirme ortamında yüklemek bir şablon başarısız olursa, sorunu bulmak için birkaç yolu vardır.

## <a name="validate-the-vstemplate-file"></a>Vstemplate dosyası doğrula

Varsa *vstemplate* şablon dosyasında için Visual Studio şablon şeması uyması değil, şablon görüntülenmeyebilir **yeni proje** iletişim kutusu.

### <a name="to-validate-the-vstemplate-file"></a>Vstemplate dosyası doğrulamak için

1. Bulun *.zip* şablonu içeren dosya.

1. Ayıklama *.zip* dosya.

1. Üzerinde **dosya** Visual Studio menüsünde **açık** > **dosya**.

1. Seçin *vstemplate* dosya şablonu ve seçin **açık**.

1. Doğrulayın, XML *vstemplate* dosyası için şablon şeması uyar. Daha fazla bilgi için *vstemplate* şema bakın [şablon şeması başvurusu](../extensibility/visual-studio-template-schema-reference.md).

    > [!NOTE]
    > Geliştirme sırasında IntelliSense desteği almak için *vstemplate* ekleyin bir `xmlns` özniteliğini `VSTemplate` öğesini ve değerini atayın http://schemas.microsoft.com/developer/vstemplate/2005.

1. Kaydet ve Kapat *vstemplate* dosya.

1. Şablonunuzda, içerdiği dosyaları seçin, sağ tıklatın ve seçin **göndermek** > **sıkıştırılmış (daraltılmış) klasör**. Seçtiğiniz dosyalar sıkıştırılmadan bir *.zip* dosya.

1. Yeni yerleştirin *.zip* eski ile aynı dizinde dosya *.zip* dosya.

1. Ayıklanan şablon dosyalarını ve eski şablonu silmek *.zip* dosya.

## <a name="enable-diagnostic-logging"></a>Tanılama günlüğünü etkinleştirme

İçindeki adımları izleyerek, şablon keşfi için tanılama günlük kaydını etkinleştirebilirsiniz [sorun giderme şablon bulma (genişletilebilirlik)](../extensibility/troubleshooting-template-discovery.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Şablon bulma (genişletilebilirlik) sorunlarını giderme](../extensibility/troubleshooting-template-discovery.md)
- [Şablonları özelleştirme](../ide/customizing-project-and-item-templates.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)