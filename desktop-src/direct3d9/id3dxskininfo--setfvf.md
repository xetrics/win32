﻿---
Description: 'Sets the flexible vertex format (FVF) type.'
ms.assetid: 'e581dcd4-7e17-4c36-aac9-c2942924cf51'
title: 'ID3DXSkinInfo::SetFVF method'
---

# ID3DXSkinInfo::SetFVF method

Sets the flexible vertex format (FVF) type.

## Syntax


```C++
HRESULT SetFVF(
  [in] DWORD FVF
);
```



## Parameters

<dl> <dt>

*FVF* \[in\]
</dt> <dd>

Type: **[**DWORD**](winprog.windows_data_types)**

Flexible vertex format. See [D3DFVF](d3dfvf.md).

</dd> </dl>

## Return value

Type: **[**HRESULT**](455d07e9-52c3-4efb-a9dc-2955cbfd38cc)**

If the method succeeds, the return value is D3D\_OK. If the method fails, the return value can be D3DERR\_INVALIDCALL.

## Requirements



|                    |                                                                                        |
|--------------------|----------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>D3DX9Mesh.h</dt> </dl> |
| Library<br/> | <dl> <dt>D3dx9.lib</dt> </dl>   |



## See also

<dl> <dt>

[ID3DXSkinInfo](id3dxskininfo.md)
</dt> </dl>

 

 



