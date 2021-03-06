---
description: Grafik tanılama 'nın uygulama içi bileşeninin programlı denetimi için bir arabirim temsil eder.
title: VsgDbg sınıfı | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2bb3a9009c38da483b0792b89c115c2e8e9908eb
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232459"
---
# <a name="vsgdbg-class"></a>VsgDbg Sınıfı
Grafik tanılama 'nın uygulama içi bileşeninin programlı denetimi için bir arabirim temsil eder.

## <a name="syntax"></a>Syntax

```C++
class VsgDbg;
```

## <a name="members"></a>Üyeler
 `VsgDbg`Sınıfı aşağıdaki üyeleri destekler.

### <a name="public-constructors"></a>Ortak Oluşturucular

|Ad|Açıklama|
|----------|-----------------|
|[VsgDbg::VsgDbg (Oluşturucu)](vsgdbg-vsgdbg-constructor.md)|Sınıfının bir örneğini oluşturur `VsgDbg` ve isteğe bağlı olarak grafik tanılama 'nın uygulama içi bileşenini, grafik bilgilerini etkin bir şekilde yakalayıp kaydetmek üzere hazırlar.|
|[VsgDbg::~VsgDbg (Yok Edici)](vsgdbg-tilde-vsgdbg-destructor.md)|Sınıfının bir örneğini yok eder `VsgDbg` .|

### <a name="public-methods"></a>Ortak Yöntemler

|Ad|Açıklama|
|----------|-----------------|
|[AddMessage](addmessage.md)|Grafik tanılama HUD (baş ekran) için özel bir ileti ekler.|
|[BeginCapture](begincapture.md)|İle biten bir yakalama aralığı başlatır `EndCapture` .|
|[CaptureCurrentFrame](capturecurrentframe.md)|Geçerli çerçevenin kalan kısmını grafik günlük dosyasına yakalar.|
|[Kopyalama (Programlı Yakalama)](copy-programmatic-capture.md)|Etkin grafik günlüğü (. vsglog) dosyasının içeriğini yeni bir dosyaya kopyalar.|
|[EndCapture](endcapture.md)|İle başlatılan bir yakalama aralığını sonlandırır `BeginCapture` .|
|[Dengeleyici](init.md)|Grafik tanılama 'nın uygulama içi bileşenini, grafik bilgilerini etkin bir şekilde yakalamak ve kaydetmek üzere hazırlar.|
|[ToggleHUD](togglehud.md)|Grafik tanılama HUD kaplamasına açık veya kapalı olarak geçiş yapar.|
|[UnInit](uninit.md)|Grafik günlük dosyasını sonlandırır, kapatır ve uygulama grafik bilgilerini etkin bir şekilde kaydederken kullanılan kaynakları serbest bırakır.|

## <a name="remarks"></a>Açıklamalar
 `VsgDbg`Sınıfı, grafik Tanılama özelliklerini programlama yoluyla denetlemek için kullanabileceğiniz bir arabirimi temsil eder. Grafik bilgilerini etkin bir şekilde yakalamaktan ve kaydetmeseniz bile bazı özellikleri kullanabilirsiniz; Bu, `AddMessage` üye işlev ve `ToggleHUD` üye işlevini içerir. Diğer üye işlevleri grafik tanılama 'nın uygulama içi bileşenini, grafik bilgilerinin etkin bir şekilde yakalanması veya durdurulması için hazırlayın ya da uygulama etkin bir şekilde yakalayıp grafik bilgilerini bir grafik günlüğü dosyasına kaydederken çağrılmalıdır.
