# 306san/rpi-ruby
This PC and Raspberry Pi can work ruby images.
But Docker for Linux can't work it.

これはPCとRaspberry　Piの両方で動くコンテナです。  
今のところ、Docker for Mac Raspberry Pi上のDockerでの動作確認をしています。  
しかしLinux上のDockerでは動かないことを確認済みです。  
PRお待ちしています

## Version
- Baseimage: resin/rpi-raspbian
- reference image: docker_official/ruby
  - under [Apache 2.0 license](https://github.com/docker-library/repo-info/blob/master/LICENSE).
- Ruby
  - 2.4.1