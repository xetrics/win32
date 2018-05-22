﻿---
Description: 'Constants used by D3DPRESENT\_PARAMETERS.'
ms.assetid: '1294171e-b3f6-4264-8411-b69427cefe7b'
title: D3DPRESENTFLAG
---

# D3DPRESENTFLAG

Constants used by [**D3DPRESENT\_PARAMETERS**](d3dpresent-parameters.md).



<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td>#define</td>
<td>Value</td>
<td>Description</td>
</tr>
<tr class="even">
<td>D3DPRESENTFLAG_DEVICECLIP</td>
<td>0x00000004</td>
<td>Clip a windowed [<strong>Present</strong>](idirect3ddevice9--present.md) blit into the window client area, within the monitor screen area of the video adapter that created the Direct3D device. D3DPRESENTFLAG_DEVICECLIP is not valid with D3DSWAPEFFECT_FLIPEX.</td>
</tr>
<tr class="odd">
<td>D3DPRESENTFLAG_DISCARD_DEPTHSTENCIL</td>
<td>0x00000002</td>
<td>Set this flag when the device or swap chain is created to enable z-buffer discarding. If this flag is set, the contents of the depth stencil buffer will be invalid after calling either [<strong>Present</strong>](idirect3ddevice9--present.md), or [<strong>SetDepthStencilSurface</strong>](idirect3ddevice9--setdepthstencilsurface.md) with a different depth surface. Discarding z-buffer data can increase performance and is driver dependent. The debug runtime will enforce discarding by clearing the z-buffer to some constant value after calling either [<strong>Present</strong>](idirect3ddevice9--present.md), or [<strong>SetDepthStencilSurface</strong>](idirect3ddevice9--setdepthstencilsurface.md) with a different depth surface.<br/> Discarding z-buffer data is illegal for all lockable formats, D3DFMT_D16_LOCKABLE and D3DFMT_D32F_LOCKABLE. Any use of [<strong>CreateDevice</strong>](idirect3d9--createdevice.md) specifying a lockable format and z-buffer discarding will fail. For more information about formats, see [D3DFORMAT](d3dformat.md).<br/></td>
</tr>
<tr class="even">
<td>D3DPRESENTFLAG_LOCKABLE_BACKBUFFER</td>
<td>0x00000001</td>
<td>Set this flag if the application requires the ability to lock the back buffer directly. Note that back buffers are not lockable unless the application specifies D3DPRESENTFLAG_LOCKABLE_BACKBUFFER when calling [<strong>CreateDevice</strong>](idirect3d9--createdevice.md) or [<strong>Reset</strong>](idirect3ddevice9--reset.md). Lockable back buffers incur a performance cost on some graphics hardware configurations. Performing a lock operation (or using [<strong>UpdateSurface</strong>](idirect3ddevice9--updatesurface.md) to write) on the lockable back buffer decreases performance on many cards. In this case, consider using textured triangles to move data to the back buffer.<br/> 
<table>
<tbody>
<tr class="odd">
<td>Differences between Direct3D 9 and Direct3D 9Ex:<br/> In Direct3D9Ex this flag cannot be set if the D3DSWAPEFFECT is D3DSWAPEFFECT_FLIPEX, since the flip model enables the Desktop Window Manager to access an application's back buffer. A cross-process shared-surface should not be locked.<br/></td>
</tr>
</tbody>
</table>

<p> </p></td>
</tr>
<tr class="odd">
<td>D3DPRESENTFLAG_NOAUTOROTATE</td>
<td>0x00000020</td>
<td>Rotated monitors are handled automatically with a rotating copy during presentation, which is not very efficient. This flag means the application will perform it's own display rotation. 
<table>
<tbody>
<tr class="odd">
<td>Differences between Direct3D 9 and Direct3D 9Ex:<br/> This flag is available in Direct3D 9Ex only.<br/></td>
</tr>
</tbody>
</table>

<p> </p>
<p>Applications can achieve their own rotation possibly by using a rotated view matrix. The methods [<strong>GetDisplayModeEx</strong>](idirect3dswapchain9-getdisplaymodeex.md) and [<strong>GetAdapterDisplayModeEx</strong>](idirect3d9ex-getadapterdisplaymodeex.md) should be used to to find the current rotation setting. The backbuffer Width and Height parameters in [<strong>CreateDeviceEx</strong>](idirect3d9ex-createdeviceex.md) and [<strong>ResetEx</strong>](idirect3ddevice9ex-resetex.md) must be use landscape orientation, while the fullscreen display mode structure should be the same as what is returned from [<strong>EnumAdapterModesEx</strong>](idirect3d9ex-enumadaptermodesex.md) (i.e. Width and Height are swapped when rotated 90 and 270 degrees).</p>
<p>When using Lock on rotated render targets, upper-left corner assumptions no longer hold true, the render target SURFACE_DESC will remain landscape (as implied by the creation parameters), and GDI window, mouse coordinates, and such need to be properly translated when used with the Direct3D render target and scene.</p></td>
</tr>
<tr class="even">
<td>D3DPRESENTFLAG_UNPRUNEDMODE</td>
<td>0x00000040</td>
<td>Use this flag to specify any RAW display mode enumerated by the display adapter even though Direct3D may have indicated the mode is invalid. The application should implement this in a robust manner in case the desired mode really is invalid. 
<table>
<tbody>
<tr class="odd">
<td>Differences between Direct3D 9 and Direct3D 9Ex:<br/> This flag is available in Direct3D 9Ex only.<br/></td>
</tr>
</tbody>
</table>

<p> </p></td>
</tr>
<tr class="odd">
<td>D3DPRESENTFLAG_VIDEO</td>
<td>0x00000010</td>
<td>This is a hint to the driver that the back buffers will contain video data.</td>
</tr>
<tr class="even">
<td>D3DPRESENTFLAG_OVERLAY_LIMITEDRGB</td>
<td>0x00000080</td>
<td>Specifies whether the overlay is full range RGB or limited range RGB. Setting this flag indicates limited range RGB. In limited range RGB, the RGB range is compressed such that 16:16:16 is black and 235:235:235 is white.
<table>
<tbody>
<tr class="odd">
<td>Differences between Direct3D 9 and Direct3D 9Ex:<br/> This flag is available in Direct3D 9Ex only.<br/></td>
</tr>
</tbody>
</table>

<p> </p></td>
</tr>
<tr class="odd">
<td>D3DPRESENTFLAG_OVERLAY_YCbCr_BT709</td>
<td>0x00000100</td>
<td>Specifies whether the overlay is BT.601 or BT.709. Setting this flag indicates BT.709, for high-definition TV (HDTV).
<table>
<tbody>
<tr class="odd">
<td>Differences between Direct3D 9 and Direct3D 9Ex:<br/> This flag is available in Direct3D 9Ex only.<br/></td>
</tr>
</tbody>
</table>

<p> </p></td>
</tr>
<tr class="even">
<td>D3DPRESENTFLAG_OVERLAY_YCbCr_xvYCC</td>
<td>0x00000200</td>
<td>Specifies whether the overlay is conventional YCbCr or extended YCbCr (xvYCC). Setting this flag indicates extended YCbCr (xvYCC).
<table>
<tbody>
<tr class="odd">
<td>Differences between Direct3D 9 and Direct3D 9Ex:<br/> This flag is available in Direct3D 9Ex only.<br/></td>
</tr>
</tbody>
</table>

<p> </p></td>
</tr>
<tr class="odd">
<td>D3DPRESENTFLAG_RESTRICTED_CONTENT</td>
<td>0x00000400</td>
<td>Setting this flag indicates that the swapchain contains protected content and automatically causes the runtime to restrict access to the swapchain so that only the Desktop Windows Manager (DWM) can use the swapchain.
<table>
<tbody>
<tr class="odd">
<td>Differences between Direct3D 9 and Direct3D 9Ex:<br/> This flag is available in Direct3D 9Ex only.<br/></td>
</tr>
</tbody>
</table>

<p> </p></td>
</tr>
<tr class="even">
<td>D3DPRESENTFLAG_RESTRICT_SHARED_RESOURCE_DRIVER</td>
<td>0x00000800</td>
<td>Setting this flag indicates that the driver should restrict access to any shared resources that are created for DWM interaction. The caller must create an authenticated channel with the driver. The driver should then allow access to processes that attempt to open those shared resources.
<table>
<tbody>
<tr class="odd">
<td>Differences between Direct3D 9 and Direct3D 9Ex:<br/> This flag is available in Direct3D 9Ex only.<br/></td>
</tr>
</tbody>
</table>

<p> </p></td>
</tr>
</tbody>
</table>



 

These constants are used by [**D3DPRESENT\_PARAMETERS**](d3dpresent-parameters.md).

## Constant Information



|                          |             |
|--------------------------|-------------|
| Header                   | d3d9types.h |
| Minimum operating system | Windows 98  |



 

## Related topics

<dl> <dt>

[Direct3D Constants](dx9-graphics-reference-d3d-constants.md)
</dt> </dl>

 

 



