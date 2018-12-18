---
title: MSBuild koşulları | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, conditions
- conditions [MSBuild]
ms.assetid: 9d7aa308-b667-48ed-b4c9-a61e49eb0a85
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba55fca6e34cb93af257f32f33df7b7b8c6d6045
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49286318"
---
# <a name="msbuild-conditions"></a>MSBuild Koşulları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] olabilir koşulları belirli bir kümesini destekler yerde uygulanan bir `Condition` özniteliğine izin verilir. Aşağıdaki tabloda, bu koşullar açıklanmaktadır.  
  
|Koşul|Açıklama|  
|---------------|-----------------|  
|'`stringA`' == '`stringB`'|Değerlendiren `true` varsa `stringA` eşittir `stringB`.<br /><br /> Örneğin:<br /><br /> `Condition="'$(CONFIG)'=='DEBUG'"`<br /><br /> Basit alfasayısal dize veya Boole değerleri için tırnak gerekmez. Ancak, tek tırnak, boş değerler için gereklidir.|  
|'`stringA`' != '`stringB`'|Değerlendiren `true` varsa `stringA` eşit değildir `stringB`.<br /><br /> Örneğin:<br /><br /> `Condition="'$(CONFIG)'!='DEBUG'"`<br /><br /> Basit alfasayısal dize veya Boole değerleri için tırnak gerekmez. Ancak, tek tırnak, boş değerler için gereklidir.|  
|\<, >, \<=, >=|Sayısal değerlerin işlenenden değerlendirir. Döndürür `true` ilişkisel değerlendirme doğru olması durumunda. İşlenen, bir ondalık ya da onaltılık sayı değerlendirmelidir. Onaltılık sayılar "0 x" başlaması gerekir. **Not:** XML'de karakterleri `<` ve `>` kaçış karakterleri eklenmelidir. Simgenin `<` olarak temsil edilir `<`. Simgenin `>` olarak temsil edilir `>`.|  
|Var ('`stringA`')|Değerlendiren `true` bir dosya veya klasör adıyla `stringA` bulunmaktadır.<br /><br /> Örneğin:<br /><br /> `Condition="!Exists('$(builtdir)')"`<br /><br /> Basit alfasayısal dize veya Boole değerleri için tırnak gerekmez. Ancak, tek tırnak, boş değerler için gereklidir.|  
|HasTrailingSlash ('`stringA`')|Değerlendiren `true` ya da arkaya eğik belirtilen dizeyi içerip içermediğini (\\) veya İleri eğik çizgi (/) karakteri.<br /><br /> Örneğin:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Basit alfasayısal dize veya Boole değerleri için tırnak gerekmez. Ancak, tek tırnak, boş değerler için gereklidir.|  
|!|Değerlendiren `true` işlenen değerlendirilirse `false`.|  
|ve|Değerlendiren `true` her iki işlenen de sonucunu verirse `true`.|  
|Veya|Değerlendiren `true` en az bir işlenen değerlendirilirse `true`.|  
|()|Değerlendiren mekanizması gruplandırma `true` ifadeler içinde yer alan sonucunu verirse `true`.|  
|(% ifade %) $if$ $başka$, $endif$|Denetler olup belirtilen `%expression%` geçirilen özel bir şablon parametresinin dize değeri eşler. Varsa `$if$` değerlendirilen koşul `true`, kendi deyimleri sonra çalışır; Aksi halde, `$else$` koşul denetlenir. Varsa `$else$` koşul `true`, kendi deyimleri sonra çalışır; Aksi halde, `$endif$` koşul ifade değerlendirme sona erer.<br /><br /> Kullanım örnekleri için bkz: [Visual Studio Proje/öğe şablon parametre mantıksal](http://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic).|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [MSBuild başvurusu](../msbuild/msbuild-reference.md)   
 [Koşullu yapılar](../msbuild/msbuild-conditional-constructs.md)   
 [İzlenecek Yol: Sıfırdan MSBuild Proje Dosyası Oluşturma](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)



