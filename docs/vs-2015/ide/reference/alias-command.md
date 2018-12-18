---
title: Diğer ad komutu | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- tools.alias
helpviewer_keywords:
- aliases, Visual Studio commands
- commands, aliases
- Tools.Alias command
- command aliases
- alias command
ms.assetid: bdf857df-b5d5-450f-8c10-a6fd4dccc130
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f9fb6a4da0b18cf022ee388ff4a6fa5f399dc650
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49258524"
---
# <a name="alias-command"></a>Diğer Ad Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Tam komut, tam komut ve bağımsız değişkenler için yeni bir diğer ad veya başka bir diğer ad oluşturur.  
  
> [!TIP]
>  Yazarak `>alias` herhangi bir bağımsız değişken görüntüler olmadan geçerli diğer adlar ve tanımlarının listesi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]  
```  
  
## <a name="arguments"></a>Arguments  
 `aliasname`  
 İsteğe bağlı. Yeni diğer adı. İçin herhangi bir değer sağlanmazsa `aliasname`, geçerli diğer adlar ve tanımlarının bir listesi görüntülenir.  
  
 `aliasstring`  
 İsteğe bağlı. Tam komu adı veya mevcut bir diğer ad ve bir diğer ad olarak oluşturmak istediğiniz herhangi bir parametre. İçin herhangi bir değer sağlanmazsa `aliasstring`, belirtilen diğer ad görüntüler için diğer ad ve diğer ad dizesi.  
  
## <a name="switches"></a>Anahtarlar  
 / DELETE veya/DEL veya /d  
 İsteğe bağlı. Otomatik tamamlamadan kaldırarak belirtilen diğer adları siler.  
  
 Reset  
 İsteğe bağlı. Önceden tanımlanmış diğer adlar listesini özgün ayarlarına sıfırlar. Diğer bir deyişle, önceden tanımlanmış tüm diğer adları geri yükler ve kullanıcı tarafından tanımlanan tüm diğer adları kaldırır.  
  
## <a name="remarks"></a>Açıklamalar  
 Diğer adlar komutları temsil ettiğinden, komut satırının başında bulunmaları gerekir.  
  
 Bu komut yayınlanırken, diğer adlardan sonra değil komutun hemen sonrasına anahtarları içermelidir, aksi takdirde anahtar diğer ad dizesinin bir parçası olarak dahil edilir.  
  
 `/reset` Anahtarı diğer adlar geri yüklenmeden önce bir onay ister. İn bir kısa biçimi yoktur `/reset`.  
  
## <a name="examples"></a>Örnekler  
 Bu örnek, yeni bir diğer ad oluşturur `upper`, tam komut Edit.MakeUpperCase için.  
  
```  
>Tools.Alias upper Edit.MakeUpperCase  
```  
  
 Bu örnek, diğer adını siler `upper`.  
  
```  
>Tools.alias /delete upper  
```  
  
 Bu örnek, tüm geçerli diğer adlar ve açıklamalarının bir listesini görüntüler.  
  
```  
>Tools.Alias  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)   
 [Komut penceresi](../../ide/reference/command-window.md)   
 [Bul/komut kutusu](../../ide/find-command-box.md)   
 [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)



