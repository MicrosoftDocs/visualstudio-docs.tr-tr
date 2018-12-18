---
title: Örnek Proje Birim testleri oluşturmak için | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- unit test sample [Visual Studio]
- unit tests, samples
ms.assetid: db80aaf2-0652-4d3f-a8c5-2a98fd8502a2
caps.latest.revision: 32
ms.author: gewarren
manager: douge
ms.openlocfilehash: c3d364ffe23e79bb8842770bec0602d4bb7022c9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49248592"
---
# <a name="sample-project-for-creating-unit-tests"></a>Birim Testleri Oluşturmak için Örnek Proje
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu örnek kod aşağıdaki izlenecek yollardaki kullanım için sağlanır:  
  
-   [İzlenecek yol: Oluşturma ve çalıştırma için birim testleri yönetilen kodu](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md). Bu izlenecek yol, oluşturma ve birim testlerini özelleştirme, bunları çalıştırmak ve test sonuçları inceleyin adımlarında size yol gösterir.  
  
-   [İzlenecek yol: Testleri çalıştırmak ve kod kapsamı görüntülemek](http://msdn.microsoft.com/en-us/d4aab8e2-2140-4975-b4e3-41ef3fa944c8). Bu kılavuz edilmekte olan proje kodunuzun oranını gösteren kod kapsamı verilerini görüntülemek nasıl gösterir.  
  
-   [İzlenecek yol: komut satırı test yardımcı programını kullanarak](http://msdn.microsoft.com/library/52c11992-9e94-4067-a4b7-59f19d69d867). Bu kılavuzda, testleri çalıştırmak ve sonuçları görüntülemek için MSTest.exe komut satırı yardımcı programını kullanın.  
  
## <a name="sample-code"></a>Örnek kod  
 Bu örnekte yalnızca kasıtlı hata içinde banka yöntemi "m_balance += amount" bir artı eşittir işareti önce oturum eksi gerektiğidir.  
  
```  
using System;   
  
namespace BankAccountNS  
{  
    /// <summary>   
    /// Bank Account demo class.   
    /// </summary>   
    public class BankAccount  
    {  
        private string m_customerName;  
  
        private double m_balance;  
  
        private bool m_frozen = false;  
  
        private BankAccount()  
        {  
        }  
  
        public BankAccount(string customerName, double balance)  
        {  
            m_customerName = customerName;  
            m_balance = balance;  
        }  
  
        public string CustomerName  
        {  
            get { return m_customerName; }  
        }  
  
        public double Balance  
        {  
            get { return m_balance; }  
        }  
  
        public void Debit(double amount)  
        {  
            if (m_frozen)  
            {  
                throw new Exception("Account frozen");  
            }  
  
            if (amount > m_balance)  
            {  
                throw new ArgumentOutOfRangeException("amount");  
            }  
  
            if (amount < 0)  
            {  
                throw new ArgumentOutOfRangeException("amount");  
            }  
  
            m_balance += amount; // intentionally incorrect code  
        }  
  
        public void Credit(double amount)  
        {  
            if (m_frozen)  
            {  
                throw new Exception("Account frozen");  
            }  
  
            if (amount < 0)  
            {  
                throw new ArgumentOutOfRangeException("amount");  
            }  
  
            m_balance += amount;  
        }  
  
        private void FreezeAccount()  
        {  
            m_frozen = true;  
        }  
  
        private void UnfreezeAccount()  
        {  
            m_frozen = false;  
        }  
  
        public static void Main()  
        {  
            BankAccount ba = new BankAccount("Mr. Bryan Walton", 11.99);   
  
            ba.Credit(5.77);  
            ba.Debit(11.22);  
            Console.WriteLine("Current balance is ${0}", ba.Balance);  
        }  
  
    }  
}  
```  
  
 / * Örnek şirketler, kuruluşlar, ürünler, etki alanı adları, e-posta adresleri, logolar, kişiler, yerler ve sahiplerinin hayal ürünüdür.  Gerçek şirket, kuruluş, ürün, etki alanı adı, e-posta adresi, logo, kişi, yer veya olayları ile hiçbir ilişki amaçlanmamıştır veya çıkarılmamalıdır. \*/  
  
## <a name="working-with-the-code"></a>Kod ile çalışma  
 Bu kod ile çalışmak için önce içinde bir proje oluşturmak olması [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. "İzlenecek yolu hazırlayın" bölümündeki adımları [izlenecek yol: yönetilen kod için birim testleri oluşturma ve çalıştırma](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen kod için birim testleri izlenecek yol: Oluşturma ve çalıştırma](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)   
 [İzlenecek yol: testleri çalıştırmak ve kod kapsamı görüntüleyin](http://msdn.microsoft.com/en-us/d4aab8e2-2140-4975-b4e3-41ef3fa944c8)   
 [İzlenecek yol: komut satırı test yardımcı programını kullanma](http://msdn.microsoft.com/library/52c11992-9e94-4067-a4b7-59f19d69d867)



