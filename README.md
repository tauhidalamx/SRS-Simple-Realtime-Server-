# SRS(Simple Realtime Server)

![](http://ossrs.net/gif/v1/sls.gif?site=github.com&path=/srs/develop)
[![](https://github.com/ossrs/srs/actions/workflows/codeql-analysis.yml/badge.svg?branch=develop)](https://github.com/ossrs/srs/actions?query=workflow%3ACodeQL+branch%3Adevelop)
[![](https://github.com/ossrs/srs/actions/workflows/release.yml/badge.svg)](https://github.com/ossrs/srs/actions/workflows/release.yml?query=workflow%3ARelease)
[![](https://github.com/ossrs/srs/actions/workflows/test.yml/badge.svg?branch=develop)](https://github.com/ossrs/srs/actions?query=workflow%3ATest+branch%3Adevelop)
[![](https://codecov.io/gh/ossrs/srs/branch/develop/graph/badge.svg)](https://codecov.io/gh/ossrs/srs/branch/develop)
[![](https://ossrs.net/wiki/images/wechat-badge4.svg)](../../wikis/Contact#wechat)
[![](https://ossrs.net/wiki/images/srs-faq.svg)](https://github.com/ossrs/srs/issues/2716)
[![](https://ossrs.net/wiki/images/mulan-incubating.svg)](http://mulanos.cn)
[![](https://ossrs.net/wiki/images/srs-alternativeto.svg)](https://alternativeto.net/software/srs/about/)
[![](https://img.shields.io/youtube/channel/views/UCP6ZblCL_fIJoEyUzZxC1ng?style=social)](https://www.youtube.com/channel/UCP6ZblCL_fIJoEyUzZxC1ng)
[![](https://badgen.net/discord/members/yZ4BnPmHAd)](https://discord.gg/yZ4BnPmHAd)
[![](https://opencollective.com/srs-server/tiers/badge.svg)](https://opencollective.com/srs-server/contribute)
[![](https://badgen.net/badge/srs/stackoverflow/orange?icon=terminal)](https://stackoverflow.com/questions/tagged/simple-realtime-server)
[![](https://img.shields.io/docker/pulls/ossrs/srs)](https://hub.docker.com/r/ossrs/srs/tags)


> Note: If image load fail, please see it at [here](https://www.processon.com/view/link/619f29791efad425fd699fd2).

<a name="product"></a>
<a name="usage-docker"></a>
## Usage

Build SRS from source:

```
git clone -b develop https://gitee.com/ossrs/srs.git &&
cd srs/trunk && ./configure && make && ./objs/srs -c conf/srs.conf
```

Open [http://localhost:8080/](http://localhost:8080/) to check it, then publish
by [FFmpeg](https://ffmpeg.org/download.html) or [OBS](https://obsproject.com/download) as:

```bash
ffmpeg -re -i ./doc/source.flv -c copy -f flv -y rtmp://localhost/live/livestream
```

Play the following streams by [players](https://ossrs.net):

* RTMP (by [VLC](https://www.videolan.org/)): rtmp://localhost/live/livestream
* H5(HTTP-FLV): [http://localhost:8080/live/livestream.flv](http://localhost:8080/players/srs_player.html?autostart=true&stream=livestream.flv&port=8080&schema=http)
* H5(HLS): [http://localhost:8080/live/livestream.m3u8](http://localhost:8080/players/srs_player.html?autostart=true&stream=livestream.m3u8&port=8080&schema=http)

Note that if convert RTMP to WebRTC, please use [`rtmp2rtc.conf`](https://github.com/ossrs/srs/issues/2728#issuecomment-964686152):

* H5(WebRTC): [webrtc://localhost/live/livestream](http://localhost:8080/players/rtc_player.html?autostart=true)

> Note: Besides of FFmpeg or OBS, it's also able to [publish by H5](http://localhost:8080/players/rtc_publisher.html?autostart=true) 
> if **WebRTC([CN](https://github.com/ossrs/srs/wiki/v4_CN_WebRTC#rtc-to-rtmp), [EN](https://github.com/ossrs/srs/wiki/v4_EN_WebRTC#rtc-to-rtmp))** is enabled,
> please remember to set the **CANDIDATE([CN](https://github.com/ossrs/srs/wiki/v4_CN_WebRTC#config-candidate) or [EN](https://github.com/ossrs/srs/wiki/v4_EN_WebRTC#config-candidate))** for WebRTC.

> Highly recommend that directly run SRS by
> **docker([CN](https://github.com/ossrs/srs/wiki/v4_CN_Home#docker) / [EN](https://github.com/ossrs/srs/wiki/v4_EN_Home#docker))**,
> **Cloud Virtual Machine([CN](https://github.com/ossrs/srs/wiki/v4_CN_Home#cloud-virtual-machine) / [EN](https://github.com/ossrs/srs/wiki/v4_EN_Home#cloud-virtual-machine))**,
> or **K8s([CN](https://github.com/ossrs/srs/wiki/v4_CN_Home#k8s) / [EN](https://github.com/ossrs/srs/wiki/v4_EN_Home#k8s))**,
> however it's also easy to build SRS from source code, for detail please see
> **Getting Started([CN](https://github.com/ossrs/srs/wiki/v4_CN_Home#getting-started) / [EN](https://github.com/ossrs/srs/wiki/v4_EN_Home#getting-started))**.

> Note: If need HTTPS, by which WebRTC and modern browsers require, please read
> **HTTPS API([CN](https://github.com/ossrs/srs/wiki/v4_CN_HTTPApi#https-api) / [EN](https://github.com/ossrs/srs/wiki/v4_EN_HTTPApi#https-api))**
> and **HTTPS Callback([CN](https://github.com/ossrs/srs/wiki/v4_CN_HTTPCallback#https-callback) / [EN](https://github.com/ossrs/srs/wiki/v4_EN_HTTPCallback#https-callback))**
> and **HTTPS Live Streaming([CN](https://github.com/ossrs/srs/wiki/v4_EN_DeliveryHttpStream#https-flv-live-stream) / [EN](https://github.com/ossrs/srs/wiki/v4_EN_DeliveryHttpStream#https-flv-live-stream))**,
> however HTTPS proxy also works perfect with SRS such as Nginx.

<a name="srs-40-wiki"></a>
<a name="wiki"></a>

