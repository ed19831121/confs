ServerRoot：					# "服务器的基础目录，注意，此指令中的路径最后不要加 / "
	conf/
	logs/
Listen [IP-address:]portnumber [protocol]：	# 指定服务器监听的IP和端口。默认情况下Apache会在所有IP地址上监听。
						# Listen是Apache2.0以后版本必须设置的指令，如果在配置文件中找不到这个指令，服务器将无法启动。
LoadModule module filename
User
Group
ServerName [scheme://]fully-qualified-domain-name[:port]

AllowOverride仅在不包含正则表达式的<Directory>配置段中才是有效的。在<Location>, <DirectoryMatch>, <Files>配置段中都是无效的。
配置段
<Directory>
<Location> 
<DirectoryMatch> 
<Files>
