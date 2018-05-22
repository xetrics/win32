---
title: ICM\_DECOMPRESS\_GET\_PALETTE message
description: The ICM\_DECOMPRESS\_GET\_PALETTE message requests that the video decompression driver supply the color table of the output BITMAPINFOHEADER structure. You can send this message explicitly or by using the ICDecompressGetPalette macro.
ms.assetid: 'f9fae9ab-9f69-44b6-bedb-f56f43845229'
keywords: ["ICM_DECOMPRESS_GET_PALETTE message Windows Multimedia"]
topic_type:
- apiref
api_name:
- ICM_DECOMPRESS_GET_PALETTE
api_location:
- Vfw.h
api_type:
- HeaderDef
---

# ICM\_DECOMPRESS\_GET\_PALETTE message

The **ICM\_DECOMPRESS\_GET\_PALETTE** message requests that the video decompression driver supply the color table of the output [**BITMAPINFOHEADER**](https://msdn.microsoft.com/library/windows/desktop/dd183376) structure. You can send this message explicitly or by using the [**ICDecompressGetPalette**](icdecompressgetpalette.md) macro.


```C++
ICM_DECOMPRESS_GET_PALETTE 
wParam = (DWORD_PTR) (LPVOID) lpbiInput; 
lParam = (DWORD_PTR) (LPVOID) lpbiOutput; 
```



## Parameters

<dl> <dt>

<span id="lpbiInput"></span><span id="lpbiinput"></span><span id="LPBIINPUT"></span>*lpbiInput*
</dt> <dd>

Pointer to a [**BITMAPINFOHEADER**](https://msdn.microsoft.com/library/windows/desktop/dd183376) structure containing the input format.

</dd> <dt>

<span id="lpbiOutput"></span><span id="lpbioutput"></span><span id="LPBIOUTPUT"></span>*lpbiOutput*
</dt> <dd>

Pointer to a [**BITMAPINFOHEADER**](https://msdn.microsoft.com/library/windows/desktop/dd183376) structure to contain the color table. The space reserved for the color table is always at least 256 colors. You can specify zero for this parameter to return only the size of the color table.

</dd> </dl>

## Return Value

Returns ICERR\_OK if successful or an error otherwise.

## Remarks

If *lpbiOutput* is nonzero, the driver sets the **biClrUsed** member of [**BITMAPINFOHEADER**](https://msdn.microsoft.com/library/windows/desktop/dd183376) to the number of colors in the color table. The driver fills the **bmiColors** member of [**BITMAPINFO**](https://msdn.microsoft.com/library/windows/desktop/dd183375) with the actual colors.

The driver should support this message only if it uses a palette other than the one specified in the input format.

## Requirements



|                                     |                                                                                  |
|-------------------------------------|----------------------------------------------------------------------------------|
| Minimum supported client<br/> | Windows�2000 Professional \[desktop apps only\]<br/>                       |
| Minimum supported server<br/> | Windows�2000 Server \[desktop apps only\]<br/>                             |
| Header<br/>                   | <dl> <dt>Vfw.h</dt> </dl> |



## See also

<dl> <dt>

[Video Compression Manager](video-compression-manager.md)
</dt> <dt>

[Video Compression Messages](video-compression-messages.md)
</dt> </dl>

�

�




