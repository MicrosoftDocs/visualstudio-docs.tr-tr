---
title: '&lt;Signature &gt; öğesi (ClickOnce dağıtımı) | Microsoft Docs'
description: Imza öğesi, bu dağıtım bildirimini dijital olarak imzalamak için gereken bilgileri içerir. Dağıtım bildirimini imzalama isteğe bağlıdır, ancak önerilir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <Signature> element [ClickOnce deployment manifest]
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b7a86236087bdbff8cf82ca4821573f9f799d019
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349288"
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>&lt;Signature &gt; öğesi (ClickOnce dağıtımı)
Bu dağıtım bildirimini dijital olarak imzalamak için gereken bilgileri içerir.

## <a name="syntax"></a>Syntax

```xml

<Signature> 
   XML signature information 
</Signature>
```

## <a name="remarks"></a>Açıklamalar
 Bir zarf imzasını kullanarak bir dağıtım bildirimini imzalama isteğe bağlıdır, ancak önerilir. XML dosyalarını imzalama hakkında daha fazla bilgi için, bkz. "XML-Signature sözdizimi ve Işleme" başlıklı World Wide Web Konsorsiyumu önerisi [http://www.w3.org/TR/xmldsig-core/](https://www.w3.org/TR/xmldsig-core/) .

 Bildiriminizi imzalamak istiyorsanız tüm dosyalar için karmaların sağlanması gerekir. Karma olmayan dosyaları olan bir bildirim, kullanıcılar karma olmayan dosyaların içeriğini doğrulayamadığından imzalanamıyor.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, bir `Signature` dağıtımda kullanılan bir dağıtım bildiriminde bir öğe gösterir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

```xml
<Signature xmlns="http://www.w3.org/2000/09/xmldsig#">
  <SignedInfo>
    <CanonicalizationMethod Algorithm=
           "http://www.w3.org/TR/2001/REC-xml-c14n-20010315" />
    <SignatureMethod Algorithm=
           "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />
    <Reference URI="">
      <Transforms>
        <Transform Algorithm=
           "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />
      </Transforms>
      <DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
      <DigestValue>d2z5AE...</DigestValue>
    </Reference>
  </SignedInfo>
  <SignatureValue>
4PHj6SaopoLp...
  </SignatureValue>
  <KeyInfo>
    <X509Data>
      <X509Certificate>
MIIHnTCCBoWgAwIBAgIKJY9+nwAHAAB...
      </X509Certificate>
    </X509Data>
  </KeyInfo>
</Signature>
```

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce dağıtım bildirimi](../deployment/clickonce-deployment-manifest.md)
