---
title: 'Nasıl yapılır: devre dışı bırakılmış bir VSTO eklentisini yeniden etkinleştirme'
description: Microsoft Office uygulamasında devre dışı bırakılmış bir VSTO eklentisini yeniden etkinleştirmek için Visual Studio 'Yu nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VST.Warning.DisabledAddIn
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- disabled add-ins
- add-ins [Office development in Visual Studio], disabled
- add-ins [Office development in Visual Studio], enabling
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: de3e251c15699ce29b7986e4f0cc19a3f5c5798d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942197"
---
# <a name="how-to-re-enable-a-vsto-add-in-that-has-been-disabled"></a>Nasıl yapılır: devre dışı bırakılmış bir VSTO eklentisini yeniden etkinleştirme
  Microsoft Office uygulamalar, beklenmedik şekilde davranan VSTO eklentilerini devre dışı bırakabilir. Bir uygulama, hata ayıklamaya çalıştığınızda VSTO eklentisini yüklemezse, uygulama, VSTO eklentisini devre dışı bırakmış veya geçici olarak devre dışı bırakmış olabilir.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="hard-disabled-vsto-add-ins"></a>Sabit devre dışı bırakılmış VSTO eklentileri
 Bir VSTO eklentisi uygulamanın beklenmedik şekilde kapatılmasına neden olduğunda, sabit devre dışı bırakma gerçekleşebilir. Ayrıca, <xref:Microsoft.Office.Tools.AddIn.Startup> VSTO eklentiinizdeki olay işleyicisi yürütülürken hata ayıklayıcıyı durdurursanız, geliştirme bilgisayarınızda da meydana gelebilir.

### <a name="to-re-enable-a-vsto-add-in"></a>VSTO eklentisini yeniden etkinleştirmek için

1. Uygulamada, **Dosya** sekmesine tıklayın.

2. *ApplicationName* **seçenekleri** düğmesine tıklayın.

3. Kategoriler bölmesinde, **Eklentiler**' i tıklatın.

4. Ayrıntılar bölmesinde, VSTO eklentisinin **devre dışı bırakılmış uygulama eklentileri** listesinde göründüğünü doğrulayın.

     **Ad** sütunu derlemenin adını belirtir ve **Location** sütunu uygulama bildiriminin tam yolunu belirtir.

5. **Yönet** kutusunda, **devre dışı öğeler**' i ve sonra **Git**' i tıklatın.

6. VSTO eklentisini seçin ve **Etkinleştir**' e tıklayın.

7. **Kapat**’a tıklayın.

## <a name="soft-disabled-vsto-add-ins"></a>Geçici olarak devre dışı VSTO eklentileri
 Bir VSTO eklentisi uygulamanın beklenmedik şekilde kapatılmasına neden olmayan bir hata ürettiğinden, geçici devre dışı bırakma gerçekleşebilir. Örneğin, bir uygulama, olay işleyicisi yürütülürken işlenmeyen bir özel durum oluşturursa, VSTO eklentisini geçici olarak devre dışı bırakabilir <xref:Microsoft.Office.Tools.AddIn.Startup> .

> [!NOTE]
> Geçici olarak devre dışı bırakılmış bir VSTO eklentisini yeniden etkinleştirdiğinizde, uygulama doğrudan VSTO eklentisini yüklemeye çalışır. İlk olarak uygulamanın, VSTO eklentisini geçici olarak devre dışı bırakmasına neden olan sorun düzeltilmediyse, uygulama VSTO eklentisini yeniden devre dışı bırakır.

### <a name="to-re-enable-a-vsto-add-in"></a>VSTO eklentisini yeniden etkinleştirmek için

1. Uygulamada, **Dosya** sekmesine tıklayın.

2. *ApplicationName* **seçenekleri** düğmesine tıklayın.

3. Kategoriler bölmesinde, **Eklentiler**' i tıklatın.

4. Ayrıntılar bölmesinde, VSTO eklentisinin **etkin olmayan uygulama eklentileri** listesinde göründüğünü doğrulayın.

     **Ad** sütunu derlemenin adını belirtir ve **Location** sütunu uygulama bildiriminin tam yolunu belirtir.

5. **Yönet** kutusunda, **com eklentileri**' ne ve ardından **Git**' e tıklayın.

6. **Com eklentileri** iletişim kutusunda, devre DıŞı bırakılmış VSTO eklentisinin yanındaki onay kutusunu işaretleyin.

7. **Tamam**'a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümleri oluşturma](../vsto/building-office-solutions.md)
- [Office projelerinde hata ayıklama](../vsto/debugging-office-projects.md)
- [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md)
