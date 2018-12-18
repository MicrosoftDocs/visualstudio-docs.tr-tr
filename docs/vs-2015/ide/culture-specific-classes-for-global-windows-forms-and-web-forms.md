---
title: Genel Windows Formları ve Web formları için kültüre özgü sınıflar | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- globalization [Windows Forms], classes
- Web applications [.NET Framework], globalization
- culture, culture-specific classes
- numbers, international
- localization [Windows Forms], classes
- globalization [Visual Studio], culture-specific classes
- Windows Forms, localization
- international applications [Visual Studio], data formats
- time [Visual Studio], international
- dates [Visual Studio], international
- culture
- international characters
- currency formats
- ASP.NET, globalization
- classes [Visual Studio], culture-specific
- localization [Visual Studio], culture-specific classes
ms.assetid: 0d06a0a4-f887-4f7c-bde7-1d543c06f803
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bbd599864cfd1e5af770ab4305380d10c71b622a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49283302"
---
# <a name="culture-specific-classes-for-global-windows-forms-and-web-forms"></a>Genel Windows Formları ve Web Formları İçin Kültüre Özgü Sınıflar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Her bir kültürün tarih, zaman, sayı, para birimi ve diğer bilgileri görüntülemek için farklı kurallara sahiptir. <xref:System.Globalization> Ad alanı, kültüre özgü değerlerini değiştirmek için kullanılan sınıfları içerir, gibi görüntüleneceğini <xref:System.Globalization.DateTimeFormatInfo>, **Takvim**, ve <xref:System.Globalization.NumberFormatInfo>.  
  
## <a name="using-the-culture-setting"></a>Kültür ayarı kullanma  
 Ancak çoğu uygulama veya depolanan kültür ayarı kullanacağınız zaman **Bölgesel Seçenekler** otomatik olarak çalışma zamanında kuralları belirlemek ve bilgileri biçimlendirebilmek için Denetim Masası'nı tıklatın,. Kültürü ayarlama hakkında daha fazla bilgi için bkz [nasıl yapılır: Windows Forms Genelleştirme için UI kültürü ve kültüre ayarlayın](http://msdn.microsoft.com/en-us/694e049f-0b91-474a-9789-d35124f248f0) veya [nasıl yapılır: ASP.NET Web sayfası Genelleştirme için kültürü ve kullanıcı Arabirimi kültürünü ayarlama](http://msdn.microsoft.com/library/76091f86-f967-4687-a40f-de87bd8cc9a0). Kültüre özgü bilgileri kültür ayarı göre otomatik olarak Biçimlendir sınıfları çağrılır. Kültüre özgü bazı yöntemler <xref:System.IFormattable.ToString%2A?displayProperty=fullName>, <xref:System.Console.WriteLine%2A?displayProperty=fullName>, ve <xref:System.String.Format%2A?displayProperty=fullName>. Bazı kültüre özgü işlevleri (Visual Basic dilindeki) `MonthName` ve `WeekDayName`.  
  
 Örneğin, aşağıdaki kod nasıl kullanabileceğinizi gösterir. <xref:System.IFormattable.ToString%2A> biçimi para birimi bir yönteme geçerli kültür için:  
  
```vb  
' Put the Imports statements at the beginning of the code module  
Imports System.Threading  
Imports System.Globalization  
' Display a number with the culture-specific currency formatting  
Dim MyInt As Integer = 100  
Console.WriteLine(MyInt.ToString("C", Thread.CurrentThread.CurrentCulture))  
  
```  
  
```csharp  
// Put the using statements at the beginning of the code module  
using System.Threading;  
using System.Globalization;  
// Display a number with the culture-specific currency formatting  
int myInt = 100;  
Console.WriteLine(myInt.ToString("C", Thread.CurrentThread.CurrentCulture));  
```  
  
 Kültür, "fr-FR" olarak ayarlanırsa çıktı penceresinde şunu görürsünüz:  
  
 `100,00`  
  
 Kültürü "en-US" olarak ayarlanırsa çıktı penceresinde şunu görürsünüz:  
  
 `$100.00`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IFormattable.ToString%2A?displayProperty=fullName>   
 <xref:System.Globalization.DateTimeFormatInfo>   
 <xref:System.Globalization.NumberFormatInfo>   
 <xref:System.Globalization.Calendar>   
 <xref:System.Console.WriteLine%2A?displayProperty=fullName>   
 <xref:System.String.Format%2A?displayProperty=fullName>   
 [Uygulamaları Genelleştirme ve Yerelleştirme](../ide/globalizing-and-localizing-applications.md)

