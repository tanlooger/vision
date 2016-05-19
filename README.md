
sip服务器(resiprocate)：为不同设备建立连接服务，不同的设备一上线，就在这台服务器上进行注册，这样其他终端就可以看到

媒体服务器(pjsip->nath)：只是单纯的做两台设备流媒体数据的转发

1、假设终端A， 终端B

2、A向sipserver发出注册申请，sipserver有一个A的IP和端口号；B向sipserver发出注册申请，sipserver有个B的IP和PORT

3、A向nathserver发出建立连接申请，获取nathserver为其分配的PORT后向sipserver发出INVITE申请，目标是B

4、sipserver收到申请后，通知B，B向nathserver发出申请，获取nathserver为其分配的PORT后向sipserver发出200响应信息

5、nathserver对A和B建立匹配信息，此后A向nathserver发的信息会转发B，反之亦然








string urlDecode(string &SRC) {
	string ret;
	char ch;
	int i, ii;
	for (i = 0; i<SRC.length(); i++) {
		if (int(SRC[i]) == 37) {
			sscanf(SRC.substr(i + 1, 2).c_str(), "%x", &ii);
			ch = static_cast<char>(ii);
			ret += ch;
			i = i + 2;
		}
		else {
			ret += SRC[i];
		}
	}
	return (ret);
}
