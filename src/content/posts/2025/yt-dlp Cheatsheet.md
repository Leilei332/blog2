---
title: yt-dlp Cheatsheet
published: 2024-02-13
updated: 2025-05-30
tags: 
- 工具
abbrlink: yt-dlp-cheatsheet
---


> 由于yt-dlp的许多功能依赖ffmpeg，建议安装ffmpeg。

# 下载B站视频与弹幕
`yt-dlp`支持下载弹幕但是不会默认下载。

<!-- TEASER_END -->

```bash
yt-dlp $url --sub-lang danmuku --embed-metadata
```

如果要加章节可以加上`--embed-chapters`，如果要下载分P视频用`-I`选项。

```bash
function downloadBilibili() {
	yt-dlp $1 --sub-lang danmuku --embed-metadata
}
```

Powershell版：

```powershell
function Download-Bilibili($url) {
    yt-dlp $url --sub-lang danmuku --embed-metadata
}
```

# 下载网易云音乐（包括歌词与元数据）
这个方面`yt-dlp`做得比洛雪音乐更好，不但支持加入元数据，还支持在元数据增加专辑发行年份信息。

```bash
yt-dlp $url --sub-lang lyrics --write-subs --embed-thumbnail --embed-metadata -o "%(title)s - %(creator)s.%(ext)s"
```

其中`--sub-lang lyrics --write-subs`用来下载歌词，如果原音乐无歌词可以去掉。歌词有三种类型，将上面的`lyrics`替换即可：

* `lyrics` 原歌词
* `lyrics_translated` 翻译后的歌词
* `lyrics_merged` 原歌词与翻译

另外，`yt-dlp`默认给音乐里的元数据不包含轨道编号，但这很好解决，只要对于音乐专辑的链接（或网易云电台）用下面的命令下载就能按顺序编号：

```bash
yt-dlp $url --parse-metadata "playlist_index:%(track_number)s" --add-metadata --embed-metadata --embed-thumbnail -o "%(title)s - %(creator)s.%(ext)s"
```

```bash
function downloadNetease() {
	yt-dlp $1 --sub-lang lyrics --write-subs --embed-thumbnail --embed-metadata -o "%(title)s - %(creator)s.%(ext)s"
}
```

Powershell版：

```powershell
function Download-Netease {
    param (
	[string] $url,
	[switch] $lyrics
    )
    if ($lyrics) {
	yt-dlp $url --sub-lang lyrics --write-subs --embed-thumbnail --embed-metadata -o "%(title)s - %(creator)s.%(ext)s"
    } else {
	yt-dlp $url --embed-thumbnail --embed-metadata -o "%(title)s - %(creator)s.%(ext)s"
    }
}
```
