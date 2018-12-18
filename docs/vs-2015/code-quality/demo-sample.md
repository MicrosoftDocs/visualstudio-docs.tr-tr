---
title: Örnek Tanıtım | Microsoft Docs
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
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2ca480078bf269e8af662d94910a5d337c13bcd8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51722381"
---
# <a name="demo-sample"></a>Gösterim Örneği
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu prosedürler için örnek oluşturma işlemi gösterilmektedir [izlenecek yol: C/C++ kodunu analiz etme hataları](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md). Yordamlar oluşturun:  
  
- A [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] CppDemo adlı çözüm.  
  
- CodeDefects adlı bir statik kitaplık projesi oluşturun.  
  
- Statik kitaplık projesi ek açıklamaları adı.  
  
  Yordamlar kodu statik kitaplıklar için üst bilgi ve .cpp dosyaları için de sağlar.  
  
### <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>CppDemo çözüm ve CodeDefects proje oluşturma  
  
1.  Tıklayın **dosya** menüsünde **yeni**ve ardından **yeni proje**.  
  
2.  İçinde **proje türleri** ağaç listesi, Visual C++ varsayılan dilinizi vs'de değilse genişletin **diğer diller**.  
  
3.  Genişletin **Visual C++** ve ardından **genel**.  
  
4.  İçinde **şablonları**, tıklayın **boş proje**.  
  
5.  İçinde **adı** metin kutusunda, **CodeDefects**.  
  
6.  Seçin **çözüm için dizin oluştur** onay kutusu.  
  
7.  İçinde **çözüm adı** metin kutusunda, **CppDemo**.  
  
### <a name="configure-the-codedefects-project-as-a-static-library"></a>Statik kitaplık olarak CodeDefects proje yapılandırma  
  
1.  Çözüm Gezgini'nde sağ **CodeDefects** ve ardından **özellikleri**.  
  
2.  Genişletin **yapılandırma özellikleri** ve ardından **genel**.  
  
3.  İçinde **genel** listesinde, metin sütunu yanındaki seçin **hedef uzantısı**, Anahtar'a tıklayın ve **.lib**.  
  
4.  İçinde **Proje Varsayılanları**, sütun tıklayın **yapılandırma türü**ve ardından **statik kitaplık (.lib)**.  
  
### <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>Üst bilgi ve kaynak dosya CodeDefects projeye ekleyin.  
  
1.  Çözüm Gezgini'nde **CodeDefects**, sağ **üst bilgi dosyaları**, tıklayın **Ekle**ve ardından **yeni öğe**.  
  
2.  İçinde **Yeni Öğe Ekle** iletişim kutusu, tıklayın **kod**ve ardından **üst bilgi dosyası (.h)**.  
  
3.  İçinde **adı** kutusuna **Bug.cpp** ve ardından **Ekle**.  
  
4.  Aşağıdaki kodu kopyalayın ve yapıştırın **Bug.cpp** dosyası [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Düzenleyici.  
  
    ```  
    #include <windows.h>  
  
    //    
    //These 3 functions are consumed by the sample  
    //  but are not defined. This project cannot be linked!  
    //  
  
    bool CheckDomain( LPCSTR );  
    HRESULT ReadUserAccount();  
  
    //  
    //These constants define the common sizes of the   
    //  user account information throughout the program  
    //  
  
    const int USER_ACCOUNT_LEN = 256;  
    const int ACCOUNT_DOMAIN_LEN = 128;  
    ```  
  
5.  Çözüm Gezgini'nde sağ **kaynak dosyaları**, işaret **yeni**ve ardından **yeni öğe**.  
  
6.  İçinde **Yeni Öğe Ekle** iletişim kutusu, tıklayın **C++ dosyası (.cpp)**  
  
7.  İçinde **adı** kutusuna **Bug.cpp** ve ardından **Ekle**.  
  
8.  Aşağıdaki kodu kopyalayın ve Bug.h dosyasında yapıştırın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Düzenleyici.  
  
    ```  
    #include <stdlib.h>  
    #include "Bug.h"  
  
    // the user account   
    TCHAR g_userAccount[USER_ACCOUNT_LEN] = "";  
    int len = 0;  
  
    bool ProcessDomain()  
    {  
        TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];  
        // ReadUserAccount gets a 'domain\user' input from   
        //the user into the global 'g_userAccount'  
        if (ReadUserAccount() )  
        {  
  
            // Copies part of the string prior to the '\'   
            // character onto the 'domain' buffer  
            for( len = 0 ; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != '\0') ; len++  )  
            {  
                if ( g_userAccount[len] == '\\' )   
                {  
                    // Stops copying on the domain and user separator ('\')   
                    break;  
                }  
                domain[len] = g_userAccount[len];          
            }  
            if((len= ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
            {  
                // '\' was not found. Invalid domain\user string.  
                delete [] domain;  
                return false;  
            }  
            else  
            {  
                domain[len]='\0';  
            }  
            // Process domain string  
            bool result = CheckDomain( domain );  
  
            delete[] domain;  
            return result;  
        }  
        return false;  
    }  
  
    int path_dependent(int n)  
    {  
        int i;  
        int j;  
        if (n == 0)  
            i = 1;  
        else  
            j = 1;  
        return i+j;   
    }  
    ```  
  
9. Tıklayın **dosya** menüsüne ve ardından **Tümünü Kaydet**.  
  
### <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Ek açıklamalar projeye ekleyin ve statik bir kitaplık olarak yapılandırma  
  
1.  Çözüm Gezgini'nde tıklayın **CppDemo**, işaret **Ekle**ve ardından **yeni proje**.  
  
2.  İçinde **Yeni Proje Ekle** iletişim kutusunda, Visual C++'ı genişletin, **genel**ve ardından **boş proje**.  
  
3.  İçinde **adı** metin kutusunda, **ek açıklamaları**ve ardından **Ekle**.  
  
4.  Çözüm Gezgini'nde sağ **ek açıklamaları** ve ardından **özellikleri**.  
  
5.  Genişletin **yapılandırma özellikleri** ve ardından **genel**.  
  
6.  İçinde **genel** listesinde, metin sütunu yanındaki seçin **hedef uzantısı**, Anahtar'a tıklayın ve **.lib**.  
  
7.  İçinde **Proje Varsayılanları**, sütun tıklayın **yapılandırma türü**ve ardından **statik kitaplık (.lib)**.  
  
### <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Kaynak dosya ve üstbilgi dosyası ek açıklamaları projeye ekleyin.  
  
1.  Çözüm Gezgini'nde **ek açıklamaları**, sağ **üst bilgi dosyaları**, tıklayın **Ekle**ve ardından **yeni öğe**.  
  
2.  İçinde **Yeni Öğe Ekle** iletişim kutusu, tıklayın **üst bilgi dosyası (.h)**.  
  
3.  İçinde **adı** kutusuna **annotations.h** ve ardından **Ekle**.  
  
4.  Aşağıdaki kodu kopyalayın ve yapıştırın **annotations.h** dosyası [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Düzenleyici.  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
  
    struct LinkedList  
    {  
        struct LinkedList* next;  
        int data;  
    };  
  
    typedef struct LinkedList LinkedList;  
  
    [returnvalue:SA_Post( Null=SA_Maybe )] LinkedList* AllocateNode();  
  
    ```  
  
5.  Çözüm Gezgini'nde sağ **kaynak dosyaları**, işaret **yeni**ve ardından **yeni öğe**.  
  
6.  İçinde **Yeni Öğe Ekle** iletişim kutusu, tıklayın **kod** ve ardından **C++ dosyası (.cpp)**  
  
7.  İçinde **adı** kutusuna **annotations.cpp** ve ardından **Ekle**.  
  
8.  Aşağıdaki kodu kopyalayın ve yapıştırın **annotations.cpp** dosyası [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Düzenleyici.  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
    #include <windows.h>  
    #include <stdlib.h>    
    #include "annotations.h"  
  
    LinkedList* AddTail( LinkedList *node, int value )  
    {  
        LinkedList *newNode = NULL;   
  
        // finds the last node  
        while ( node->next != NULL )   
        {  
            node = node->next;  
        }  
  
        // appends the new node  
        newNode = AllocateNode();   
        newNode->data = value;  
        newNode->next = 0;  
        node->next = newNode;  
  
        return newNode;  
    }  
  
    ```  
  
9. Tıklayın **dosya** menüsüne ve ardından **Tümünü Kaydet**.



