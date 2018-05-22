﻿---
Description: 'Specifies the number of streaming endpoints and the number of supported streams for a UVC H.264 encoder.'
ms.assetid: '343EC59E-30E5-4F37-8B05-60EF51717835'
title: 'MF\_MT\_H264\_SIMULCAST\_SUPPORT attribute'
---

# MF\_MT\_H264\_SIMULCAST\_SUPPORT attribute

Specifies the number of streaming endpoints and the number of supported streams for a UVC H.264 encoder.

## Data type

**UINT32**

## Get/set

To get this attribute, call [**IMFAttributes::GetUINT32**](imfattributes-getuint32.md).

To set this attribute, call [**IMFAttributes::SetUINT32**](imfattributes-setuint32.md).

## Applies to

[**IMFMediaType**](imfmediatype.md)

## Remarks

This attribute applies to media types for H.264 streams transmitted over USB. The value corresponds to the **bSimulcastSupport** field in the UVC 1.5 H.264 video format descriptor.

This attribute is also used with [H.264 UVC 1.5 camera encoders](camera-encoder-h264-uvc-1-5.md).

## Requirements



|                                     |                                                                                    |
|-------------------------------------|------------------------------------------------------------------------------------|
| Minimum supported client<br/> | Windows 8 \[desktop apps \| UWP apps\]<br/>                                  |
| Minimum supported server<br/> | Windows Server 2012 \[desktop apps \| UWP apps\]<br/>                        |
| Header<br/>                   | <dl> <dt>Mfapi.h</dt> </dl> |



## See also

<dl> <dt>

[Alphabetical List of Media Foundation Attributes](alphabetical-list-of-media-foundation-attributes.md)
</dt> <dt>

[Media Type Attributes](media-type-attributes.md)
</dt> </dl>

 

 



