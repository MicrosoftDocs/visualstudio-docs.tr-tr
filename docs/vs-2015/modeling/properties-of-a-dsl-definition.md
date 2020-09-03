---
title: DSL tanımının özellikleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
ms.assetid: 38debcfe-e1a6-4a3f-9d69-3ab07520f2b6
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8755b1b70051c54157fa87ee0b66dbc9340b5024
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668460"
---
# <a name="properties-of-a-dsl-definition"></a>DSL Tanımının Özellikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DslDefinition özellikleri, sürüm numaralandırması gibi, *etki alanına özgü dil* tanımı özelliklerini tanımlar. *Alana özgü dil Tasarımcısı*diyagramın açık bir alanına tıkladığınızda DslDefinition özellikleri **Özellikler** penceresinde görünür.

 Daha fazla bilgi için bkz. [etki alanına özgü dil tanımlama](../modeling/how-to-define-a-domain-specific-language.md). Bu özelliklerin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [etki alanına özgü dili özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

 DslDefinition aşağıdaki tabloda bulunan özelliklere sahiptir:

|Özellik|Açıklama|Varsayılan|
|--------------|-----------------|-------------|
|Erişim değiştiricisi|Etki alanı sınıfına ait erişim değiştiricisinin public veya internal olduğunu belirler.|public|
|Özel Öznitelikler|Alan sınıfı için özel tanımlanmış öznitelikler.<br /><br /> **Göz önünde** Bir öznitelik eklemek için tarayıcı düğmesini kullanın.|\<none>|
|Şirket Adı|Sistem kayıt defterindeki geçerli şirket adının adı.|Geçerli şirket adı|
|Name|Bu alan sınıfının adı.|Geçerli ad|
|Ad Alanı|Bu alan sınıfıyla ilişkili ad alanı.|Geçerli ad alanı|
|Paket GUID 'Si|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Bu DSL için oluşturulan paketin GUID 'i.|\<none>|
|Paket ad alanı|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Bu DSL için oluşturulan paketin ad alanı.|\<none>|
|Ürün Adı|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Bu DSL için oluşturulan paket için kaydedilecek ürünün adı.|\<none>|
|Notlar|Bu alan sınıfıyla ilişkili notlar.|\<none>|
|Description|Bu alan sınıfı için açıklama.|\<none>|
|Görünen Ad|Bu alan sınıfı için oluşturulan tasarımcıda görüntülenecek ad.|\<none>|
|Help anahtar sözcüğü|Bu alan sınıfıyla ilişkili Yardım anahtar sözcüğü.|\<none>|
|Oluşturma|Bu etki alanına özgü dil tanımı için Artımlı derleme numarası.|0|
|Ana Sürüm|Bu etki alanına özgü dil tanımı için artımlı ana derleme numarası.|1|
|Alt Sürüm|Bu etki alanına özgü dil tanımı için artımlı küçük derleme numarası.|0|
|Revizyon|Bu etki alanına özgü dil tanımı için artımlı düzeltme derleme numarası.|0|

## <a name="see-also"></a>Ayrıca Bkz.
 [Alana Özgü Dil Araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
