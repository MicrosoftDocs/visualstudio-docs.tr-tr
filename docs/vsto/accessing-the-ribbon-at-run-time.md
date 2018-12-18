---
title: Şerit, çalışma zamanında erişme
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Globals class, Ribbon
- Ribbon [Office development in Visual Studio], accessing
- RibbonManager class
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9a20297ee0d60173cbd0513f3d34e12f12388bdb
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304629"
---
# <a name="access-the-ribbon-at-runtime"></a>Şerit, çalışma zamanında erişme
  Gösterme, gizleme ve Şerit değiştirme için kod yazma ve bir özel görev bölmesi, Eylemler bölmesi veya Outlook form bölgesi denetimlerinden kodu çalıştırmak kullanıcıları etkinleştirin.  

 Şerit kullanarak erişebileceğiniz `Globals` sınıfı. Outlook projeleri için belirli bir Outlook denetçisi veya Outlook Gezgini penceresinde görünür şeritler erişebilirsiniz.  

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  

## <a name="access-the-ribbon-by-using-the-globals-class"></a>Globals sınıfı kullanarak Şerit erişim  
 Kullanabileceğiniz `Globals` sınıfı bir belge düzeyi projesi veya VSTO eklenti projesinde bir Şerit dilediğiniz yerde erişmek için projedeki.  

 Hakkında daha fazla bilgi için `Globals` sınıfı [Office projelerindeki nesnelere genel erişim](../vsto/global-access-to-objects-in-office-projects.md).  

 Aşağıdaki örnekte `Globals` adlı özel bir Şerit erişmek için sınıf `Ribbon1` ve Şerit üzerindeki bir birleşik giriş kutusu üzerinde görüntülenen metni ayarlama `Hello World`.  

 [!code-vb[Trin_Outlook_FR_Access#4](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#4)]
 [!code-csharp[Trin_Outlook_FR_Access#4](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#4)]  

## <a name="access-a-collection-of-ribbons-that-appear-in-a-specific-outlook-inspector-window"></a>Belirli bir Outlook denetçisi penceresinde görünür şeritler koleksiyonunu erişim  
 Outlook'ta görünen Şerit koleksiyonunu erişebileceğiniz *denetçiler*. Bir denetçi kullanıcıların e-posta iletilerini oluşturmak gibi belirli görevleri gerçekleştirdiğinizde, Outlook'ta açılır penceredir. Şerit denetçisi penceresinin ulaşmak için `Ribbons` özelliği `Globals` geçirin ve sınıfı bir <xref:Microsoft.Office.Interop.Outlook.Inspector> Inspector'ı temsil eden nesne.  

 Aşağıdaki örnekte, o anda odağı içeren denetçisi Şerit koleksiyonunu alır. Bu örnek adlı bir Şerit ardından erişen `Ribbon1` ve Şerit üzerindeki bir birleşik giriş kutusu üzerinde görüntülenen metnin ayarlar `Hello World`.  

 [!code-vb[Trin_Outlook_FR_Access#5](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#5)]
 [!code-csharp[Trin_Outlook_FR_Access#5](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#5)]  

## <a name="access-a-collection-of-ribbons-that-appear-for-a-specific-outlook-explorer"></a>Bir koleksiyon için belirli bir Outlook Gezgini görünen Şerit erişim  
 Bir koleksiyon bir Outlook'ta görünen Şerit erişebileceğiniz *Gezgini*. Bir Gezgin Outlook örneği için ana uygulama kullanıcı arabirimi (UI) ' dir. Bir Gezgin penceresi Şerit ulaşmak için `Ribbons` özelliği `Globals` geçirin ve sınıfı bir <xref:Microsoft.Office.Interop.Outlook.Explorer> Gezgini temsil eden nesne.  

 Aşağıdaki örnekte, o anda odağı içeren Gezgini Şerit koleksiyonunu alır. Bu örnek adlı bir Şerit ardından erişen `Ribbon1` ve Şerit üzerindeki bir birleşik giriş kutusu üzerinde görüntülenen metnin ayarlar `Hello World`.  

 [!code-vb[Trin_Outlook_FR_Access#6](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#6)]
 [!code-csharp[Trin_Outlook_FR_Access#6](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#6)]  

## <a name="see-also"></a>Ayrıca bkz.  
 [Şerite Genel Bakış](../vsto/ribbon-overview.md)   
 [Şerit Tasarımcısı](../vsto/ribbon-designer.md)   
 [Şerit XML](../vsto/ribbon-xml.md)   
 [Şerit nesne modeline genel bakış](../vsto/ribbon-object-model-overview.md)   
 [İzlenecek yol: Şerit Tasarımcısını kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [İzlenecek yol: çalışma zamanında Şerit denetimlerini güncelleştirme](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Outlook için Şerit özelleştirme](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Form bölgesine çalışma zamanında erişme](../vsto/accessing-a-form-region-at-run-time.md)  
