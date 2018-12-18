---
title: 'Hata: Transact-SQL yürütmesi hata ayıklama olmadan bitti | Microsoft Docs'
ms.custom: ''
ms.date: 11/08/2018
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.sqlde_sql_executed_but_not_debugged
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0efb83f6b6cbebc255f6f47c30e3934d74de7870
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349013"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Hata: Transact-SQL yürütmesi hata ayıklaması yapılmadan sonlandı

SQLCLR yordam ya da Transact-SQL hata ayıklama çalıştığınız ve hata ayıklayıcı hata ayıklama iletilerini SQL Server'dan almaz. Bu hata oluşur.  
  
SQL Server'da sorunları veya ağ sorunları nedeniyle bu bir sorun olabilir, ancak en olası nedeni izinlerle ilgili bir sorun.  
  
Kullanılan iki hesap vardır:  
  
- Kullanıcı hesabı uygulama hesabıdır [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] olarak çalışıyor.  
  
- Bağlantı hesabı SQL Server'a bağlantı kurmak için kullanılan kimliktir. Bu hesap mutlaka bağlantı SQL kimlik doğrulaması kullanıyorsanız gibi Visual Studio çalıştıran kimliğin ile aynı değildir.  
  
  SQL hata ayıklama, uygulama hesabı bağlantı hesapla eşleşmesi gerekir veya sysadmin olmanız gerekir.  
  
  SQL hesabı adları gibi sa kullanıyorsanız, uygulama hesabının SQL Server'da sysadmin olarak ayarlanması gerekir. Varsayılan olarak, SQL server çalıştıran makinede SQL Server Sistem yöneticilerdir.  
  
  Bu hatayı düzeltmek için ihtiyacınız olabilecek:  
  
  - İzinleri ayarlarınızı doğrulayın. Daha fazla bilgi için [nasıl yapılır: hata ayıklama için SQL Server izinleri ayarlayın](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
  - SQL hata ayıklamayı'ı doğru bir şekilde ayarlandığından emin olun.  
  
  - Ağ veya veritabanı yöneticinize başvurun.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [SQL hata ayıklamayı kurma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))
- [Nasıl yapılır: hata ayıklama için SQL Server izinleri ayarla](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [Hata Ayıklayıcısı Ayarları ve Hazırlığı](../debugger/debugger-settings-and-preparation.md)
- [Uzaktan Hata Ayıklama](../debugger/remote-debugging.md)