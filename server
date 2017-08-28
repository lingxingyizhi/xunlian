# _*_ coding: utf-8 _*_
import socket,threading,time
def tcplink(sock,addr):
	print('接收到新的连接，源：%s:%s...'%addr)
	sock.send(b'huanying')
	while True:
		data=sock.recv(1024)
		time.sleep(1)
		if not data or data.decode('utf-8')=='exit':
			break
		sock.send (('hello,%s!'%data.decode('utf-8')).encode('utf-8'))
	sock.close()
	print('从%s:%s来的连接中断'%addr)
#引入socket函数
s=socket.socket(socket.AF_INET,socket.SOCK_STREAM)
#创建一个基于IPv4和TCP协议的socket
s.bind(('127.0.0.1',9999))
#绑定监听的地址和端口
s.listen(5)
print('等一会......客户端正在接入')
#开始监听端口9999
while True:
    #接受一个新连接
	sock,addr=s.accept()
	#创建新线程来处理TCP连接
	t=threading.Thread(target=tcplink,args=(sock,addr))
	t.start()
