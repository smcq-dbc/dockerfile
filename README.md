由于平时总需要搭环境，各版本php有些差别，每次用docker拉一个基础镜像都是换源装vim和相关环境，突然发现这不是重复劳动吗，然后想整一个dockerfile，到时候用着也方便，至于网上有现成的为啥还要自己搭，个人习惯吧，记得某次拉了个镜像900M，但自己搭了同样的镜像仅260M，迷惑。
所有dockerfile都在本地测试了下，应该没啥问题，可能有些扩展啥的需要自己额外安装(: