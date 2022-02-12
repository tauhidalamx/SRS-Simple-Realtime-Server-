# SRS(Simple Realtime Server)

![](http://ossrs.net/gif/v1/sls.gif?site=github.com&path=/srs/develop)
[![](https://github.com/ossrs/srs/actions/workflows/codeql-analysis.yml/badge.svg?branch=develop)](https://github.com/ossrs/srs/actions?query=workflow%3ACodeQL+branch%3Adevelop)
[![](https://github.com/ossrs/srs/actions/workflows/release.yml/badge.svg)](https://github.com/ossrs/srs/actions/workflows/release.yml?query=workflow%3ARelease)
[![](https://github.com/ossrs/srs/actions/workflows/test.yml/badge.svg?branch=develop)](https://github.com/ossrs/srs/actions?query=workflow%3ATest+branch%3Adevelop)
[![](https://codecov.io/gh/ossrs/srs/branch/develop/graph/badge.svg)](https://codecov.io/gh/ossrs/srs/branch/develop)


[![SRS Overview](https://ossrs.net/wiki/images/SRS-Overview-4.0.png)](https://ossrs.net/wiki/images/SRS-Overview-4.0.png)
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

