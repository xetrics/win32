---
title: DnsName
description: Contains the full DNS label associated with the resource.
audience: developer
author: REDMOND\\markl
manager: REDMOND\\markl
ms.assetid: '1E105AA9-846D-48AD-B7DA-C30FCA4738C2'
ms.prod: 'windows-server-dev'
ms.technology: 'failover-clustering'
ms.tgt_platform: multiple
keywords: ["DnsName Failover Cluster , for virtual machine replication brokers", "DnsName Failover Cluster"]
topic_type:
- apiref
api_name:
- DnsName
api_type:
- NA
---

# DnsName

Contains the full [*DNS*](d-gly.md#-wolf-domain-name-system-gly) label associated with the resource. The following table summarizes the attributes of the **DnsName** property.



| Attribute | Value                                                            |
|-----------|------------------------------------------------------------------|
| Data type | Null-terminated Unicode string                                   |
| Access    | [Read/write](read-write-properties.md)                          |
| Status    | Required                                                         |
| Structure | [**CLUSPROP\_SZ**](clusprop-sz.md)                              |
| Maximum   | None (but see [Maximum Property Size](maximum-string-size.md).) |
| Default   | **NULL**                                                         |



�

## Remarks

The [**CLUSPROP\_SZ\_DECLARE**](clusprop-sz-declare.md) macro creates a [**CLUSPROP\_SZ**](clusprop-sz.md) structure with an array of the correct size.

## Examples

The property value portion of a [property list](property-lists.md) entry for **DnsName** can be set with the following example code.


```C++
WCHAR szDnsNameData[]  = L"myDNS";
CLUSPROP_SZ_DECLARE(     DnsNameValue, sizeof( szDnsNameData ) / sizeof( WCHAR ) );

DnsNameValue.Syntax.dw = CLUSPROP_SYNTAX_LIST_VALUE_SZ;
DnsNameValue.cbLength  = sizeof( szDnsNameData );
StringCbCopy(            DnsNameValue.sz, 
                         DnsNameValue.cbLength, 
                         szDnsNameData );
```



## Requirements



|                                     |                                |
|-------------------------------------|--------------------------------|
| Minimum supported client<br/> | None supported<br/>      |
| Minimum supported server<br/> | Windows Server�2012<br/> |



## See also

<dl> <dt>

[Virtual Machine Replication Broker Private Properties](virtual-machine-replication-broker-private-properties.md)
</dt> <dt>

[**CLUSPROP\_SZ**](clusprop-sz.md)
</dt> <dt>

[**CLUSPROP\_SZ\_DECLARE**](clusprop-sz-declare.md)
</dt> </dl>

�

�




