---
title: 基本和摘要式身份验证
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- authentication [.NET Framework], classes
- Basic authentication
- authentication [.NET Framework], basic
- client authentication, basic
- user authentication, basic
- authentication [.NET Framework], digest
- receiving data, authentication
- client authentication, digest
- Internet, authentication
- digest authentication
- sending data, authentication
- network resources, authentication
- user authentication, digest
ms.assetid: 8cce2742-8d52-4643-9dd2-64ddf38aa878
ms.openlocfilehash: 9a1ad701e1e8f4ee9966ebd56922c29e2bae7a03
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048905"
---
# <a name="basic-and-digest-authentication"></a>基本和摘要式身份验证
基本身份验证和摘要式身份验证的 <xref:System.Net> 实现符合 RFC2617 – HTTP 身份验证：基本身份验证和摘要式身份验证（可从[万维网联合会](https://www.w3.org) 网站找到）。  
  
 若要使用基本身份验证和摘要式身份验证，应用程序必须在 <xref:System.Net.WebRequest> 对象的 <xref:System.Net.WebRequest.Credentials%2A> 属性中提供用户名和密码，该对象用于从 Internet 中请求数据，如下例所示。  
  
```vb  
Dim MyURI As String = "http://www.contoso.com/"  
Dim WReq As WebRequest = WebRequest.Create(MyURI)  
WReq.Credentials = New NetworkCredential(UserName, SecurelyStoredPassword)  
```  
  
```csharp  
String MyURI = "http://www.contoso.com/";  
WebRequest WReq = WebRequest.Create(MyURI);  
WReq.Credentials = new NetworkCredential(UserName, SecurelyStoredPassword);  
```  
  
> [!CAUTION]
> 使用基本和摘要式身份验证发送的数据不会加密，因此攻击者会看到数据。 此外，基本身份验证凭据（用户名和密码）是以明文形式发送的，会被截取。  
  
## <a name="see-also"></a>另请参阅

- [NTLM 和 Kerberos 身份验证](ntlm-and-kerberos-authentication.md)
- [Internet 身份验证](internet-authentication.md)
