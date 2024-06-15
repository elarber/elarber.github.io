---
title: axios 封装下载功能

index_img: 
lazyload: true
categories:
- 前端插件使用
tags:
- axios
- 文件下载



---










# 封装
```javascript
import axios from 'axios'
import { Message } from 'element-ui';


export default {
  excel(params) {
  const downLoading = ELEMENT.Loading.service({
    lock: true,
     text: "正在获取...",
     spinner: "el-icon-loading",
     background: "rgba(0, 0, 0, 0.7)",
   });
    axios({
      url: '/model/exportAllTable/exportTableMsg2',
      method: 'post',
      responseType: 'blob',
      url: process.env.BASE_URL,
      data: {
        key: "8e15edc35cb68460d4jn08b849okn791",
        tokens: window.name,
        ...params
      }
    }).then(res => {
      console.log(res);
      if (res.status === 200) {
        const blob = new Blob([res.data], { type: "application/vnd.ms-excel" }); // excel文件
        var link = document.createElement("a"); // 创建下载的实体标签
        link.href = URL.createObjectURL(blob); // 创建下载的链接
        link.download = params.fileName +"【用能医生】.xls"; // 下载的文件名
        link.click(); // 执行下载
        URL.revokeObjectURL(link.href); // 下载完成释放掉blob对象
        Message.success("下载成功")
      } else {
        Message.error("下载失败")
      }
    }).finally(() => {
      downLoading.close();
    });
  }
}
```


# blob的type值：
|      文件后缀        |    文件               |         type值                                     |
| ---------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| aac        | AAC audio                                                    | audio/aac                                                    |
| .abw       | [AbiWord](https://en.wikipedia.org/wiki/AbiWord) document    | application/x-abiword                                        |
| .arc       | Archive document (multiple files embedded)                   | application/x-freearc                                        |
| .avi       | AVI: Audio Video Interleave                                  | video/x-msvideo                                              |
| .azw       | Amazon Kindle eBook format                                   | application/vnd.amazon.ebook                                 |
| .bin       | Any kind of binary data                                      | application/octet-stream                                     |
| .bmp       | Windows OS/2 Bitmap Graphics                                 | image/bmp                                                    |
| .bz        | BZip archive                                                 | application/x-bzip                                           |
| .bz2       | BZip2 archive                                                | application/x-bzip2                                          |
| .csh       | C-Shell script                                               | application/x-csh                                            |
| .css       | Cascading Style Sheets (CSS)                                 | text/css                                                     |
| .csv       | Comma-separated values (CSV)                                 | text/csv                                                     |
| .doc       | Microsoft Word                                               | application/msword                                           |
| .docx      | Microsoft Word (OpenXML)                                     | application/vnd.openxmlformats-officedocument.wordprocessingml.document |
| .eot       | MS Embedded OpenType fonts                                   | application/vnd.ms-fontobject                                |
| .epub      | Electronic publication (EPUB)                                | application/epub+zip                                         |
| .gif       | Graphics Interchange Format (GIF)                            | image/gif                                                    |
| .htm .html | HyperText Markup Language (HTML)                             | text/html                                                    |
|            |                                                              |                                                              |
|            |                                                              |                                                              |
| .jar       | Java Archive (JAR)                                           | application/java-archive                                     |
| .jpeg .jpg | JPEG images                                                  | image/jpeg                                                   |
| .js        | JavaScript                                                   | text/javascript                                              |
| .json      | JSON format                                                  | application/json                                             |
| .jsonld    | JSON-LD format                                               | application/ld+json                                          |
| .mid .midi | Musical Instrument Digital Interface (MIDI)                  | audio/midi audio/x-midi                                      |
| .mjs       | JavaScript module                                            | text/javascript                                              |
| .mp3       | MP3 audio                                                    | audio/mpeg                                                   |
| .mpeg      | MPEG Video                                                   | video/mpeg                                                   |
| .mpkg      | Apple Installer Package                                      | application/vnd.apple.installer+xml                          |
| .odp       | OpenDocument presentation document                           | application/vnd.oasis.opendocument.presentation              |
| .ods       | OpenDocument spreadsheet document                            | application/vnd.oasis.opendocument.spreadsheet               |
| .odt       | OpenDocument text document                                   | application/vnd.oasis.opendocument.text                      |
| .oga       | OGG audio                                                    | audio/ogg                                                    |
| .ogv       | OGG video                                                    | video/ogg                                                    |
| .ogx       | OGG                                                          | application/ogg                                              |
| .otf       | OpenType font                                                | font/otf                                                     |
| .png       | Portable Network Graphics                                    | image/png                                                    |
| .pdf       | Adobe [Portable Document Format](https://acrobat.adobe.com/us/en/why-adobe/about-adobe-pdf.html) (PDF) | application/pdf                                              |
| .ppt       | Microsoft PowerPoint                                         | application/vnd.ms-powerpoint                                |
| .pptx      | Microsoft PowerPoint (OpenXML)                               | application/vnd.openxmlformats-officedocument.presentationml.presentation |
| .rar       | RAR archive                                                  | application/x-rar-compressed                                 |
| .rtf       | Rich Text Format (RTF)                                       | application/rtf                                              |
| .sh        | Bourne shell script                                          | application/x-sh                                             |
| .svg       | Scalable Vector Graphics (SVG)                               | image/svg+xml                                                |
| .swf       | [Small web format](https://en.wikipedia.org/wiki/SWF) (SWF) or Adobe Flash document | application/x-shockwave-flash                                |
| .tar       | Tape Archive (TAR)                                           | application/x-tar                                            |
| .tif .tiff | Tagged Image File Format (TIFF)                              | image/tiff                                                   |
| .ttf       | TrueType Font                                                | font/ttf                                                     |
| .txt       | Text, (generally ASCII or ISO 8859-*n*)                      | text/plain                                                   |
| .vsd       | Microsoft Visio                                              | application/vnd.visio                                        |
| .wav       | Waveform Audio Format                                        | audio/wav                                                    |
| .weba      | WEBM audio                                                   | audio/webm                                                   |
| .webm      | WEBM video                                                   | video/webm                                                   |
| .webp      | WEBP image                                                   | image/webp                                                   |
| .woff      | Web Open Font Format (WOFF)                                  | font/woff                                                    |
| .woff2     | Web Open Font Format (WOFF)                                  | font/woff2                                                   |
| .xhtml     | XHTML                                                        | application/xhtml+xml                                        |
| .xls       | Microsoft Excel                                              | application/vnd.ms-excel                                     |
| .xlsx      | Microsoft Excel (OpenXML)                                    | application/vnd.openxmlformats-officedocument.spreadsheetml.sheet |
| .xml       | XML                                                          | application/xml 代码对普通用户来说不可读 ([RFC 3023](https://tools.ietf.org/html/rfc3023#section-3), section 3) text/xml 代码对普通用户来说可读 ([RFC 3023](https://tools.ietf.org/html/rfc3023#section-3), section 3) |
| .xul       | XUL                                                          | application/vnd.mozilla.xul+xml                              |
| .zip       | ZIP archive                                                  | application/zip                                              |
| .3gp       | [3GPP](https://en.wikipedia.org/wiki/3GP_and_3G2) audio/video container | video/3gpp audio/3gpp（若不含视频）                          |
| .3g2       | [3GPP2](https://en.wikipedia.org/wiki/3GP_and_3G2) audio/video container | video/3gpp2 audio/3gpp2（若不含视频）                        |
| .7z        | [7-zip](https://en.wikipedia.org/wiki/7-Zip) archive         | application/x-7z-compressed                                  |



