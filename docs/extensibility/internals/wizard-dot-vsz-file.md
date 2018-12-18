---
title: Sihirbazı'nı (. Vsz) dosya | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b0076e1ee7409486a3b7b86ccd0f46bcd02a54a5
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757889"
---
# <a name="wizard-vsz-file"></a>Sihirbaz (.Vsz) Dosyası

Tümleşik geliştirme ortamı (IDE) .vsz dosyaları sihirbazları başlatmak için kullanır. Bu .vsz dosyaları IDE çağırmak için hangi Sihirbazı belirlemek için kullandığı bilgileri ve sihirbaza geçirmek için hangi bilgilerini içerir.

.Vsz dosyası, hiçbir bölümleri içeren bir .ini biçimli metin dosyası bir sürümüdür. Bilgiler IDE bilinen dosyasının başında depolanır. Bu, IDE çağırır Sihirbazı'nı ve IDE geçirilecek .vsz dosyasındaki parametreler arasında bir bağlantı sağlar. Dosyanın kalanını sihirbaza özeldir ve IDE tarafından toplanacak olan ve belirli Sihirbazı'nı geçirilen parametre sağlar.

Aşağıdaki örnek .vsz dosyası içeriğini gösterir.

```
VSWizard 8.0
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}
Param="WIZARDNAME = Wizard One"
Param="WIZARDUI = FALSE"
```

.Vsz dosyası bölümlerinde aşağıda verilmiştir.

|Bölümü|Açıklama|
|----------|-----------------|
|VSWizard|Dosyasında ilk parametresi şablon dosya biçimi sürüm sayısıdır. Bu sürüm numarası 6.0, 7.0, 7.1 veya 8.0 olması gerekir. Diğer sayılar başlatılamıyor ve biçimi geçersiz hataya neden.|
|Sihirbazı|Bu alan OLE ProgID Sihirbazı'nın veya alternatif olarak tarafından IDE cocreated Sihirbazı'nı CLSID GUID dize gösterimini içerir.|
|Param|Bu bölümleri isteğe bağlıdır. Kadar gerekli ekleyebilirsiniz.|

Parametreler sihirbaz için ek özel parametreleri geçirmek .vsz dosyası etkinleştirin. Her değer varsayılan olarak, Sihirbazı bir dizi çeşitleri dize öğesinde olarak geçirilir. Daha fazla bilgi için bkz: [özel parametreler](../../extensibility/internals/custom-parameters.md).

.Vsz dosyanıza varsayılan yerel ayar kimliği eklemek için belirtmeniz `FALLBACK_LCID`= xxxx, xxxx olmak üzere yerel ayar kimliği, örneğin, İngilizce için 1033. Zaman `FALLBACK_LCID` parametresi tanımlanır, geçerli kimlik bulunmazsa sihirbaz sağlanan geri dönüş yerel ayar kimliği kullanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Parametreler](../../extensibility/internals/custom-parameters.md)
- [Sihirbazlar](../../extensibility/internals/wizards.md)
- [Şablon Dizin Açıklaması (.Vsdir) Dosyaları](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)