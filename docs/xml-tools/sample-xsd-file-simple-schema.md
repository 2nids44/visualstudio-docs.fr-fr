---
title: "Exemple de fichier XSD&#160;: sch&#233;ma simple | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f7e1dde1-b4f6-4371-add4-935b68ec77d7
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# Exemple de fichier XSD&#160;: sch&#233;ma simple
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le fichier XSD suivant est utilisé dans différents exemples de la documentation du Concepteur de schémas XSD.Ce fichier est un schéma de bon de commande simple.  
  
```xml  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
           xmlns:tns="http://tempuri.org/PurchaseOrderSchema.xsd"   
           targetNamespace="http://tempuri.org/PurchaseOrderSchema.xsd"   
           elementFormDefault="qualified">  
 <xsd:element name="PurchaseOrder" type="tns:PurchaseOrderType"/>  
 <xsd:complexType name="PurchaseOrderType">  
  <xsd:sequence>  
   <xsd:element name="ShipTo" type="tns:USAddress" maxOccurs="2"/>  
   <xsd:element name="BillTo" type="tns:USAddress"/>  
  </xsd:sequence>  
  <xsd:attribute name="OrderDate" type="xsd:date"/>  
 </xsd:complexType>  
  
 <xsd:complexType name="USAddress">  
  <xsd:sequence>  
   <xsd:element name="name"   type="xsd:string"/>  
   <xsd:element name="street" type="xsd:string"/>  
   <xsd:element name="city"   type="xsd:string"/>  
   <xsd:element name="state"  type="xsd:string"/>  
   <xsd:element name="zip"    type="xsd:integer"/>  
  </xsd:sequence>  
  <xsd:attribute name="country" type="xsd:NMTOKEN" fixed="US"/>  
 </xsd:complexType>  
</xsd:schema>  
```