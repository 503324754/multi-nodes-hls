该版本为HLS共享cdn版本，主要实现流程
1.程序启动后,player-controller.js 先从cdn源请求ts数据
2.在收到视频元数据metadataloaded后，调用node-query.js查询获取共享cdn节点
3.PlayerController.requestPiece()请求ts时按节点优先级顺序请求，请求后该节点优先级-1
4.最多同时保持三节点请求.
5.发生超时或网络异常，删除节点.
6.PlayerController.getPayloadByFragSN()顺序获取下载的ts流，进行转码封装.
