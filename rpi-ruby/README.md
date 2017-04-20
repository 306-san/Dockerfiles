# 306san/rpi-ruby
This PC and Raspberry Pi can work ruby images.  
This image based on arm.  
Before using this image on linux  
install qemu system.
For Ubuntu  
```
sudo apt install qemu-user-static 
```
Thanks  
これはPCとRaspberry Piの両方で動くコンテナです。  
今のところ、Mac or Linux or Raspberry pi2での動作確認をしています。  
Linuxで使う場合はqemu環境が必要になります。  
導入していない場合、Ubuntuは
```
sudo apt install qemu-user-static 
```
で導入できるかと思います。

## Version
- Baseimage: resin/rpi-raspbian
- reference image: docker_official/ruby
  - under [Apache 2.0 license](https://github.com/docker-library/repo-info/blob/master/LICENSE).
- Ruby
  - 2.4.1
